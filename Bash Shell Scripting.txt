bash shell scripting

ls #list of files for vim


#!/bin/bash

# Comment

echo "Hello World!"

chmod 755 file_name       
#this changes permission of the file: owner, group, others; 
#7 - read write execute, 6 - read and write, 5 - read and execute, 4 - read only , 3 - write and execute 2 - write only , 1 - execute only, 0 - nothing 

vim options:
:w #save
:wq #save and quit
:q! #discard and quit
:set number #line numbers
:syntax on #syntax colouring
:set tabstop=4 #how many tab spaces
:set autoindent

declaring:

declare -r num1=5

num2=4

num3=$((num1+num2))
num4=$((num1-num2))
num5=$((num1*num2))
num6=$((num1/num2))

echo "5 + 4 = $num3"
echo "5 - 4 = $num4"
echo "5 * 4 = $num5"
echo "5 / 4 = $num6"


rand=5
let rand+=1
echo ""
echo "5 bigger by 1 is $rand"
echo ""
echo "rand++ = $(( rand++ ))" 
#print, then increment - shows 6, value is now 7

echo "++rand = $(( ++rand ))" 
#increment, then print - shows 8, value is now 8

echo "rand-- = $(( rand-- ))" 
#print, then decrement - shows 8, value is now 7

echo "--rand = $(( --rand ))" 
#decrement, then print - shows 6, value is now 6



#to use numbers other than ints just call Python
echo "sum of 1.2 and 3.4 is:"
num7=1.2
num8=3.4
num9=$(python -c "print $num7+$num8")
echo $num9


#text spanning many lines
cat<< END
This text
prints
on
many lines
END


#out of insert mode: gg to get to start, dG to delete all

#functions
getDate()
{
	date
	return
}

getDate
#prints current date



#local variables:
name="Dude"
demLocal()
{
  local name="Mate"
  return
}
demLocal
echo "$name"
#prints Dude as it is a blobal var, Mate is only within that functions



#making a function in which you input stuff in
getSum()
{
  local num3=$1
  local num4=$2
  local sum=$((num3+num4))

  echo $sum
}
num1=5
num2=6
sum=$(getSum num1 num2)
echo "The sum is $sum"
#--------------------------

#user input
read -p "What is your name? " name
echo "Hello $name"
#read input, stores in variable called name



#if statements

read -p "How old are ye matey? " age

if [ $age -ge 16 ]   #ge greater or equal
then
  echo "You can drive"
elif [ $age -eq 15 ]   #eq equal
then
  echo "You can drive next year"
else
  echo "You can't drive"
fi
#fi ends an if statement

# eq - equal
# ne - not equal
# le - less or equal
# lt - less than
# ge - greater or equal
# gt - greater than



#nicer if statements
read -p "Input a number:  " num

if ((num == 10)); then
  echo "Your number equals 10"
fi

if ((num > 10)); then
  echo "It is greater than 10"
else
  echo "It is less or equal to ten"
fi

if (( ((num % 2)) == 0)); then
  echo "It is even"
fi
#----------------

#logic operators
if (( ((num > 0)) && ((num < 11)) )); then
  echo "$num is between 1 and 10"
else
  echo "$num is not between 1 and 10"
fi
#---------------


