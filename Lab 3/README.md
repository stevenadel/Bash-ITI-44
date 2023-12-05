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

```
### 5. Write a script called mymail using for utility to send a mail to all users in the system. Note: write the mail body in a file called mtemplate.
### 6. Write a script called chkmail to check for new mails every 10 seconds. Note: mails are saved in /var/mail/username.
### 7. What is the output of the following script
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
### 8. Create the following menu: (Using select utility then while utility)
#### a. Press 1 to ls
#### b. Press 2 to ls –a
#### c. Press 3 to exit
### 9. Write a script called myarr that ask a user how many elements he wants to enter in an array, fill the array and then print it.
### 10.Write a script called myavg that calculate average of all numbers entered by a user. Note: use arrays
### 11.Write a function called mysq that calculate square if its argument.

## Screenshots
