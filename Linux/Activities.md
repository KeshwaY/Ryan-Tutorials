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
