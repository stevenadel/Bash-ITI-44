# Bash Lab 1
### Using sed utility
### 1- Display the lines that contain the word “lp” in /etc/passwd file.
sed -n '/lp/p' /etc/passwd

![1](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/affc4a5f-3ebd-4815-9cbd-6b501724862b)

### 2- Display /etc/passwd file except the third line.
sed '3d' /etc/passwd

![2](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/75235534-1839-4aea-b624-8ffc5b07a19d)

### 3- Display /etc/passwd file except the last line.
sed ‘$d’ myfile

![3](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/60975b62-bef4-4e96-a291-3e2c34ec984a)

### 4- Display /etc/passwd file except the lines that contain the word “lp”.
sed '/lp/d' /etc/passwd

![4](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/f29f1ced-7109-40a1-aed4-c0245dd260e2)

### 5- Substitute all the words that contain “lp” with “mylp” in /etc/passwd file.
sed 's/lp/mylp/g' /etc/passwd

![5](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/ce9d2e10-a02f-486d-8570-2a2e12f6fb4b)

---------------------------------------------------------------------------------------

### Using awk utility
### 1- Print full name (comment) of all users in the system.
awk –F: ‘{print $5}’ /etc/passwd

![Screenshot from 2023-11-28 14-06-05](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/f790597e-ab93-4d37-a185-a3792ff7672b)

### 2- Print login, full name (comment) and home directory of all users.( Print each line preceded by a line number)
awk -F: '{ print NR,$1,$5,$6 }' /etc/passwd

![Screenshot from 2023-11-28 14-11-58](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/05710340-dca2-428a-968e-a4e4135226da)

### 3- Print login, uid and full name (comment) of those uid is greater than 500
awk -F: '{ if ($3 > 500) print $1,$3,$6 }' /etc/passwd

![Screenshot from 2023-11-28 14-21-45](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/4d743f7a-a445-4594-a458-03970f1ae54f)

### 4- Print login, uid and full name (comment) of those uid is exactly 500
awk -F: '{ if ($3 == 500) print $1,$3,$6 }' /etc/passwd

![Screenshot from 2023-11-28 14-22-52](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/5eadbb44-3896-489e-a417-02f3593c186a)

### 5- Print line from 5 to 15 from /etc/passwd
awk -F: '{ if (NR>=5&&NR<=15) print $0 }' /etc/passwd

![Screenshot from 2023-11-28 14-28-34](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/00cf2f5f-1857-41e6-b03a-9c1a81966e1d)

### 6- Change lp to mylp
awk -F: '{ for (i=1; i<=NF; i++) { if ($i~"lp") $i="mylp" } print $0 }' /etc/passwd

![Screenshot from 2023-11-28 15-04-28](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/dc75ad94-868d-4a97-bd98-7d401c86ad03)

### 7- Print all information about greatest uid.
awk -F: 'BEGIN{ max=1; } { if (max<$3) { max=$3;  line=$0 }} END { print line }' /etc/passwd

![Screenshot from 2023-11-28 15-20-56](https://github.com/stevenadel/Red-Hat-Sysadmin-ITI-44/assets/111876286/48f2e9f3-820b-42f0-a8e5-e79ecf530cb8)

### 8- Get the sum of all accounts id’s.


