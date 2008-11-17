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

