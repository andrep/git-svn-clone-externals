git-svn-clone-externals
=======================

This is a very simple shell script to make git-svn clone your svn:externals
definitions.  Place the script in a directory where you have one or more
svn:externals definitions, run it, and it will:

* git svn clone each external into a .git_externals/ directory.
* symlink the cloned repository in .git_externals/ to the proper directory
  name.
* add the symlink and .git_externals/ to the .git/info/excludes/ file, so that
  you're not pestered about it when performing a git status.

That's pretty much about it.  Low-tech and cheap and cheery, but I couldn't
find anything else like it after extensive Googling, so hopefully some other
people out there with low-tech minds like mine will find this useful.

You could certainly make the script a lot more complex and do things such as
share svn:externals repositories between different git repositories, traverse
through the entire git repository to detect svn:externals definitions instead
of having to place the script in the correct directory, etc... but this works,
it's simple, and it does just the one thing, unlike a lot of other git/svn
integration scripts that I've found.  I absolutely do welcome those features,
but I figured I'd push this out since it works for me and is probably useful
for others.

Enjoy,

- Andre Pang <ozone@algorithm.com.au>


git-svn-check-unpushed and git-svn-externals-check
==================================================

In addition to the git-svn-clone-externals script I created two more
scripts:

* ``git-svn-check-unpushed`` tries to determine whether there are
  commits which are not yet pushed back to the subversion
  repository. Originally I took this idea from Magit (an interface to
  the version control system Git, implemented as an extension to
  Emacs) and implemented it in Python instead of Lisp.

* git-svn-externals-check is a script that displays whether there are
  uncommitted changes or commits that are not pushed to the subversion
  repository yet. Basically it executes ``git status`` and the
  ``git-svn-check-unpushed`` scripts for each directory in the current
  directory.

Feel free to use and improve these scripts.

- Mark van Lent <mark@vlent.nl>
