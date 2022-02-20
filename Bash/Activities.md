---

date: 20-02-2022 00:03:40
author: Damian Ciepiela

---
### `ris:At` Tags: #RyanTutorials #Bash
### `ris:GitBranch` Backlinks:
---
# `ris:GitCommit` Activities
## [Variables](https://ryanstutorials.net/bash-scripting-tutorial/bash-variables.php)
-   A good place to start is to create a simple script which will accept some command line arguments and **echo** out some details about them (eg, how many are there, what is the secone one etc).
```bash
#!/bin/bash
echo Number of arguments: $#
echo Arugments: $@
echo First: $1
echo Second: $2
```
-   Create a script which will print a random word. There is a file containing a list of words on your system (usually /usr/share/dict/words or /usr/dict/words). Hint: [Piping](https://ryanstutorials.net/linuxtutorial/piping.php#piping) will be useful here.
```bash
#!/bin/bash
WORD=$(sort -R /usr/share/dict/words | head -1)
echo $WORD
```
-   Expand the previous activity so that if a number is supplied as the first command line argument then it will select from only words with that many characters. Hint: [Grep](https://ryanstutorials.net/linuxtutorial/grep.php) may be useful here.
```bash
#!/bin/bash
WORD=$(sort -R /usr/share/dict/words | head -$1)
echo $WORD
```
-   Take a copy of the two files script1.sh and script2.sh above then experiment by tweaking them and running them and observing the output. This will help you get a feel for how exporting variables works.
```bash
#!/bin/bash
if [ $# != 1 ]; then
 exit
fi
WORD=$(egrep "^.{$1}$" < /usr/share/dict/words | sort -R | head -1)
echo $WORD
```
-   Now let's create a script which will take a filename as its first argument and create a dated copy of the file. eg. if our file was named file1.txt it would create a copy such as 2022-02-20_file1.txt. (To achieve this you will probably want to play with command substitution and the command **date**)
```bash
#!/bin/bash
if [ $# != 1 ]; then
 exit
fi
FILE=$1
cp $(pwd)/$FILE $(pwd)/`date +%F`_$FILE
```
-   **Challenge:** To make it a bit harder, see if you can get it so that the date is after the name of the file (eg. file1_2022-02-20.txt (The command **basename** can be useful here.)
```bash
#!/bin/bash
if [ $# != 1 ]; then
 exit
fi
FILE=$1
FILE_NAME=`basename $FILE | cut -d '.' -f1`
FILE_EXT=`basename $FILE | cut -d '.' -f2`
cp $(pwd)/$FILE $(pwd)/"$FILE_NAME"_`date +%F`."$FILE_EXT"
```
-   **Challenge:** Now see if you can expand the previous question to accept a list of files on the command line and it will create a named copy of all of them. (The command [xargs](https://ryanstutorials.net/linuxtutorial/bonus.php#xargs) may be useful here.)
```bash
#!/bin/bash
for FILE in "$@"; do
 FILE_NAME=`basename $FILE | cut -d '.' -f1`
 FILE_EXT=`basename $FILE | cut -d '.' -f2`
 cp $(pwd)/$FILE $(pwd)/"$FILE_NAME"_`date +%F`."$FILE_EXT"
done
```

## [User input](https://ryanstutorials.net/bash-scripting-tutorial/bash-input.php)
-   Create a simple script which will ask the user for a few pieces of information then combine this into a message which is echo'd to the screen.
```bash
#!/bin/bash
read -p "Your name: " NAME
read -p "Your last name: " LAST_NAME
read -p "Date of birth: " BIRTH_DATE
echo Your first name: $NAME
echo Your last name: $LAST_NAME
echo Date of birth: $BIRTH_DATE
```
-   Add to the previous script to add in some data coming from command line arguments and maybe some of the other system variables.
```bash
#!/bin/bash
read -p "Your name: " NAME
read -p "Your last name: " LAST_NAME
read -p "Date of birth: " BIRTH_DATE

echo Your first name: $NAME
echo Your last name: $LAST_NAME
echo Date of birth: $BIRTH_DATE

echo My favorite food:
for FOOD in "$@"; do
        echo $FOOD
done
echo My home directory: $HOME
```
-   Create a script which will take data from STDIN and print the 3rd line only.
```bash
#!/bin/bash
cat /dev/stdin | sed -n "3p"
```
-   Now play about with creating a script which will behave as a filter. Create a script which will rearrange the output of the command **ls -l** in a useful way (eg maybe you only print the filename, size and owner) (Hint: [awk](https://ryanstutorials.net/linuxtutorial/bonus.php#awk) can be useful here).
```bash
#!/bin/bash
ls -lh | awk '{print $9" "$5" "$3}'
```
