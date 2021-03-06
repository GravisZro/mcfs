SCFS is a component of [System X](https://github.com/GravisZro/SystemX)
# Service Connector File System
build status: [![Build Status](https://travis-ci.org/GravisZro/scfs.svg?branch=master)](https://travis-ci.org/GravisZro/scfs)
SCFS is a FUSE VFS that manages socket files for processes.  It's intended use is to provide a permissions based [IPC](https://en.wikipedia.org/wiki/Inter-process_communication) interface between daemons and client programs.

# Setup
Simply execute scfs and specify the mount directory.

example:
> sudo scfs /svc

Note: User must have permissions to the mount directory.

# How To Use
## Daemons
A daemon must create a socket file in a subdirectory matching the username used to execute the daemon.

example:
> sudo -u audio /usr/bin/audiomixerd

/usr/bin/audiomixerd may now create one or more socket files inside directory /svc/audio/
<br>Note: Directories are automatically created and destroyed.  Daemons can only create socket files.

## Client Programs
A client program only needs to try to open a specific socket for their daemon.
