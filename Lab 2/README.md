# Lab 2
### 1. Create a script that asks for user name then send a greeting to him.
```bash
#!/bin/bash
read -p "Enter your username: " name
echo Hello, $name. Welcome to ITI!
```
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
### 3. Create a script called mycp where:
#### a. It copies a file to another

#### b. It copies multiple files to a directory.
```bash

```
### 4. Create a script called mycd where:
#### a. It changed directory to the user home directory, if it is called without arguments.
#### b. Otherwise, it change directory to the given directory.
### 5. Create a script called myls where:
#### a. It lists the current directory, if it is called without arguments.
#### b. Otherwise, it lists the given directory.
### 6. Enhance the above script to support the following options individually:
#### a. –l: list in long format
#### b. –a: list all entries including the hiding files.
#### c. –d: if an argument is a directory, list only its name
#### d. –i: print inode number
#### e. –R: recursively list subdirectories

