Bash-Accessible SSH File System (BASSHFS)
=========================================

Working with remote systems over SSH is common in HPC environments
where the size of data sets makes them nontrivial to relocate.  To run
arbitrary commands on that data, a full SSH session is required.  There
are cases, however, when the user may wish to perform simpler operations
such as checking file existence and size, viewing differences between
configuration files, creating directories, etc. that can be achieved
with more limited access.  Juggling multiple sessions to multiple hosts
may be inconvenient for such simple tasks.  BASSHFS is a tool that
allows users to perform such tasks within a single terminal on a single
host by transparently carrying out remote operations as needed to
present remote files as if they are locally mounted when using the bash
shell.

BASSHFS is similar to the existing SSHFS utility except it is does not
require FUSE kernel support.  Instead, BASSHFS uses the aliasing and
function mechanisms of the bash shell to intercept program invocations
and remap those that are supported to its own versions.  These internal
versions determine if files on the command line are local or remote.
Remote files are processed transparently using a persistent SSH
connection to the associated host(s).  Output associated with the local
and remote files is then multiplexed together into the standard unified
format associated with the original command.  To the user, it appears as
if all files reside on a local file system even though they may span
multiple files systems on multiple hosts.

To install, copy "basshfs" to a directory in $PATH and "basshfs.1" to
a directory in $MANPATH.  For usage details, see "basshfs.1" (in man
page format, viewable with "nroff -man").  For license details, see
"COPYING".

Questions, comments, fixes, and/or enhancements welcome.

--Paul Kolano <paul.kolano@nasa.gov>

