# Lab 3
### 1. Write a script called mycase, using the case utility to checks the type of character entered by a user:
#### a. Upper Case.
#### b. Lower Case.
#### c. Number.
#### d. Nothing.
```bash
#!/bin/bash
shopt -s extglob

read -p "Please enter a character: " char

case $char in
@([A-Z]))
        echo uppercase
        ;;
@([a-z]))
        echo lowercase
        ;;
@([0-9]))
        echo number
        ;;
*)
        echo nothing
        ;;
esac
```
![Screenshot from 2023-12-05 20-24-02](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/a5707614-1759-4c7b-8467-a3aadb04003a)
### 2. Enhanced the previous script, by checking the type of string entered by a user:
#### a. Upper Cases.
#### b. Lower Cases.
#### c. Numbers.
#### d. Mix.
#### e. Nothing.
```bash
#!/bin/bash
shopt -s extglob

read -p "Please enter a string: " str

case $str in
+([A-Z]))
        echo uppercase
        ;;
+([a-z]))
        echo lowercase
        ;;
+([0-9]))
        echo number
        ;;
+([A-Za-z0-9]))
        echo mix
        ;;
*)
        echo nothing
        ;;
esac
```
![Screenshot from 2023-12-05 20-25-47](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/d2487969-9dc2-44dc-9c03-bc1bbcbb9505)
### 3. Write a script called mychmod using for utility to give execute permission to all files and directories in your home directory.
```bash
#!/bin/bash
cd /home/rhel/
for file in $(ls ~)
do
        chmod u+x $file
done
```
![Screenshot from 2023-12-05 20-29-08](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/aa7c6c8c-540b-4052-8707-ae31dff9e680)
### 4. Write a script called mybackup using for utility to create a backup of only files in your home directory.
```bash
#!/bin/bash
cd $HOME
if [[ ! -d backup ]]
then
        mkdir backup
        echo creating backup directory in home
else
        echo backup folder already exists in home
fi

for file in $(ls -r)
do
        if [[ ! $file = backup ]]
        then
                cp -r $file backup/
                echo copied $file
        fi
done
```
![Screenshot from 2023-12-06 13-16-54](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/4be61ddc-6c7c-4369-8742-1c66a3278dce)
### 5. Write a script called mymail using for utility to send a mail to all users in the system. Note: write the mail body in a file called mtemplate.
```bash
#!/bin/bash
users=`cat /etc/passwd | cut -d: -f1`
for user in $users
do
        mail -s "Lab 3 Bash" $user < mtemplate
done
```
![Screenshot from 2023-12-06 14-22-53](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/68b9432b-3676-4566-a8ad-56882a14015e)
### 6. Write a script called chkmail to check for new mails every 10 seconds. Note: mails are saved in /var/mail/username.
```bash
#!/usr/bin/bash
typeset -i lines=0
while true
do
  newlines=$(cat "/var/mail/$USER" | wc -l)
  if [[ $newlines -gt $lines ]]
  then
    echo "You've got an email!"
    lines=$newlines
  fi
  sleep 10
done
```
![Screenshot from 2023-12-07 01-56-29](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/634c538c-bdf3-49a0-95bd-276c335062b4)
### 7. What is the output of the following script
```bash
typeset –i n1
typeset –i n2
n1=1
n2=1
while test $n1 –eq $n2
do
n2=$n2+1
print $n1
if [ $n1 –gt $n2 ]
then
break
else
continue
fi
n1=$n1+1
print $n2
done
```
```bash
./script: line 2: typeset: `–i': not a valid identifier
./script: line 3: typeset: `–i': not a valid identifier
./script: line 6: test: –eq: binary operator expected
# because – is not -
# also print is not a keyword in bash
```
![Screenshot from 2023-12-07 02-22-09](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/b8dec4d5-0278-4586-8387-7b6e958ae5ff)
### 8. Create the following menu: (Using select utility then while utility)
#### a. Press 1 to ls
#### b. Press 2 to ls –a
#### c. Press 3 to exit
```bash
#!/bin/bash
select choice in 'ls' 'ls -a' 'exit'
do
        case $choice in
        'ls')
                ls
                ;;
        'ls -a')
                ls -a
                ;;
        'exit')
                break
                ;;
        esac
done
```
```bash
#!/bin/bash
while [[ ! $input = 'exit' ]]
do
        read -p "Choose ls, ls -a or exit: " input
        if [[ $input = 'ls' ]]
        then
                ls
        elif [[ $input = 'ls -a' ]]
        then
                ls -a
        fi
done
```
![Screenshot from 2023-12-07 00-42-10](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/97603345-71ad-42c7-ba87-f46c2879c959)
### 9. Write a script called myarr that ask a user how many elements he wants to enter in an array, fill the array and then print it.
```bash
#!/bin/bash
read -p "How many elements to enter: " n
for ((i=0; i<n; i++))
do
        read -p "Enter element $i: " arr[$i]
done

echo ${arr[@]}
```
![Screenshot from 2023-12-07 00-57-45](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/d47c395e-2e4e-41cc-8cab-cb226e76787a)
### 10.Write a script called myavg that calculate average of all numbers entered by a user. Note: use arrays
```bash
#!/bin/bash 
typeset -i n
typeset -i sum=0
typeset -i count=0

read -p "How many numbers to enter: " n
for ((i=1; i<=n; i++))
do
        read -p "Enter number $i: " arr[$i]
        sum+=${arr[$i]}
        ((count++))
done

avg=$(($sum/$count))
echo avgerage is $avg
```
![Screenshot from 2023-12-07 01-18-06](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/9435e30e-772f-4bc9-80da-3581885c062e)
### 11.Write a function called mysq that calculate square of its argument.
```bash
#!/bin/bash
function sq {
        return $(( $1 * $1 ))
}

sq $1
echo $?
```
![Screenshot from 2023-12-07 01-26-38](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/1f7f489f-9216-43b9-80cf-739ed178dd2a)
