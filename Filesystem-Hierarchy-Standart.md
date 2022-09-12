# Filesystem Hierarchy Standard (FHS)

The Filesystem Hierarchy Standard (FHS) is a guideline for the directory structure for Unix-like operating systems.

The standard is aimed at software developers and administrators. The standard is intended to improve the Internet operability

of computer programs by making the directory structure predictable. The development of the standard began

1993 and was initially only related to Linux.

## File categories

The FHS distinguishes files into two categories:

Static or variable.  
A file is considered static if it does not change without the intervention of the system administrator.  
All other files are considered variable

shareable or unsherable  
A file is considered shareable if it can be used by other computers via a computing network.  
All other files are considered unsharable

These aspects result in four categories of files:

static shareable  
static unshareable  
variable shareable  
variable unshareable

Root directory

The root directory (volume) must contain all files which are necessary to boot the operating system

and to add new partitions.

## Main directories

<table><tbody><tr><td>Path</td><td>Description</td></tr><tr><td>/bin</td><td>binary files</td></tr><tr><td>/boot</td><td>files of the bootloader</td></tr><tr><td>/dev</td><td>device files</td></tr><tr><td colspan="1">/etc</td><td colspan="1">host system configuration</td></tr><tr><td colspan="1">/lib</td><td colspan="1">basic libraries and kernel modules</td></tr><tr><td colspan="1">/media</td><td colspan="1">mount point for removable media</td></tr><tr><td colspan="1">/mnt</td><td colspan="1">for temporarily mounted file systems</td></tr><tr><td colspan="1">/opt</td><td colspan="1">application programs</td></tr><tr><td colspan="1">/run</td><td colspan="1">for running processes relevant data</td></tr><tr><td colspan="1">/sbin</td><td colspan="1">essential binaries of the system</td></tr><tr><td colspan="1">/srv</td><td colspan="1">data for services</td></tr><tr><td colspan="1">/tmp</td><td colspan="1">temporary files</td></tr><tr><td colspan="1">/usr</td><td colspan="1">secondary hierarchy (second directory)</td></tr><tr><td colspan="1">/var</td><td colspan="1">variable data</td></tr></tbody></table>
