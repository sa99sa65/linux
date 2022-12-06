#!/usr/bin/bash
: '
echo "Enter name: "
read name1 name2 name3
echo "Enter names: $name1 , $name2  , $name3"
'
read -p 'username :  '  user_var
read -sp'password : '  pass_var
echo
echo "username : $user_var"
echo "username : $pass_var"


echo "enter names: "
read -a names   #which tell the script read an array
echo "Names: ${names[0]} , ${names[1]} , ${names[2]}"      

echo "Enter name: "
read
echo "Name : $REPLY" #default variable

echo $0 $1 $2 $3 '> echo $1 $2 $3'

echo $0 $1 $2 $3 '> echo $1 $2 $3'
args=("$@")
echo ${args[0]} ${args[1]} ${args[2]} #${args[3]}
echo $@
echo $#

#IS STATEMENT
count=10
if (( $count >= 0 ))
then
 echo "condition is true"
fi

word=efg
if  [ $word = "efg" ]
then
  echo "condition is true"
fi

word=a
if  [[ $word < "b" ]]
then
  echo "condition is b true"
elif  [[ $word == "a" ]]
then
  echo "contion a is true"
  else 
  echo "conditon id false"
fi

#FILE TEST OPERATOR
echo -e "Enter  the name of the file : \c"
read file_name
if [ -e $file_name ]
then
 echo "$file_name is found"
else
 echo "$file_name is not found"
fi
#for -f rgular file 
#FILE TEST OPERATOR

echo -e "Enter  the name of the file : \c"
read file_name
if [ -f $file_name ]
then
 echo "$file_name is found"
else
 echo "$file_name is not found"
fi
#-d for directry found
echo -e "Enter  the name of the file : \c"
read file_name
if [ -d $file_name ]
then
 echo "$file_name is found"
else
 echo "$file_name is not found"
fi

#two type file bloc special file and one is charator special file ,charator special file is normal file and block special file is binary file for pic or video file for block -b for charactor special -c flag
#-s for check not empty file 

echo -e "Enter  the name of the file : \c"
read file_name
if [ -s $file_name ]
then
 echo "$file_name is not empty"
else
 echo "$file_name empty"
fi

# to check read, write, execute -r,-w,-x flag

echo -e "Enter  the name of the file : \c"
read file_name
if [ -r $file_name ]
then
 echo "$file_name can read"
else
 echo "$file_name not read"
fi
#cat command input file
echo -e "Enter  the name of the file : \c"
read file_name
if [ -f $file_name ]
then
  if [ -w $file_name ]
  then
    echo "type some text. to quite press ctrl+d"
    cat >> $file_name
    else
    echo "no write permission"
  fi
 else
 echo "$file_name not exit"
fi





#terminal test
samina@Andrew58:~/Desktop$  ls
 0      calln.sh  '*.cpp'           hello.sh   smina.sh   suu
 algo   cars       expression.txt   hui.txt    srm2       uiu
samina@Andrew58:~/Desktop$ ./smina.sh
Enter  the name of the file : test
test not read
samina@Andrew58:~/Desktop$ ./smina.sh
Enter  the name of the file : test
test not exit
samina@Andrew58:~/Desktop$ touch
touch: missing file operand
Try 'touch --help' for more information.
samina@Andrew58:~/Desktop$ touch  test
samina@Andrew58:~/Desktop$ ls -al
total 44

samina@Andrew58:~/Desktop$ chmod -w test
samina@Andrew58:~/Desktop$ ls -al
total 44

samina@Andrew58:~/Desktop$ ^C
samina@Andrew58:~/Desktop$ 

samina@Andrew58:~/Desktop$ ./smina.sh
Enter  the name of the file : test
no write permission
samina@Andrew58:~/Desktop$ ./smina.sh
Enter  the name of the file : test
no write permission
samina@Andrew58:~/Desktop$ chmod +w test
samina@Andrew58:~/Desktop$ ls -al
total 48

type some text. to quite press ctrl+d





#logical and operator

age=59
if [ "$age" -gt 18 ] && [ "$age" -lt 30 ]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

age=59
if [ "$age" -gt 18 -a  "$age" -lt 30 ]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

age=59
if [[ "$age" -gt 18 &&  "$age" -lt 30 ]]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

#logical or operator

age=59
if [ "$age" -gt 18  ]||  [ "$age" -lt 30 ]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

age=59
if [ "$age" -eq 18  ]||  [ "$age" -eq 30 ]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

age=59
if [ "$age" -eq 18 -o "$age" -eq 30 ]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

age=59
if [[ "$age" -eq 18 && "$age" -eq 30 ]]
then 
  echo "valid age"
  else 
  echo "age not valid"
fi

#arithmatic operator

num1=20
num2=5

echo $(( num1 + num2 ))
echo $(( num1 - num2 ))
echo $(( num1 * num2 ))
echo $(( num1 % num2 ))
#expr onr breaket
num1=20
num2=5

echo $( expr $num1 + $num2 )
echo $( expr $num1 - $num2 )
echo $( expr $num1 \* $num2 )
echo $( expr $num1 % $num2 )

#array
arr=('samina' 'sajjad' 'ruly' 'rafa' 'abbu' 'me')
arr[11]='love'
unset arr[5]
echo "${arr[4]}"
echo "${arr[@]}"
echo "${#arr[@]}"
echo "${!arr[@]}"

arr2=tyuieop

echo "${arr2[1]}"
echo "${arr2[0]}"
echo "${arr2[@]}"
echo "${#arr2[@]}"
echo "${!arr2[@]}"

#while loop

b=1
while [ $b -le 10 ]
do
   echo "$b"
   b=$(( b+1 ))
done

b=1
while (( $b <= 10 )) 
do
   echo "$b"
   (( b++ ))
done

#while loop
#break statement

b=9
while (( $b < 10 )) 
do
   echo "$b"
   if [ $b -eq 1 ]
   then
      break
   fi

   (( b-- ))

done

#while loop
#read file content
 
while read p
do 
 echo $p
done < calln.sh
#usingcat command
cat calln.sh | while read p
do 
 echo $p
done < calln.sh

#IFS
while IFS= read -r p
do 
 echo $p
done < calln.sh

#etc file read
while IFS= read -r p
do 
 echo $p
done < /etc/magic.mime

#until loop
n=1
until [ $n -ge 10 ]
do
  echo "$n"
  (( n++ ))

done

n=1
until (( $n >= 10  )) 
do
  echo "$n"
  (( n++ ))

done

#until loop
n=10
until (( $n > 10  )) 
do
  if [ $n -lt 1 ]
  then break
  fi
  echo "$n"
  (( n-- ))

done





## sum
read x

read y
a=x
b=y
sum=`expr $a + $b`
echo "total sum is = $sum"
# sum=$(( $a + $b))
