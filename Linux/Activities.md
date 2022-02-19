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

## [Permissions](https://ryanstutorials.net/linuxtutorial/permissions.php)
-   First off, take a look at the permissions of your home directory, then have a look at the permissions of various files in there.
```bash
**➜** **~** ls -l 
total 0
drwx------@ 6 damianciepiela staff 192 Dec 30 18:35 **Applications**
drwx------@ 4 damianciepiela staff 128 Nov 27 13:46 **Creative Cloud Files**
drwx------@ 340 damianciepiela staff 10880 Feb 18 14:40 **Desktop**
drwx------+ 14 damianciepiela staff 448 Feb 19 19:12 **Documents**
drwx------@ 118 damianciepiela staff 3776 Feb 19 15:45 **Downloads**
...
```
-   Now let's go into your linuxtutorialwork directory and change the permissions of some of the files in there. Make sure you use both the shorthand and longhand form for setting permissions and that you also use a variety of absolute and relative paths. Try removing the read permission from a file then reading it. Or removing the write permission and then opening it in vi.
```bash
**➜** **permissions** touch testFile 
**➜** **permissions** mkdir test 
**➜** **permissions** touch anotherTestFile
**➜** **permissions** ls -l
total 0
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:28 anotherTestFile
drwxr-xr-x 2 damianciepiela staff 64 Feb 19 20:27 **test**
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:27 testFile
**➜** **permissions** chmod u-r anotherTestFile
**➜** **permissions** chmod 044 testFile 
**➜** **permissions** ls -l
total 0
--w-r--r-- 1 damianciepiela staff 0 Feb 19 20:28 anotherTestFile
drwxr-xr-x 2 damianciepiela staff 64 Feb 19 20:27 **test**
----r--r-- 1 damianciepiela staff 0 Feb 19 20:27 testFile
**➜** **permissions** vi testFile
"testFile" [Permission Denied]
**➜** **permissions** vi anotherTestFile
"anotherTestFile" [Permission Denied]
**➜** **permissions** cat testFile 
cat: testFile: Permission denied
**➜** **permissions** less anotherTestFile 
anotherTestFile: Permission denied
**➜** **permissions** chmod u+wr anotherTestFile testFile 
**➜** **permissions** ls -l 
total 0
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:28 anotherTestFile
drwxr-xr-x 2 damianciepiela staff 64 Feb 19 20:27 **test**
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:27 testFile
```
-   Let's play with directories now. Create a directory and put some files into it. Now play about with removing various permissions from yourself on that directory and see what you can and can't do.
```bash
**➜** **permissions** chmod 055 test 
**➜** **permissions** ls -l
total 0
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:28 anotherTestFile
d---r-xr-x 2 damianciepiela staff 64 Feb 19 20:27 **test**
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:27 testFile
**➜** **permissions** cd test 
cd: permission denied: test
**➜** **permissions** ls -l test 
total 0
ls: test: Permission denied
**➜** **permissions** mv anotherTestFile testFile ./test
mv: rename anotherTestFile to ./test/anotherTestFile: Permission denied
mv: rename testFile to ./test/testFile: Permission denied
**➜** **permissions** chmod u+r test
**➜** **permissions** ls -l ./test
total 0
**➜** **permissions** chmod u+x test
**➜** **permissions** cd test 
**➜** **test** cd ..
**➜** **permissions** mv anotherTestFile ./test
mv: rename anotherTestFile to ./test/anotherTestFile: Permission denied
**➜** **permissions** touch ./test/testFile2
touch: ./test/testFile2: Permission denied
**➜** **permissions** chmod u+w test
**➜** **permissions** mv anotherTestFile ./test
**➜** **permissions** touch ./test/testFile2
**➜** **permissions** ls -l ./test
total 0
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:28 anotherTestFile
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 20:41 testFile2
```
-   Finally, have an explore around the system and see what the general permissions are for files in other system directories such as /etc and /bin
```bash
**➜** **/etc** ls -l 
total 832
-rw-r--r-- 1 root wheel 515 Dec 8 00:39 afpovertcp.cfg
lrwxr-xr-x 1 root wheel 15 Dec 8 00:39 aliases -> postfix/aliases
-rw-r----- 1 root wheel 16384 Dec 8 00:39 aliases.db
drwxr-xr-x 9 root wheel 288 Dec 8 00:39 **apache2**
drwxr-xr-x 17 root wheel 544 Dec 8 00:39 **asl**
-rw-r--r-- 1 root wheel 1051 Dec 8 00:39 asl.conf
-rw-r--r-- 1 root wheel 149 Dec 8 00:39 auto_home
-rw-r--r-- 1 root wheel 195 Dec 8 00:39 auto_master
-rw-r--r-- 1 root wheel 1935 Dec 8 00:39 autofs.conf
...
**➜** **/etc** ls -l /bin 
total 9544
-rwxr-xr-x 1 root wheel 150608 Dec 8 00:39 [
-r-xr-xr-x 1 root wheel 1326560 Dec 8 00:39 bash
-rwxr-xr-x 1 root wheel 151792 Dec 8 00:39 cat
-rwxr-xr-x 1 root wheel 136944 Dec 8 00:39 chmod
-rwxr-xr-x 1 root wheel 152640 Dec 8 00:39 cp
-rwxr-xr-x 1 root wheel 1135936 Dec 8 00:39 csh
-rwxr-xr-x 1 root wheel 307104 Dec 8 00:39 dash
-rwxr-xr-x 1 root wheel 168912 Dec 8 00:39 date
-rwxr-xr-x 1 root wheel 151520 Dec 8 00:39 dd
-rwxr-xr-x 1 root wheel 151264 Dec 8 00:39 df
-rwxr-xr-x 1 root wheel 150336 Dec 8 00:39 echo
-rwxr-xr-x 1 root wheel 235248 Dec 8 00:39 ed
-rwxr-xr-x 1 root wheel 151008 Dec 8 00:39 expr
...
```

## [Filters](https://ryanstutorials.net/linuxtutorial/filters.php)
-   First off, you may want to make a file with data similar to our sample file.
```bash
**➜** **filters** touch data.txt 
**➜** **filters** vi data.txt 
**➜** **filters** cat data.txt 
Fred apples 20
Susy oranges 5
Mark watermellons 12
Robert pears 4
Terry oranges 9
Lisa peaches 7
Susy oranges 12
Mark grapes 39
Anne mangoes 7
Greg pineapples 3
Oliver rockmellons 2
Betty limes 14
```
-   Now play with each of the programs we looked at above. Make sure you use both relative and absolute paths.
```bash
**➜** **filters** head -5 ./data.txt 
Fred apples 20
Susy oranges 5
Mark watermellons 12
Robert pears 4
Terry oranges 9
**➜** **filters** tail -2 ./data.txt 
Oliver rockmellons 2
Betty limes 14
**➜** **filters** sort ./data.txt 
Anne mangoes 7
Betty limes 14
Fred apples 20
Greg pineapples 3
Lisa peaches 7
Mark grapes 39
Mark watermellons 12
Oliver rockmellons 2
Robert pears 4
Susy oranges 12
Susy oranges 5
Terry oranges 9
**➜** **filters** nl ./data.txt 
 1 Fred apples 20
 2 Susy oranges 5
 3 Mark watermellons 12
 4 Robert pears 4
 5 Terry oranges 9
 6 Lisa peaches 7
 7 Susy oranges 12
 8 Mark grapes 39
 9 Anne mangoes 7
 10 Greg pineapples 3
 11 Oliver rockmellons 2
 12 Betty limes 14
**➜** **filters** wc ./data.txt 
 12 36 197 ./data.txt
**➜** **filters** cut -f 1 -d ' ' ./data.txt 
Fred
Susy
Mark
Robert
Terry
Lisa
Susy
Mark
Anne
Greg
Oliver
Betty
**➜** **filters** sed 's/apples/test/g' ./data.txt
Fred test 20
Susy oranges 5
Mark watermellons 12
Robert pears 4
Terry oranges 9
Lisa peaches 7
Susy oranges 12
Mark grapes 39
Anne mangoes 7
Greg pinetest 3
Oliver rockmellons 2
Betty limes 14
**➜** **filters** uniq data.txt 
Fred apples 20
Susy oranges 5
Mark watermellons 12
Robert pears 4
Terry oranges 9
Lisa peaches 7
Susy oranges 12
Mark grapes 39
Anne mangoes 7
Greg pineapples 3
Oliver rockmellons 2
Betty limes 14
```
-   Have a look at the man page for each of the programs and try at least 2 of the command line options for them.
```bash
**➜** **filters** head -c20 ./data.txt 
Fred apples 20
Susy **%**
**➜** **filters** head -n2 ./data.txt 
Fred apples 20
Susy oranges 5
**➜** **filters** tail -2 ./data.txt 
Oliver rockmellons 2
Betty limes 14
**➜** **filters** tail -c20 ./data.txt 
ns 2
Betty limes 14
**➜** **filters** tail -2 -r ./data.txt
Betty limes 14
Oliver rockmellons 2
**➜** **filters** sort -c ./data.txt 
sort: ./data.txt:3: disorder: Mark watermellons 12
**➜** **filters** sort -u -o test.txt ./data.txt
**➜** **filters** nl -i2 ./data.txt 
 1 Fred apples 20
 3 Susy oranges 5
 5 Mark watermellons 12
 7 Robert pears 4
 9 Terry oranges 9
 11 Lisa peaches 7
 13 Susy oranges 12
 15 Mark grapes 39
 17 Anne mangoes 7
 19 Greg pineapples 3
 21 Oliver rockmellons 2
 23 Betty limes 14
**➜** **filters** nl -s '. ' -v10 ./data.txt 
 10. Fred apples 20
 11. Susy oranges 5
 12. Mark watermellons 12
 13. Robert pears 4
 14. Terry oranges 9
 15. Lisa peaches 7
 16. Susy oranges 12
 17. Mark grapes 39
 18. Anne mangoes 7
 19. Greg pineapples 3
 20. Oliver rockmellons 2
 21. Betty limes 14
**➜** **filters** wc -lm ./data.txt 
 12 197 ./data.txt
**➜** **filters** wc -lw ./data.txt
 12 36 ./data.txt
**➜** **filters** cut -f 1,2 -w ./data.txt
Fred apples
Susy oranges
Mark watermellons
Robert pears
Terry oranges
Lisa peaches
Susy oranges
Mark grapes
Anne mangoes
Greg pineapples
Oliver rockmellons
Betty limes
**➜** **filters** cut -f 1,2 -ws ./data.txt
Fred apples
Susy oranges
Mark watermellons
Robert pears
Terry oranges
Lisa peaches
Susy oranges
Mark grapes
Anne mangoes
Greg pineapples
Oliver rockmellons
Betty limes
**➜** **filters** sed -n '4p' ./data.txt 
Robert pears 4
**➜** **filters** sed -n '4,6!p' /Users/damianciepiela/linuxtutorialwork/filters/data.txt 
Fred apples 20
Susy oranges 5
Mark watermellons 12
Susy oranges 12
Mark grapes 39
Anne mangoes 7
Greg pineapples 3
Oliver rockmellons 2
Betty limes 14
**➜** **filters** uniq -d data.txt 
Susy oranges 5
Mark grapes 39
**➜** **filters** uniq -c ./data.txt 
 1 Fred apples 20
 3 Susy oranges 5
 1 Mark watermellons 12
 1 Robert pears 4
 1 Terry oranges 9
 1 Lisa peaches 7
 1 Susy oranges 12
 2 Mark grapes 39
 1 Anne mangoes 7
 1 Greg pineapples 3
 1 Oliver rockmellons 2
 1 Betty limes 14
```

## [Grep and Regular Expressions](https://ryanstutorials.net/linuxtutorial/grep.php)
-   First off, you may want to make a file with data similar to our sample file.
```bash
**➜** **grep** touch data.txt
**➜** **grep** vi data.txt
**➜** **grep** cat data.txt
Fred apples 20
Susy oranges 5
Mark watermellons 12
Robert pears 4
Terry oranges 9
Lisa peaches 7
Susy oranges 12
Mark grapes 39
Anne mangoes 7
Greg pineapples 3
Oliver rockmellons 2
Betty limes 14
```
-   Now play with some of the examples we looked at above.
```bash
**➜** **grep** egrep 'apples' data.txt 
Fred **apples** 20
Greg pine**apples** 3
**➜** **grep** egrep -c 'apples' data.txt
2
**➜** **grep** egrep -n 'apples' data.txt 
1:Fred **apples** 20
10:Greg pine**apples** 3
**➜** **grep** egrep '2.+' data.txt 
Fred apples **20**
**➜** **grep** egrep '3$' data.txt
Greg pineapples **3**
**➜** **grep** egrep '[p]{2}' data.txt
Fred a**pp**les 20
Greg pinea**pp**les 3
**➜** **grep** egrep '^[F-Z]' data.txt 
**F**red apples 20
**S**usy oranges 5
**M**ark watermellons 12
**R**obert pears 4
**T**erry oranges 9
**L**isa peaches 7
**S**usy oranges 12
**M**ark grapes 39
**G**reg pineapples 3
**O**liver rockmellons 2
```
-   Have a look at the man page for egrep and try atleast 2 of the command line options for them.
```bash
**➜** **grep** egrep -H 'apples' data.txt
data.txt:Fred **apples** 20
data.txt:Greg pine**apples** 3
**➜** **grep** egrep -c 'apples' data.txt
2
**➜** **grep** egrep -a 'apples' data.txt
Fred **apples** 20
Greg pine**apples** 3
```

## [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)
-   First off, experiment with saving output from various commands to a file. Overwrite the file and append to it as well. Make sure you are using a both absolute and relative paths as you go.
```bash
**➜** **grep** ls -l | tail -n +2 > text.txt
**➜** **grep** cat text.txt 
-rw-r--r-- 1 damianciepiela staff 197 Feb 19 21:55 data.txt
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 22:24 text.txt
**➜** **grep** chmod u-rw data.txt
**➜** **grep** cat data.txt 2>> text.txt 
**➜** **grep** cat text.txt 
-rw-r--r-- 1 damianciepiela staff 197 Feb 19 21:55 data.txt
-rw-r--r-- 1 damianciepiela staff 0 Feb 19 22:24 text.txt
cat: data.txt: Permission denied
**➜** **grep** chmod u+rw data.txt
**➜** **grep** cat text.txt 
cat: data.txt: Permission denied
 197 data.txt
**➜** **grep** ls -l /etc/ | tail -n +2 | cut -w -f 1 | sort | uniq > text.txt 
**➜** **grep** cat text.txt
-r--r-----
-r--r--r--
-rw-------
-rw-r-----
-rw-r--r--
-rw-r--r--@
drwxr-xr-x
lrwxr-xr-x
```
-   Now see if you can list only the 20th last file in the directory /etc.
```bash
**➜** **grep** ls /etc/ | tail -20 
rmtab
rpc
rtadvd.conf
security
services
shells
snmp
ssh
ssl
sudo_lecture
sudoers
sudoers.d
syslog.conf
ttys
uucp
wfs
xtab
zprofile
zshrc
zshrc_Apple_Terminal
```
-   Finally, see if you can get a count of how many files and directories you have the execute permission for in your home directory.
```bash
**➜** **grep** ls -l ~ | cut -w -f1| grep '^...x' | wc -l
 21
```

## [Process Management](https://ryanstutorials.net/linuxtutorial/piping.php)

-   First off, start a few programs in your desktop. Then use ps to identify their PID and kill them.
```bash
**➜** **grep** ps aux | grep 'firefox'
damianciepiela 8131 1.0 4.2 420540496 351648 ?? S 10:50PM 0:04.11 /Applications/Firefox.app/Contents/MacOS/**firefox**
damianciepiela 8206 0.0 0.0 408628368 1616 s000 S+ 10:50PM 0:00.00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn --exclude-dir=.idea --exclude-dir=.tox **firefox**
**➜** **grep** kill 8131 
**➜** **grep** ps aux | grep 'firefox'
damianciepiela 8245 0.0 0.0 408628368 1616 s000 S+ 10:50PM 0:00.00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn --exclude-dir=.idea --exclude-dir=.tox **firefox**
**➜** **grep** top
**➜** **grep** kill 8155
**➜** **grep** ps aux | grep 'Photo Booth'
damianciepiela 8536 14.2 0.6 409872880 50144 ?? S 10:52PM 0:06.67 /System/Applications/**Photo Booth**.app/Contents/MacOS/**Photo Booth**
damianciepiela 8721 0.0 0.0 408636560 1712 s000 S+ 10:52PM 0:00.00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn --exclude-dir=.idea --exclude-dir=.tox **Photo Booth**
**➜** **grep** kill 8536
```
-   Now see if you can do the same, but switch to another virtual console first.
-   Finally, play about with the command sleep and moving processes between the foreground and background.
```bash
**➜** **grep** sleep 20&
[1] 9161
**➜** **grep** sleep 15 
^Z
[2] + 9185 suspended sleep 15
**➜** **grep** jobs
[1] - running sleep 20
[2] + suspended sleep 15
**➜** **grep** fg %2
[2] - 9185 continued sleep 15
**➜** **grep** 
[1] + 9161 done sleep 20
**➜** **grep** sleep 15 
^Z
[1] + 9330 suspended sleep 15
**➜** **grep** bg %1
[1] - 9330 continued sleep 15
**➜** **grep** 
[1] - 9330 done sleep 15
```

## [Scripting](https://ryanstutorials.net/linuxtutorial/scripting.php)
-   First off, think about writing your own backup script. You can make it as simple or complex as you like. Maybe start off with a really simple one and progressively improve it.
```bash  
#!/bin/bash
if [ ! -d "$(pwd)/backup" ]; then
 mkdir backup
fi

if [ $# != 1 ]; then
 echo 'Usage: file to backup.'
 exit
fi
  
FILE=$(pwd)/$1  

if [ ! -f $FIL ]; then
 echo 'File does not exist!'
 exit
fi
  
DATE=`date +%F`
WORKING_DIR=$(pwd)/backup/$1_$DATE
if [ -f $WORKING_DIR ]; then
 echo 'Overwrite file?'
 read answer
 if [ $answer != 'y' ]
 then
 exit
 fi
fi
  
cp $FILE $WORKING_DIR

echo 'Backup completed'
```
-   Now see if you can write a script that will give you a report about a given directory. Things you could report on include
    -   How many files are in the directory?
    -   How many directories are in the directory?
    -   What is the biggest file?
    -   What is the most recently modified or created file?
    -   A list of people who own files in the directory.
    -   Anything else you can think of.
```bash
#!/bin/bash

echo Files in directory: `ls -l | cut -w -f 1 | grep '^-' | wc -l`
echo Directories in directory : `ls -l | cut -w -f 1 | grep '^d' | wc -l`
echo Biggest file: `ls -l | cut -w -f 5,9 | sort -r | cut -w -f 2 | head -1`
echo Most recently modified file: `ls -t | head -1`
echo People who own files in directory: `ls -l | cut -w -f 3 | uniq`
echo Scripts in directory: `ls -l | cut -w -f 9 | egrep '.sh$' | wc -l`
```
