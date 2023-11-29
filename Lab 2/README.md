# Lab 2
### 1. Create a script that asks for user name then send a greeting to him.
```bash
#!/bin/bash
read -p "Enter your username: " name
echo Hello, $name. Welcome to ITI!
```
![Screenshot from 2023-11-29 15-55-35](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/227c064a-b2bd-4fd5-a3ee-e29f3f1dcfb6)

### 2. Create a script called s1 that calls another script s2 where:
#### a. In s1 there is a variable called x, it's value 5
```bash
#!/bin/bash
x=5
```
#### b. Try to print the value of x in s2 by two different ways.
```bash
#!/bin/bash
#First way to source
source s1.sh
echo $x
#Second way to source
. s1.sh
echo $x
```
![Screenshot from 2023-11-29 16-12-36](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/bb35b887-d086-49b9-b027-72014d10d249)

### 3. Create a script called mycp where:
#### a. It copies a file to another
#### b. It copies multiple files to a directory.
```bash
#!/bin/bash
cp $@
```
![Screenshot from 2023-11-29 16-12-36](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/46c96cb4-ab05-45e6-b555-0e30e3228caa)

### 4. Create a script called mycd where:
#### a. It changed directory to the user home directory, if it is called without arguments.
#### b. Otherwise, it change directory to the given directory.
```bash
source mycd.sh
```
```bash
#!/bin/bash
cd $*
```
![Screenshot from 2023-11-29 16-12-36](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/bff1ab9d-18ba-4d1f-ba0d-3025bef4763e)

### 5. Create a script called myls where:
#### a. It lists the current directory, if it is called without arguments.
#### b. Otherwise, it lists the given directory.
### 6. Enhance the above script to support the following options individually:
#### a. –l: list in long format
#### b. –a: list all entries including the hiding files.
#### c. –d: if an argument is a directory, list only its name
#### d. –i: print inode number
#### e. –R: recursively list subdirectories
