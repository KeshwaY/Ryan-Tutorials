---

date: 18-02-2022 18:43:51
author: Damian Ciepiela

---
### `ris:At` Tags: #Template 
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