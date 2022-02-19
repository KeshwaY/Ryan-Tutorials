---

date: 18-02-2022 18:43:51
author: Damian Ciepiela

---
### `ris:At` Tags: #RyanTutorials #Linux 
### `ris:GitBranch` Backlinks:
---
# `ris:GitCommit` Activities
## [Navigation](https://ryanstutorials.net/linuxtutorial/navigation.php)
- Let's start by getting familiar with moving around. Use the commands cd and ls to explore what directories are on your system and what's in them. Make sure you use a variety of relative and absolute paths. Some interesting places to look at are:
```bash
**➜** **Linux** **git:(****main****)** **✗** pwd
/Users/damianciepiela/Library/Mobile Documents/iCloud~md~obsidian/Documents/Damian/Epam/Ryan tutorials/Linux
**➜** **Linux** **git:(****main****)** **✗** ls -l 
total 8
-rw-r--r-- 1 damianciepiela staff 522 Feb 18 19:02 Activities.md
**➜** **Linux** **git:(****main****)** **✗** ls . 
Activities.md
**➜** **Linux** **git:(****main****)** **✗** cd ..
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -l
total 0
drwxr-xr-x 2 damianciepiela staff 64 Feb 18 18:33 **Bash**
drwxr-xr-x 3 damianciepiela staff 96 Feb 18 18:33 **Linux**
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -l ./Linux
total 8
-rw-r--r-- 1 damianciepiela staff 1139 Feb 18 19:03 Activities.md
**➜** **Ryan tutorials** **git:(****main****)** **✗** cd ./../../
**➜** **Damian** pwd
/Users/damianciepiela/Library/Mobile Documents/iCloud~md~obsidian/Documents/Damian
**➜** **Damian** cd /var/log 
**➜** **log** ls -l 
total 42064
drwxr-xr-x 2 root wheel 64 Dec 8 00:39 **CoreDuet**
...
**➜** **log** cd ~/Desktop
**➜** **Desktop**
```
-   Now go to your home directory using 4 different methods.
```bash
**➜** **Desktop** cd ~
**➜** **~** pwd
/Users/damianciepiela
**➜** **~** cd /Users/damianciepiela
**➜** **~** pwd
/Users/damianciepiela
**➜** **~** cd $HOME
**➜** **~** pwd
/Users/damianciepiela
**➜** **~** cd
**➜** **~** pwd
/Users/damianciepiela
```

## [More about files](https://ryanstutorials.net/linuxtutorial/aboutfiles.php)
-   Try running the command **file** giving it a few different entries. Make sure you use a variety of absolute and relative paths when doing this.
```bash
**➜** **Ryan tutorials** **git:(****main****)** **✗** file ./Linux/Activities.md 
./Linux/Activities.md: Unicode text, UTF-8 text
**➜** **Ryan tutorials** **git:(****main****)** **✗** file /Users/damianciepiela 
/Users/damianciepiela: directory
**➜** **Ryan tutorials** **git:(****main****)** **✗** cd ~
**➜** **~** file ./Documents/Adobe 
./Documents/Adobe: directory  
**➜** **~** file /etc/group 
/etc/group: ASCII text
**➜** **~** cd /etc
**➜** **/etc** file ../var/log/daily.out 
../var/log/daily.out: ASCII text
```
-   Now issue a command that will list the contents of your home directory including hidden files and directories.
```bash
**➜** **/etc** cd 
**➜** **~** ls -a
**.**
**..**
.CFUserTextEncoding
.DS_Store
**.Trash**
**.android**
.bash_history
.bash_profile
**.config**
**.dotnet**
...
**➜** **~** ls -la
total 552
drwxr-xr-x+ 68 damianciepiela staff 2176 Feb 18 19:28 **.**
drwxr-xr-x 5 root admin 160 Dec 8 00:39 **..**
-r-------- 1 damianciepiela staff 7 May 25 2021 .CFUserTextEncoding
-rw-r--r--@ 1 damianciepiela staff 16388 Feb 8 11:04 .DS_Store
drwx------ 4 damianciepiela staff 128 Feb 18 14:02 **.Trash**
drwxr-xr-x 3 damianciepiela staff 96 Oct 22 14:25 **.android**
-rw------- 1 damianciepiela staff 12 Feb 18 18:44 .bash_history
-rw-r--r-- 1 damianciepiela staff 150 Oct 19 20:42 .bash_profile
drwxr-xr-x 8 damianciepiela staff 256 Jan 13 19:12 **.config**
drwxr-xr-x 11 damianciepiela staff 352 Feb 7 10:59 **.dotnet**
```

## [Manual Pages](https://ryanstutorials.net/linuxtutorial/manual.php)
-   Have a skim through the man page for **ls**. Have a play with some of the command line options you find there. Make sure you play with a few as combinations. Also make sure you play with **ls** with both absolute and relative paths.
```bash
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -lF
total 0
drwxr-xr-x 2 damianciepiela staff 64 Feb 18 18:33 **Bash**/
drwxr-xr-x 3 damianciepiela staff 96 Feb 18 18:33 **Linux**/
**➜** **Ryan tutorials** **git:(****main****)** **✗** cd ..
**➜** **Epam** ls -R 
**Ryan tutorials**

./Ryan tutorials:
**Bash** **Linux** 

./Ryan tutorials/Bash:

./Ryan tutorials/Linux:

Activities.md
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -lin
total 0
31331921 drwxr-xr-x 2 501 20 64 Feb 18 18:33 **Bash**
31331919 drwxr-xr-x 3 501 20 96 Feb 18 18:33 **Linux**
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -t
**Bash** **Linux**
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -tr
**Linux** **Bash**
**➜** **Ryan tutorials** **git:(****main****)** **✗** ls -lSh
total 0
drwxr-xr-x 3 damianciepiela staff 96B Feb 18 18:33 **Linux**
drwxr-xr-x 2 damianciepiela staff 64B Feb 18 18:33 **Bash**
```
-   Now try doing a few searches through the man pages. Depending on your chosen terms you may get quite a large listing. Look at a few of the pages to get a feel for what they are like.
```bash
**➜** **Ryan tutorials** **git:(****main****)** **✗** man -k super   
postsuper(1) - Postfix superintendent
DBIx::Class::InflateColumn::File(3pm) - DEPRECATED (superseded by DBIx::Class::InflateColumn::FS)
Moose::Exception(3pm) - Superclass for Moose internal exceptions
Moose::Exception(3pm) - Superclass of all Moose exceptions
MooseX::Declare::Syntax::Extending(3pm) - Extending with superclasses
postsuper(1) - Postfix superintendent
(END)
**➜** **Ryan tutorials** **git:(****main****)** **✗** man -k user
applygnupgdefaults(8) - Run gpgconf --apply-defaults for all users
git-bugreport(1) - Collect information for user to file a bug report
git-credential(1) - Retrieve and store user credentials
git-credential-cache--daemon(1) - Temporarily store user credentials in memory
gitcredentials(7) - Providing usernames and passwords to Git
gitcvs-migration(7) - Git for CVS users
gnutls_psk_server_get_username(3) - API function
gnutls_psk_server_get_username2(3) - API function
gnutls_srp_server_get_username(3) - API function
...
(END)
**➜** **Ryan tutorials** **git:(****main****)** **✗** man -k passwd
chkpasswd(8) - verifies user password against various systems
firmwarepasswd(8) - tool for setting and removing firmware passwords on a system
htpasswd(1) - Manage user files for basic authentication
kpasswd(1) - Kerberos 5 password changing program
kpasswdd(8) - Kerberos 5 password changing server
...
(END)
```

## [File manipulation](https://ryanstutorials.net/linuxtutorial/filemanipulation.php)
-   Start by creating a directory in your home directory in which to experiment.
```bash
**➜** **Ryan tutorials** **git:(****main****)** man git 
**➜** **Ryan tutorials** **git:(****main****)** cd 
**➜** **~** mkdir test
**➜** **~** cd test
```
-   In that directory, create a series of files and directories (and files and directories in those directories).
```bash
**➜** **test** mkdir testDirectory
**➜** **test** mkdir 'test directory'    
**➜** **test** touch testFile 
**➜** **test** touch 'test file'
**➜** **test** ls
**test directory** test file **testDirectory** testFile
```
-   Now rename a few of those files and directories.
```bash
**➜** **test** mv testDirectory testDirectory1 
**➜** **test** mv test\ directory test\ directory2
**➜** **test** ls
**test directory2** test file **testDirectory1** testFile
**➜** **test** mv testFile testFile1
**➜** **test** mv test\ file test\ file2 
**➜** **test** ls
**test directory2** test file2 **testDirectory1** testFile1
```
-   Delete one of the directories that has other files and directories in them.
```bash
**➜** **test** mv test\ file2 testDirectory1
**➜** **test** mv testFile1 test\ directory2
**➜** **test** mv testDirectory1 test\ directory2
**➜** **test** rm -r test\ directory2 
**➜** **test** ls
```
-   Move back to your home directory and from there copy a file from one of your subdirectories into the initial directory you created.
```bash
**➜** **test** cd
**➜** **~** cp ./backups/world.20211107165743/icon.png ./test
```
-   Now move that file back into another directory.
```bash
**➜** **~** ls ./test 
icon.png
**➜** **~** mv ./test/icon.png ./Documents 
**➜** **~** ls ./Documents
**➜** **~** ls -lt ./Documents 
total 24
-rw-r--r-- 1 damianciepiela staff 10102 Feb 19 19:09 icon.png
```
-   Rename a few files
```bash
**➜** **~** mv test test123
**➜** **~** mv Documents documents
**➜** **~** mv documents Documents
**➜** **~** mv test123 test
```
-   Next, move a file and rename it in the process.
```bash
**➜** **~** mv icon.png test 
**➜** **~** mkdir test2 
**➜** **~** mv ./test/icon.png ./test2/renamed_icon.png
**➜** **~** ls test2 
renamed_icon.png
**➜** **~** ls test
```

## [Vi](https://ryanstutorials.net/linuxtutorial/vi.php)
-   Start by creating a file and putting some content into it.
```bash
**➜** **~** touch testFile 
**➜** **~** vi testFile
```
-   Save the file and view it in both cat and less
```bash
**➜** **~** cat testFile 
Test
**➜** **~** vi testFile 
**➜** **~** less testFile
```
-   Go back into the file in vi and enter some more content.
```bash
**➜** **~** vi testFile 
```
-   Move around the content using at least 6 different movement commands.
```bash
9G, 5b, b, w, e, ^, $, {, }
```
-   Play about with several of the delete commands, especially the ones that incorporate a movement command. Remember you may undo your changes so you don't have to keep putting new content in.
```bash
x, 10x, dd, 6dd
```

## [Wildcards](https://ryanstutorials.net/linuxtutorial/wildcards.php)
-   A good directory to play with is /etc which is a directory containing config files for the system. As a normal user you may view the files but you can't make any changes so we can't do any harm. Do a listing of that directory to see what's there. Then pick various subsets of files and see if you can create a pattern to select only those files.
```bash
**➜** **/etc** ls -lh *.conf
-rw-r--r-- 1 root wheel 1.0K Dec 8 00:39 asl.conf
-rw-r--r-- 1 root wheel 1.9K Dec 8 00:39 autofs.conf
-rw-r--r-- 1 root wheel 0B Dec 8 00:39 kern_loader.conf
...
**➜** **/etc** ls -d *.d 
**emond.d** **manpaths.d** **newsyslog.d** **pam.d** **paths.d** **sudoers.d**
**➜** **/etc** ls -d ?a*
bashrc man.conf master.passwd passwd **racoon**
bashrc_Apple_Terminal manpaths nanorc paths
mail.rc **manpaths.d** **pam.d** **paths.d**
```
-   Do a listing of /etc with only files that contain an extension.
```bash
**➜** **/etc** ls -lh *.conf
-rw-r--r-- 1 root wheel 1.0K Dec 8 00:39 asl.conf
-rw-r--r-- 1 root wheel 1.9K Dec 8 00:39 autofs.conf
-rw-r--r-- 1 root wheel 0B Dec 8 00:39 kern_loader.conf
...
```
-   What about only a 3 letter extension?
```bash
**➜** **/etc** ls *.??? 
afpovertcp.cfg postgres-reg.ini
```
-   How about files whose name contains an uppercase letter? (hint: [[:upper:]] may be useful here)
```bash
**➜** **/etc** ls -l *[[:upper:]]*
-rw-r--r-- 1 root wheel 9309 Dec 8 00:39 bashrc_Apple_Terminal
-rw-r--r-- 1 root wheel 9335 Dec 8 00:39 zshrc_Apple_Terminal
```
-   Can you list files whose name is 4 characters long?
```bash
**➜** **/etc** ls -d ????
**cups** **snmp** ttys **uucp** xtab
```