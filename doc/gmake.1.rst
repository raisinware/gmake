=====
gmake
=====

-----------------------------------------------
GNU make utility to maintain groups of programs
-----------------------------------------------

:Date:           31 May 2022
:Version:        GNU
:Manual section: 1
:Manual group:   User Commands


SYNOPSIS
========

**gmake** [*OPTION*]... [*TARGET*]...

DESCRIPTION
===========

The *gmake* utility will determine automatically which pieces of a large
program need to be recompiled, and issue the commands to recompile them.
The manual describes the GNU implementation of **make**, which was
written by Richard Stallman and Roland McGrath, and is currently
maintained by Paul Smith. Our examples show C programs, since they are
very common, but you can use **gmake** with any programming language
whose compiler can be run with a shell command. In fact, **gmake** is not
limited to programs. You can use it to describe any task where some
files must be updated automatically from others whenever the others
change.

To prepare to use **gmake**, you must write a file called the *makefile*
that describes the relationships among files in your program, and
provides commands for updating each file. In a program, typically the
executable file is updated from object files, which are in turn made by
compiling source files.

Once a suitable makefile exists, each time you change some source files,
this simple shell command:

   **gmake**

suffices to perform all necessary recompilations. The **gmake** program
uses the makefile description and the last-modification times of the
files to decide which of the files need to be updated. For each of those
files, it issues the commands recorded in the makefile.

**gmake** executes commands in the *makefile* to update one or more
*targets*, where *target* is typically a program. If no **-f** option is
present, **gmake** will look for the makefiles *GNUmakefile*, *makefile*,
and *Makefile*, in that order.

Normally you should call your makefile either *makefile* or *Makefile*.
(We recommend *Makefile* because it appears prominently near the
beginning of a directory listing, right near other important files such
as *README*.) The first name checked, *GNUmakefile*, is not recommended
for most makefiles. You should use this name if you have a makefile that
is specific to GNU **gmake**, and will not be understood by other
versions of **gmake**. If *makefile* is '-', the standard input is read.

**gmake** updates a target if it depends on prerequisite files that have
been modified since the target was last modified, or if the target does
not exist.

OPTIONS
=======

**-b**, **-m**
   These options are ignored for compatibility with other versions of
   **gmake**.

**-B**, **--always-make**
   Unconditionally make all targets.

**-C** *dir*, **--directory**\ =\ *dir*
   Change to directory *dir* before reading the makefiles or doing
   anything else. If multiple **-C** options are specified, each is
   interpreted relative to the previous one: **-C**/ **-C**\ etc is
   equivalent to **-C**/etc. This is typically used with recursive
   invocations of **gmake**.

**-d**
   Print debugging information in addition to normal processing. The
   debugging information says which files are being considered for
   remaking, which file-times are being compared and with what results,
   which files actually need to be remade, which implicit rules are
   considered and which are applied---everything interesting about how
   **gmake** decides what to do.

**--debug**\ *[=FLAGS]*
   Print debugging information in addition to normal processing. If the
   *FLAGS* are omitted, then the behavior is the same as if **-d** was
   specified. *FLAGS* may be any or all of the following names, comma-
   or space-separated. Only the first character is significant: the rest
   may be omitted: *all* for all debugging output (same as using
   **-d**), *basic* for basic debugging, *verbose* for more verbose
   basic debugging, *implicit* for showing implicit rule search
   operations, *jobs* for details on invocation of commands, *makefile*
   for debugging while remaking makefiles, *print* shows all recipes
   that are run even if they are silent, and *why* shows the reason
   **gmake** decided to rebuild each target. Use *none* to disable all
   previous debugging flags.

**-e**, **--environment-overrides**
   Give variables taken from the environment precedence over variables
   from makefiles.

**-E** *string*, **--eval** *string*
   Interpret *string* using the **eval** function, before parsing any
   makefiles.

**-f** *file*, **--file**\ =\ *file*, **--makefile**\ =\ *FILE*
   Use *file* as a makefile.

**-i**, **--ignore-errors**
   Ignore all errors in commands executed to remake files.

**-I** *dir*, **--include-dir**\ =\ *dir*
   Specifies a directory *dir* to search for included makefiles. If
   several **-I** options are used to specify several directories, the
   directories are searched in the order specified. Unlike the arguments
   to other flags of **gmake**, directories given with **-I** flags may
   come directly after the flag: **-I**\ *dir* is allowed, as well as
   **-I** *dir*. This syntax is allowed for compatibility with the C
   preprocessor's **-I** flag.

**-j** [*jobs*], **--jobs**\ [=\ *jobs*]
   Specifies the number of *jobs* (commands) to run simultaneously. If
   there is more than one **-j** option, the last one is effective. If
   the **-j** option is given without an argument, **gmake** will not
   limit the number of jobs that can run simultaneously.

**--jobserver-style=**\ *style*
   The style of jobserver to use. The *style* may be one of **fifo**,
   **pipe**, or **sem** (Windows only).

**-k**, **--keep-going**
   Continue as much as possible after an error. While the target that
   failed, and those that depend on it, cannot be remade, the other
   dependencies of these targets can be processed all the same.

**-l** [*load*], **--load-average**\ [=\ *load*]
   Specifies that no new jobs (commands) should be started if there are
   others jobs running and the load average is at least *load* (a
   floating-point number). With no argument, removes a previous load
   limit.

**-L**, **--check-symlink-times**
   Use the latest mtime between symlinks and target.

**-n**, **--just-print**, **--dry-run**, **--recon**
   Print the commands that would be executed, but do not execute them
   (except in certain circumstances).

**-o** *file*, **--old-file**\ =\ *file*, **--assume-old**\ =\ *file*
   Do not remake the file *file* even if it is older than its
   dependencies, and do not remake anything on account of changes in
   *file*. Essentially the file is treated as very old and its rules are
   ignored.

**-O**\ [*type*], **--output-sync**\ [=\ *type*]
   When running multiple jobs in parallel with **-j**, ensure the output
   of each job is collected together rather than interspersed with
   output from other jobs. If *type* is not specified or is **target**
   the output from the entire recipe for each target is grouped
   together. If *type* is **line** the output from each command line
   within a recipe is grouped together. If *type* is **recurse** output
   from an entire recursive make is grouped together. If *type* is
   **none** output synchronization is disabled.

**-p**, **--print-data-base**
   Print the data base (rules and variable values) that results from
   reading the makefiles; then execute as usual or as otherwise
   specified. This also prints the version information given by the
   **-v** switch (see below). To print the data base without trying to
   remake any files, use *make -p -f/dev/null*.

**-q**, **--question**
   \``Question mode''. Do not run any commands, or print anything; just
   return an exit status that is zero if the specified targets are
   already up to date, nonzero otherwise.

**-r**, **--no-builtin-rules**
   Eliminate use of the built-in implicit rules. Also clear out the
   default list of suffixes for suffix rules.

**-R**, **--no-builtin-variables**
   Don't define any built-in variables.

**-s**, **--silent**, **--quiet**
   Silent operation; do not print the commands as they are executed.

**--no-silent**
   Cancel the effect of the **-s** option.

**-S**, **--no-keep-going**, **--stop**
   Cancel the effect of the **-k** option.

**-t**, **--touch**
   Touch files (mark them up to date without really changing them)
   instead of running their commands. This is used to pretend that the
   commands were done, in order to fool future invocations of **gmake**.

**--trace**
   Information about the disposition of each target is printed (why the
   target is being rebuilt and what commands are run to rebuild it).

**-v**, **--version**
   Print the version of the **gmake** program plus a copyright, a list of
   authors and a notice that there is no warranty.

**-w**, **--print-directory**
   Print a message containing the working directory before and after
   other processing. This may be useful for tracking down errors from
   complicated nests of recursive **gmake** commands.

**--no-print-directory**
   Turn off **-w**, even if it was turned on implicitly.

**--shuffle**\ *[=MODE]*
   Enable shuffling of goal and prerequisite ordering. *MODE* is one of
   *none* to disable shuffle mode, *random* to shuffle prerequisites in
   random order, *reverse* to consider prerequisites in reverse order,
   or an integer *<seed>* which enables *random* mode with a specific
   *seed* value. If *MODE* is omitted the default is *random*.

**-W** *file*, **--what-if**\ =\ *file*, **--new-file**\ =\ *file*, **--assume-new**\ =\ *file*
   Pretend that the target *file* has just been modified. When used with
   the **-n** flag, this shows you what would happen if you were to
   modify that file. Without **-n**, it is almost the same as running a
   *touch* command on the given file before running **gmake**, except
   that the modification time is changed only in the imagination of
   **gmake**.

**--warn-undefined-variables**
   Warn when an undefined variable is referenced.

EXIT STATUS
===========

GNU **gmake** exits with a status of zero if all makefiles were
successfully parsed and no targets that were built failed. A status of
one will be returned if the **-q** flag was used and **gmake** determines
that a target needs to be rebuilt. A status of two will be returned if
any errors were encountered.

SEE ALSO
========

The full documentation for **gmake** is available at
*https://www.gnu.org/software/make/manual/make.html*

BUGS
====

See the chapter \``Problems and Bugs'' in *The GNU Make Manual*.

AUTHOR
======

This manual page contributed by Dennis Morse of Stanford University.
Further updates contributed by Mike Frysinger. It has been reworked by
Roland McGrath. Maintained by Paul Smith. Conversion to reStructuredText
and light adjustments by raisinware.

COPYRIGHT
=========

Copyright © 1992-1993, 1996-2022 Free Software Foundation, Inc. This
file is part of *GNU make*.

GNU Make is free software; you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation; either version 3 of the License, or (at your
option) any later version.

GNU Make is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for
more details.

You should have received a copy of the GNU General Public License along
with this program. If not, see *https://www.gnu.org/licenses/*.
