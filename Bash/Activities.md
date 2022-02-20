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

## [Arithmetic](https://ryanstutorials.net/bash-scripting-tutorial/bash-arithmetic.php)
-   Create a simple script which will take two command line arguments and then multiply them together using each of the methods detailed above.
```bash
#!/bin/bash
let "a = $1 * $2"
echo $a

expr $1 \* $2

b=$(( $1 * $2 ))
echo $b
```
-   Write a Bash script which will print tomorrows date. (Hint: use the command **date**)
```bash
#!/bin/bash
today=$(date +%s)
tomorrow=$(( $today + 86400 ))
echo $(date -r $tomorrow)
```
-   Remember when we looked at [variables](https://ryanstutorials.net/bash-scripting-tutorial/bash-variables.php) we discovered $RANDOM will return a random number. This number is between 0 and 32767 which is not always the most useful. Let's write a script which will use this variable and some arithmetic (hint: play with modulus) to return a random number between 0 and 100.
```bash
#!/bin/bash
echo $(($RANDOM % 100))
```
-   Now let's play with the previous script. Modify it so that you can specify as a command line argument the upper limit of the random number. Can you make it so that a lower limit can be specified also? eg. if I ran ./random.sh 10 45 it would only return random numbers between 10 and 45.
```bash
#!/bin/bash
echo $(($RANDOM % $2 + $1))
```

## [If Statements](https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php#introduction)
-   Create a Bash script which will take 2 numbers as command line arguments. It will print to the screen the larger of the two numbers.
```bash
#!/bin/bash
if (( $1 > $2 ))
then
        echo $1
else
        echo $2
fi
```
-   Create a Bash script which will accept a file as a command line argument and analyse it in certain ways. eg. you could check if the file is executable or writable. You should print a certain message if true and another if false.
```bash
#!/bin/bash
FILE=$(pwd)/$1
if [ -w $FILE ] && [ -x $FILE ]
then
        echo File is writable and executable
elif [ ! -w $FILE ] && [ -x $FILE ]
then
        echo File is executable
elif [ -w $FILE ] && [ ! -x $FILE ]
then
        echo File is writable
else
        echo File is not writable nor exectubale
fi
```
-   Create a Bash script which will print a message based upon which day of the week it is (eg. 'Happy hump day' for Wedensday, 'TGIF' for Friday etc).
```bash
#!/bin/bash
DAY=`date +%A`
case $DAY in
        Monday)
                echo Monday
        ;;
        Tuesday)
                echo Tuesday
        ;;
        Wednesday)
                echo Wednesday
        ;;
        Thursday)
                echo Thursday
        ;;
        Friday)
                echo Friday
        ;;
        Saturday)
                echo Saturday
        ;;
        Sunday)
                echo Sunday
        ;;
esac
```

## [Loops](https://ryanstutorials.net/bash-scripting-tutorial/bash-loops.php)
-   Create a simple script which will print the numbers 1 - 10 (each on a separate line) and whether they are even or odd.
```bash
#!/bin/bash
for i in {1..10}
do
        echo $i
        if (( i % 2 == 0))
        then
                echo Even
        else
                echo Odd
        fi
done
```
-   Write a Bash script which will take a single command line argument (a directory) and will print each entry in that directory. If the entry is a file it will print it's size. If the entry is a directory it will print how many items are in that directory.
```bash
#!/bin/bash
MYDIR=$(pwd)/$1/
for FILE in $MYDIR/*
do
        if [ -d $FILE ]
        then
                COUNT=0
                for INNERFILE in $FILE/*
                do
                        ((COUNT++))
                done
                echo Directory $(basename $FILE), files in directory: $COUNT
        else
                echo File $(basename $FILE), size $(ls -lh $FILE | cut -w -f 5)
        fi
done
```
-   Create a command line version of the game [Mastermind](http://codebreaker.creativitygames.net/). Instead of coloured marbles you could use letters or numbers or be creative and find another way.
```bash
#!/bin/bash
SECRET=()
for i in {0..4}
do
	SECRET[i]=$(( $RANDOM % 8 + 1 ))
done
echo ${SECRET[@]}

TRIES=1
MAX_TRIES=8

WHITE="W"
BLACK="B"
NONE="N"
HELP_TEXT="$WHITE - WHITE, $BLACK - BLACK, $NONE - None match"

RESULT=1

while [ $TRIES -le $MAX_TRIES ]
do
	read -p "Enter five number form 1 to 8 (ex. 1 8 2 7 3): " INPUT
	ARR=( $INPUT )
	if (( ${#ARR[@]} != 5 ))
	then
		continue
	fi
	OUTPUT=""
	COUNTER=0
	for I in {0..4}
	do
		#echo ${SECRET[I]}
		#echo ${ARR[I]}
		if [ ${SECRET[I]} -eq ${ARR[I]} ]
		then
			(( COUNTER++ ))
			OUTPUT+=$WHITE
		else
			FOUND=1
			for J in {0..4}
			do
				if [ ${SECRET[J]} -eq ${ARR[I]} ]
				then
					FOUND=0
				fi
			done
			if (( FOUND == 0 ))
			then
				OUTPUT+=$BLACK
			else
				OUTPUT+=$NONE
			fi
		fi
	done
	echo $OUTPUT
	echo $HELP_TEXT
	echo Tries: $TRIES
	if (( COUNTER == 5 ))
	then
		RESULT=0
		break
	fi
	(( TRIES++ ))
done
if (( RESULT == 0 ))
then
	echo You won!
else
	echo You lost!
fi
```
-   Create a command line version of the game Tic Tac Toe. Make it so you can play against the computer.
```bash
#!/bin/bash
EMPTY="N"
PLAYER_1="X"
PLAYER_2="O"

FIRST_ROW=( N N N )
SECOND_ROW=( N N N )
THIRD_ROW=( N N N )

REGEX=^[1-3]$

while [ true ]
do
	echo ${FIRST_ROW[@]}
	echo ${SECOND_ROW[@]}
	echo ${THIRD_ROW[@]}
	read -p "Enter indexes for placement(from 1 to 3, ex. 1 2): " FIRST SECOND	
	if [[ ! $FIRST =~ $REGEX ]] || [[ ! $SECOND =~ $REGEX ]]
	then
		continue
	fi
	(( SECOND-- ))	
	case $FIRST in
		1)
			if [ ! ${FIRST_ROW[SECOND]} = $EMPTY ]
			then
				echo Index already selected
				continue
			fi
			FIRST_ROW[SECOND]=$PLAYER_1
			;;
		2)
			if [ ! ${SECOND_ROW[SECOND]} = $EMPTY ]
			then
				echo Index already selected
				continue
			fi
			SECOND_ROW[SECOND]=$PLAYER_1
			;;
		3)
			if [ ! ${THIRD_ROW[SECOND]} = $EMPTY ]
			then
				echo Index already selected
				continue
			fi
			THIRD_ROW[SECOND]=$PLAYER_1
			;;
	esac
	
	while [ true ]
	do
		COMPUTER_FIRST=$(( $RANDOM % 3 + 1 ))
		COMPUTER_SECOND=$(( $RANDOM % 2 ))
		case $COMPUTER_FIRST in
		1)
			if [ ! ${FIRST_ROW[COMPUTER_SECOND]} = $EMPTY ]
			then
				continue
			fi
			FIRST_ROW[COMPUTER_SECOND]=$PLAYER_2
			;;
		2)
			if [ ! ${SECOND_ROW[COMPUTER_SECOND]} = $EMPTY ]
			then
				continue
			fi
			SECOND_ROW[COMPUTER_SECOND]=$PLAYER_2
			;;
		3)
			if [ ! ${THIRD_ROW[COMPUTER_SECOND]} = $EMPTY ]
			then
				continue
			fi
			THIRD_ROW[COMPUTER_SECOND]=$PLAYER_2
			;;
		esac
		break
	done

	MERGED=( ${FIRST_ROW[@]} ${SECOND_ROW[@]} ${THIRD_ROW[@]} )
	if [[ ${MERGED[0]} != $EMPTY && ${MERGED[1]} != $EMPTY && ${MERGED[2]} != $EMPTY ]] && [[ ${MERGED[0]} == ${MERGED[1]} && ${MERGED[1]} == ${MERGED[2]} ]]
	then
		break
	elif [[ ${MERGED[3]} != $EMPTY && ${MERGED[4]} != $EMPTY && ${MERGED[5]} != $EMPTY ]] && [[ ${MERGED[3]} == ${MERGED[4]} && ${MERGED[4]} == ${MERGED[5]} ]]
	then
		break
	elif [[ ${MERGED[6]} != $EMPTY && ${MERGED[7]} != $EMPTY && ${MERGED[8]} != $EMPTY ]] && [[ ${MERGED[6]} == ${MERGED[7]} && ${MERGED[7]} == ${MERGED[8]} ]]
	then
		break
	elif [[ ${MERGED[0]} != $EMPTY && ${MERGED[4]} != $EMPTY && ${MERGED[8]} != $EMPTY ]] && [[ ${MERGED[0]} == ${MERGED[4]} && ${MERGED[4]} == ${MERGED[8]} ]]
	then
		break
	elif [[ ${MERGED[2]} != $EMPTY && ${MERGED[4]} != $EMPTY && ${MERGED[6]} != $EMPTY ]] && [[ ${MERGED[2]} == ${MERGED[4]} && ${MERGED[4]} == ${MERGED[6]} ]]
	then
		break
	elif [[ ${MERGED[0]} != $EMPTY && ${MERGED[3]} != $EMPTY && ${MERGED[6]} != $EMPTY ]] && [[ ${MERGED[0]} == ${MERGED[3]} && ${MERGED[3]} == ${MERGED[6]} ]]
	then
		break
	elif [[ ${MERGED[1]} != $EMPTY && ${MERGED[4]} != $EMPTY && ${MERGED[7]} != $EMPTY ]] && [[ ${MERGED[1]} == ${MERGED[4]} && ${MERGED[4]} == ${MERGED[7]} ]]
	then
		break
	elif [[ ${MERGED[2]} != $EMPTY && ${MERGED[5]} != $EMPTY && ${MERGED[8]} != $EMPTY ]] && [[ ${MERGED[2]} == ${MERGED[5]} && ${MERGED[5]} == ${MERGED[8]} ]]
	then
		break
	fi

done

echo ${FIRST_ROW[@]}
echo ${SECOND_ROW[@]}
echo ${THIRD_ROW[@]}
```

