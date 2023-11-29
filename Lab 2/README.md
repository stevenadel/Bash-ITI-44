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
```bash
#!/bin/bash
ls $*
```
![Screenshot from 2023-11-29 22-59-22](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/53e3fc52-ed8e-4f27-9444-fa4b5b9c6442)

### 6. Enhance the above script to support the following options individually:
#### a. –l: list in long format
#### b. –a: list all entries including the hiding files.
#### c. –d: if an argument is a directory, list only its name
#### d. –i: print inode number
#### e. –R: recursively list subdirectories
```bash
#!/bin/bash
# All this functionality already working and supported
ls $*
```
![Screenshot from 2023-11-29 23-04-27](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/e4d0b7bf-e7cc-4b5a-b3e2-dd95e2adfcbd)

## Bonus: enhance the above script to support the following Synopsis:
myls -option1 –option2\
myls –option2 –option1\
myls –option1option2\
myls –option2option1
```bash
#!/bin/bash
# All this functionality already working and supported
ls $*
```
![Screenshot from 2023-11-29 23-47-23](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/acfc2459-2613-4040-a96d-9b78c3cd8e46)

### 7. Create a script called mytest where:
#### a. It check the type of the given argument (file/directory)
#### b. It check the permissions of the given argument (read/write/execute)
```bash
#!/bin/bash
if [[ $# -ne 1 ]]
then
	echo "Usage: mytest.sh argument (must provide one argument only)"
else
	file $1
	if [[ -r $1 ]]
	then
		echo "r"
	fi

	if [[ -w $1 ]]
	then
		echo "w"
	fi

	if [[ -x $1 ]]
	then
		echo "x"
	fi
fi
```
![Screenshot from 2023-11-30 00-08-39](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/15d67bc2-776f-4071-ab38-cb1fe52d55b8)

### 8. Create a script called myinfo where:
#### a. It asks the user about his/her logname.
#### b. It print full info about files and directories in his/her home directory
#### c. Copy his/her files and directories as much as you can in /tmp directory.
#### d. Gets his current processes status.
```bash
#!/bin/bash
read -p "Enter logname: " logname

userhome=/home/$logname/
ls -la $userhome

cp -r $userhome/* /tmp 2> /dev/null

ps -U $logname
```
![Screenshot from 2023-11-30 00-35-15](https://github.com/stevenadel/Bash-ITI-44/assets/111876286/22b7036d-ab5f-43c3-944d-3902074fbd44)
