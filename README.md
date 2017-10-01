# dokuwiki-sync
``` man page
Script to synchronise seperate dokuwiki trees

Here is the man page:

DOKUWIKI-SYNC(1)                       dokuwiki-sync                       DOKUWIKI-SYNC(1)

NAME
       dokuwiki-sync - backup/restore/synchronise dokuwiki trees

SYNOPSIS
       dokuwiki-sync [-n] [-x] [-v] [-h] <command> [file...]

DESCRIPTION
       dokuwiki-sync  is a script to ease synchronising two dokuwiki trees possibly on dif-
       ferent machines by exporting that data and updating changes between two trees

       Run dokuwiki-sync -h  to see the full set of options

OPTIONS
       -n     : Dry-run print commands instead of executing them

       -x     : Enabling tracing of shell script

       -h     : Print this information

       -v     : verbose mode - print out names of changed files

Commands
       backup <data> <tfile>
              Backup directory <data> into a tar file <tfile>

       - A tar file is created as using sudo in order to preserve ownership/dates

       restore <tfile> <dir>
              - Restore tar file <tfile> inside directory <dir>

       Extracts the tar file <tfile> into a directory <dir> which will  be  created  if  it
       doesn't exist.

       rsync-diff <d1> <d2>
              - prints itemized list of files changed from <d1> to <d2>

       rsync-update <d1> <d2>
              - rsync update changes from <d1> into <d2>

       diff-summary <d1> <d2>
              - prints summary of changes between directories <d1> and <d2>

       Typically  you  synchronise two dokuwiki trees by first backing up the data from one
       tree via backup command. Then extracting it out with  the  restore  command  on  the
       remote  machine  you  wish  to  update with changes. Then you check what changes are
       present using the rsync-diff command which usually  is  run  as  the  owner  of  the
       dokuwiki  data  for access permissions. Usually this is www-data You can use by run-
       ning it from a bash shell under that required user. e.g.

              sudo su -s /bin/bash www-data

       The diff-summary command will summarise the number  of  changes  in  each  direction
       between the trees.

       When you are comfortable with the changes you can update the changes from <d1> on to
       the <d2> tree with the rsync-update command.

       At each stage use the -n option to print out what command it will run with out actu-
       ally  running  them.   This let's use avoid surprises and understand exactly what it
       proposes to do.

                                         2017-09-30                        DOKUWIKI-SYNC(1)
```
