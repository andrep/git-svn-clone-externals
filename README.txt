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

NB: This assumes you have passwordless svn.

Enjoy,

- Andre Pang <ozone@algorithm.com.au>


Tools
=====

The git-svn-clone-externals script does a great job of cloning the
svn:externals. However, in day-to-day work I want to check whether I
need to push stuff and update a buch of 'external' repositories in one
go. Therefore I creates some additional scripts.

* ``git-svn-check-unpushed`` tries to determine whether there are
  commits which are not yet pushed back to the subversion
  repository. Originally I took this idea from Magit (an interface to
  the version control system Git, implemented as an extension to
  Emacs) and implemented it in Python instead of Lisp.

  This script can be run in every location of a git repository.

* git-svn-externals-check is a script that displays whether there are
  uncommitted changes or commits that are not pushed to the subversion
  repository yet. Basically it executes ``git status`` and the
  ``git-svn-check-unpushed`` scripts for each directory in the current
  directory.

  This script must be run in the directory where the original
  svn:externals property was set. It does not walk the complete tree
  to search for these kind of repositories.

* git-svn-externals-update complements the git-svn-externals-check
  script. The update script does an ``git svn fetch`` and ``git svn
  rebase`` for every directory in the location where the script is
  executed.

  This script must also be run in the directory where the original
  svn:externals property was set.


Feel free to use and improve these scripts.

- Mark van Lent <mark@vlent.nl>

Options
=======

* External repository's url can be rewritten, to use SVN+SSH instead of
  plain HTTP or HTTPS. To do so, do `export USE_SSH=yes` in your environment.
  This can be useful if you use ssh authentication, but other developers don't.
* If you don't want to pull all external repositories, you can create a
  .git_externals_exclude file which contains the local paths to be excluded,
  one per line, the same way they show up on the first field of git svn show-externals

- Alexander Artemenko <svetlyak.40wt@gmail.com>

