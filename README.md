# SVNProcedure
Documenting my procedure for bringing an SVN repo into Git/GitHub

I have been moving more and more of my old SVN repositories to Git and GitHub.  Eventually, I'll probably hit every one that's still got any activity.  I make this public in case it's of use to anyone.  Note that my intent here is to get all of my history from the SVN repository, but then to switch completed to a GitHub-hosted Git repository going forward.  The SVN server's version and any old copies of the repository are abandoned.

Some of this is from my own accumulated knowledge of SVN and Git, but I have based some of this on information found at the following:

* https://john.albin.net/git/convert-subversion-to-git
* https://help.github.com/en/articles/adding-a-remote

The SVN repositories are on a server which I accessed through the `svn+ssh` protocol.  Most of them did not have multiple users, so I don't need to worry about the steps that try to map SVN users to Git users.  I also rarely had meaningful branches or tags, so I just import the SVN `trunk` as Git `master`.

I'll use `server.svn` as the hostname and `reponame` as the repository name below.

First step, clone the SVN repository as a Git repository (work in a temporary directory).

`git svn clone svn+ssh://server.svn/svn/reponame/trunk reponame`

Assuming that looks good, create a repository on GitHub.  It will also be called `reponame`.

Back in the clone created above, set its `origin` to the GitHub repository you just created.

`git remote add origin https://github.com/jteresco/reponame.git`

And then push the clone there.

`git push -u origin master`

The repository should now be on GitHub.  Proceed with creating a clone or whatever else.
