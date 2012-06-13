git-svn-ext
===========

This work is based on git-svn-clone-externals and the associated
scripts written by Andre Pang.

The methodology remains the same.  Put git-svn-ext in your path and
run it from the top-level tree checked out with git-svn.  git-svn-ext
will detect and git-svn clone the externals using the following
method:

* git svn clone each external into a .git_externals/ directory.
* symlink the cloned repository in .git_externals/ to the proper directory
  name.
* add the symlink and .git_externals/ to the .git/info/excludes/ file, so that
  you're not pestered about it when performing a git status.

but the code has been converted to python as one script with
sub-commands, supports newer subversion urls, and adds a few new
features.

From the usage output:

Usage: ./git-svn-ext <sub command> [sub command args]

  sub commmands:
    clone          : clone all svn externals into .git_externals
      (warning: removes local changes and commits on subsequent runs)
    update         : Updates all svn externals (git svn fetch[ --revision]/rebase --local)
    check-unpushed : Check if local git-svn checkout has unpushed commits
    check          : run 'git status' and 'check-unpushed' for all externals
    for-all        : run a command against all externals
      (ie: git svn-ext for-all git grep 'whatever')

  Notes:
    externals may be ignored if listed in .git_external_excludes

Authors
=======
- Andre Pang <ozone@algorithm.com.au>
- Mark van Lent <mark@vlent.nl>
- Alexander Artemenko <svetlyak.40wt@gmail.com>
- Wade Berrier <wberrier@gmail.com>

