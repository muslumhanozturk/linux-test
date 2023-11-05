# Hands-on Linux-01 : Managing Files in Linux

Purpose of the this hands-on training is to teach the students how to manage files in Linux.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- Explain files in linux system.

- Create and edit files.

- Work with file contents

- Search files.

## Outline

- Part 1 - Working with File Contents

- Part 2 - Searching Files

## Part 1 - Working with File Contents

- Create a folder and name it linux-lessons.

```bash
mkdir linux-lessons
cd linux-lessons
```

- Create a `text` file named `clarusway.txt`.

```txt
Welcome to the linux lessons
line 2
line 3
line 4
line 5
line 6
line 7
line 8
line 9
line 10
line 11
line 12
line 13
line 14
Line 15
```

- Show the first 10 lines of clarusway.txt.

```bash
head clarusway.txt
```

- Show the first 5 lines of clarusway.txt.

```bash
head -5 clarusway.txt
```

- Show the last 10 lines of clarusway.txt.

```bash
tail clarusway.txt
```

- Show the last 5 lines of clarusway.txt.

```bash
tail -5 clarusway.txt
```

- Display the clarusway.txt file on the screen.

```bash
cat clarusway.txt
```

- Create three files with echo command and name them file1 file2 file3.

```bash
echo "this is file1" > file1
echo "this is file2" > file2
echo "this is file3" > file3
```

- Display the file1, file2 and file3 files on the screen.

```bash
cat file1 file2 file3
```

- Concatenate file1, file2 and file3 to `all.txt` file.

```bash
cat file1 file2 file3 > all.txt
```

- Create a file with `cat` command.

```bash
cat > summer.txt 
Today is cold.
Today is rainy
```

- After the last line, type and hold the Control (Ctrl) key and press d.

- View the clarusway.txt file with the `more` command.

```bash
more clarusway.txt
```

- View the clarusway.txt file with the `less` command.

```bash
less clarusway.txt
```

- The main difference between more and less is that less command is faster because it does not load the entire file at once and allows navigation though file using page up/down keys. 

- Display clarusway.txt file in reverse.

```bash
tac clarusway.txt
```

- Create reverse-clarusway.txt in reverse of clarusway.txt.

```bash
tac clarusway.txt > reverse-clarusway.txt
```

## Part 2 - Searching Files

### `find` command

- Find all the files whose name is clarusway.txt in a current working directory.

```bash
find . -name clarusway.txt
```

- Find all the files under /home directory with name clarusway.txt.

```bash
find /home -name clarusway.txt
```

- Find all the files whose name is clarusway.txt and contains both capital and small letters in /home directory.

```bash
find /home -iname clarusway.txt
```

- Find all directories whose name is linux-lessons in /home directory.

```bash
find /home -type d -name linux-lessons
```

- Find all txt files in the working directory.

```bash
find . -type f -name "*.txt"
```

- Find all empty files in the working directory.

```bash
find . -type f -empty
```

- Find all empty files in the /home directory.

```bash
find /home -type f -empty
```

- To find all 100MB files under home directory. 

```bash
find /home -size 100M
```

- Find all the files which are greater than 50MB and less than 100MB under home directory. Note that the `+` and `-` prefixes signify greater than and less than.

```bash
find /home -size +50M -size -100M
```

- Find all the files which are modified 10 days ago in /home directory.

```bash
find /home -mtime 10
```

- Find all the files which are modified in the last 10 days in /home directory.

```bash
find /home -mtime -10
```

- Find all the files which are modified in more than 10 days in /home directory.

```bash
find /home -mtime +10
```

- Find all the files which are modified more than 10 minutes back and less than 30 minutes in current folder.

```bash
find . -mmin +10 -mmin -30
```

### `grep` command

Grep is a Linux / Unix command-line tool used to search for a string of characters in a specified file. 

- Create a file and name it `grep.txt`.

```txt
grep  searches  for  PATTERNS  in  each  FILE.
PATTERNS  is  one  or more patterns separated by newline characters, and grep prints each line that matches a pattern.  
Typically PATTERNS should be  quoted  when grep is used in a shell command.
```

- Create another file and name it `linux.txt`

```txt
Linux is a family of open-source Unix-like operating systems based on the Linux kernel.
It is an operating system kernel first released on September 17, 1991, by Linus Torvalds.Linux is typically packaged in a Linux distribution.
Distributions include the Linux kernel and supporting system software and libraries.
Popular Linux distributions include Debian, Fedora, and Ubuntu. 
Commercial distributions include Red Hat Enterprise Linux and SUSE Linux Enterprise Server.
```

- Search `linux.txt` file for `kernel`. 

```bash
grep "kernel" linux.txt
```

- Search all files for `is`.

```bash
grep  "is" *
```

- Search `linux.txt` file for `linux`.

```bash
grep "linux" linux.txt
```

- It didn't find linux expression. Because grep is case sensitive. Now try with the following command.

```bash
grep -i "linux" linux.txt
```

- Search `linux.txt` file for `ker`.

```bash
grep -i "ker" linux.txt
```

- Now search `linux.txt` file for `ker` with the following command.

```bash
grep -w "ker" linux.txt
```

- It didn't find `ker`. Grep allows you to find and print the results for whole words only with `-w` flag. Let's try with the following command.

```bash
grep -w "kernel" linux.txt
```

- We can display the lines that are not matched with the specified search sting pattern using the -v option. 

```bash
grep -v "kernel" linux.txt
```

- The `^` regular expression pattern specifies the start of a line. This can be used in grep to match the lines which start with the given string or pattern. 

```bash
grep "^li" clarusway.txt
```

- The $ regular expression pattern specifies the end of a line. This can be used in grep to match the lines which end with the given string or pattern.

```bash
grep "kernel.$" linux.txt
```

- Sometimes we need more content in search results to decide what is most relevant. For this, we can use the following operators to add the desired lines before, after a match, or both:

    - Use -A and a number of lines to display after a match.
    
    ```bash
    grep -A3 "line 5" clarusway.txt # this command prints three lines after the match.
    ```

    - Use -B and a number of lines to display before a match.
    
    ```bash
    grep -B2 "line 5" clarusway.txt # this command prints two lines before the match.
    ```

    - Use -C and a number of lines to display before and after the match.
    
    ```bash
    grep -C4 "line 5" clarusway.txt # this command prints four lines before and after the match.
    ```

- We can also use `grep` command with | (pipe).

```bash
man pwd | grep "print"
```

```bash
man find | grep -A5 "size"
```

```bash
history | grep "find"
```# Hands-on Linux-02 : Linux Environment Variables

Purpose of the this hands-on training is to teach the students how to use environment variables.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- explain environment variables.

- understand Quoting with Variables.

## Outline

- Part 1 - Common Environment Variables & Accessing Variable

- Part 2 - Path Variable

- Part 3 - Quoting with Variables

- Part 4 - Sudo Command

## Part 1 - Common Environment/Shell Variables & Accessing Variable
​
- Difference between "env" and "printenv" commands.
​
```bash
env
printenv
printenv HOME
echo $HOME
env HOME
```
​
- Understanding the shell variable.
​
```bash
CLARUS=way
env
set
set | grep CLARUS
echo $CLARUS
```
​
- Understanding the environment variable. Use export command.
​
```bash
export WAY=clarus
env
```
​
- Difference between shell and environment variables. Create a user, name it "user1", switch to user1, check the environment and shell variables.
​
```bash
export WAY=clarus
sudo su
useradd user1
passwd user1 # give user1 any password.
exit
su user1
env | grep WAY
set | grep CLARUS
```
​
- Change the environment variable value.
​
```bash
export WAY=linux
env
export WAY=script
env
```
​
- Remove the environment variable with unset command.
​
```bash
export WAY=clarusway
env | grep WAY
unset WAY
env | grep WAY
```
​
## Part 2 - Path Variable
​
- PATH variable.
​
```bash
printenv PATH
cd /bin
ls ca*    # see the cat command.
```
​
- Add a path to PATH variable for running a script.
​
```bash
cd
mkdir test && cd test
nano test.sh
# copy and paste the code-echo "hello world"- in test.sh
chmod +x test.sh
./test.sh
cd    # change directory to ec2-user's home directory
./test.sh    # it doesnt work. 
./test/test.sh
printenv PATH
cd test
pwd
export PATH=$PATH:/home/ec2-user/test
printenv PATH
cd
test.sh
cd /
test.sh
```
​
- Using the environment variable in the script.
​
```bash
cd test
export CLARUS=env.var
WAY=shell.var
cd test
nano test1.sh
# copy and paste the code-echo "normally we should see env. variable $CLARUS but probably we can't see the shell variable $WAY "
chmod +x test1.sh
./test1.sh
```
​
## Part 3 - Quoting with Variables.
​
- Double Quotes.
​
```bash
MYVAR=my value
echo $MYVAR
MYVAR="my value"
echo $MYVAR
MYNAME=james
MYVAR="my name is $MYNAME"
echo $MYVAR
MYNAME="james"
MYVAR="hello $MYNAME"
echo $MYVAR
MYVAR="hello \$MYNAME"
echo $MYVAR
```
​
- Single Quotes.
​
```bash
echo '$SHELL'
echo 'My\$SHELL'
```
​
## Part 4 - Sudo Command.
​
- Sudo Command.
​
```bash
yum update
sudo yum update
cd /
mkdir testfile
sudo su
sudo -s
sudo su -
```# Hands-on Linux-03 : Managing Users and Groups

Purpose of the this hands-on training is to teach the students how to manage users and groups.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- explain users and groups in linux.

- manage users and groups.

## Outline

- Part 1 - Basic User Commands

- Part 2 - User Management

- Part 3 - User Passwords

- Part 4 - Group Management

## Part 1 - Basic User Commands
​
- whoami.
​
```bash
whoami
sudo su
pwd
whoami
su ec2-user
sudo su -
pwd
```
​
- who.
​
```bash
exit
who
who # open a new shell and retry who command to see the users who logged in.
```
​
- w.
​
```bash
w
who
```
​
- id.
​
```bash
id
id root
sudo su
useradd user1
id user1
```
​
- su.
​
```bash
su ec2-user
su user1
sudo su user1
pwd
exit
sudo su - user1
pwd
```
​
- passwd.
​
```bash
exit
sudo su
useradd user2
passwd user2    # give a password to user2
su - user2
passwd
exit
su user2
```
​
## Part 2 - User management
​
- /etc/passwd.
​
```bash
exit
cat /etc/passwd
tail -3 /etc/passwd
```
​
- useradd.
​
```bash
sudo useradd user3
cd /home
ls
cd /etc
ls login*
cat login.defs
sudo nano login.defs    # change the CREATE_HOME variable's value to "no"
sudo useradd user4
cd /home && ls
cat /etc/passwd
sudo useradd -m user5    # force to system to create a home directory for user with -m option.
cd /home && ls
sudo useradd -m -d /home/user6home user6    # change the user's home directory name with -d option.
ls
sudo useradd -m -c "this guy is developer" user7    # give a descrpition to user with -c option.
cat /etc/passwd
cat /etc/passwd | grep user7
```
​
- userdel.
​
```bash
cat /etc/passwd
sudo userdel user5
cat /etc/passwd
cd /home && ls
sudo userdel -r user1    # delete user and its home directory with -r option.
cd /home && ls
```
​
- usermod.
​
```bash
cat /etc/passwd
sudo usermod -c "this guy will be an aws solution architect" user7
cat /etc/passwd
sudo usermod --help
sudo usermod -l Superuser user2    # change the name of the user2 with -l option.
cat /etc/passwd
```
​
## Part 3 - User Passwords
​
- passwd-etc/shadow-etc/login.defs.
​
```bash
  sudo su
  useradd user8
  passwd user8
  cd /etc
  cat shadow
  cat login.defs
```
​
## Part 4 - Group Management
​
- groups.
​
```bash
groups
sudo groupadd linux
sudo groupadd aws
sudo groupadd python
cat /etc/group
groups
sudo usermod -a -G linux ec2-user    # append ec2-user in linux group.
cat /etc/group
groups
sudo usermod -G aws ec2-user    # this command deletes all groups that ec2-user in except default group of ec2-user and add ec2-user to aws group.
cat /etc/group
sudo groupmod -n my-linux linux    # change the name of the linux group.
cat /etc/group
groups
cat /etc/group
sudo groupdel python
cat /etc/group
sudo gpasswd -a user7 aws    # add a user to a group.
cat /etc/group
sudo gpasswd -d user7 aws    # delete a user to a group.
cat /etc/group
```# Hands-on Linux-04 : Using Package Managers in Linux
​
Purpose of the this hands-on training is to teach the students how to use package managers in Linux.
​
## Learning Outcomes
​
At the end of the this hands-on training, students will be able to;
​
- Explain what is package management.
​
- Work with most common package management tools.
​
- Install, upgrade, configure and remove software packages using package management tools.
​
## Outline
​
- Part 1 - Using package managers ('yum' and 'apt') 
​
## Part 1 - Using Package Managers ('yum' and 'apt')
​
- Update Amazon Linux Instance.
​
```bash
sudo yum update
```
- Update Ubuntu's package list. This command updates the local repo database but do not install any package.
​
```bash
sudo apt update
```
- Upgrade the packages. This command installs the listed available packages.

```bash
sudo apt upgrade
```

- Check if 'git' is installed on Amazon Linux instance.
​
```bash
git --version
```
- Check if 'git' is installed on Ubuntu instance.
​
```bash
git --version
```
- Install git on Amazon Linux instance.
​
```bash
sudo yum install git
```
- Uninstall git on Amazon Linux instance.
​
```bash
sudo yum remove git
```
- Install git on Amazon Linux instance without any interruption.
​
```bash
sudo yum install git -y
```
- Uninstall git on Amazon Linux instance without any interruption.
​
```bash
sudo yum remove git -y
```
- Check the version of git installed on Amazon Linux instance.(There should be no info, because it's just removed a minute ago)
​
```bash
git --version
```
- Explain why there is still version info.
- Install git on Amazon Linux instance without any interruption.
​
```bash
sudo yum install git -y
```
- Uninstall git with dependencies on Amazon Linux instance without any interruption.
​
```bash
sudo yum autoremove git -y
```
- Check the version of git installed on Amazon Linux instance.(There should ne no info, because it's just removed a minute ago)
​
```bash
git --version
```
- Uninstall git on Ubuntu instance.
​
```bash
sudo apt remove git
```
- Check the version of git installed on Ubuntu instance.(There should be no info, because it's just removed a minute ago)
​
```bash
git --version
```
- Install git on Ubuntu instance without any interruption.
​
```bash
sudo apt install git -y
```
- Uninstall git with dependencies on Ubuntu instance without any interruption.
​
```bash
sudo apt autoremove git -y
```
- Check the info for the git package installed on Amazon Linux instance.
​
```bash
sudo yum info git
```
- Check the info for the git package installed on Ubuntu instance.
​
```bash
sudo apt info git
```
- List all available packages for Amazon Linux instance.
​
```bash
sudo yum list
```
- List all available packages for Ubuntu instance.
​
```bash
sudo apt list
```
- List all available git packages for Amazon Linux instance.
​
```bash
sudo yum list git
```
- List all available git packages for Ubuntu instance.
​
```bash
sudo apt list git
```
- List all installed packages on Amazon Linux instance.
​
```bash
sudo yum list installed
```
- List all installed packages on Ubuntu instance.
​
```bash
sudo apt list --installed
```
- List all available versions of git packages on Amazon Linux instance.
​
```bash
sudo yum --showduplicates list git
```
- Check the version of git installed on Amazon Linux instance.
​
```bash
git --version
```
- Uninstall git with dependencies on Amazon Linux instance without any interruption.
​
```bash
sudo yum autoremove git -y
```
- Install a previous version of git on Amazon Linux instance.
​
```bash
sudo yum --showduplicates list git
sudo yum install git-2.14.5-1.amzn2 -y
```
- Check the version of git installed on Amazon Linux instance.
​
```bash
git --version
```
- List all available versions of git packages on Amazon Linux instance.
​
```bash
sudo yum --showduplicates list git
``` 
- Check the available version of git with info command.
​
```bash
sudo yum list git
```
- Update git and check the version.
​
```bash
sudo yum update git -y
git --version
```
# Hands-on Linux-05 : Filters and Control Operators
​
Purpose of the this hands-on training is to teach the students how to use filters and control operators in Linux.
​
## Learning Outcomes
​
At the end of the this hands-on training, students will be able to;
​
- Use filter commands.
​
- Pipe commands.
​
- Use Control operators.
​
## Outline
​
- Part 1 - Using Filters
​
- Part 2 - Using Control Operators
​
## Part 1 - Using Filters
​
**cat**

- concatenate files and print on the standard output
​
- Create a folder and name it filters.
​
```bash
mkdir filters
cd filters
```
- Create a `text` file named `days.txt`.
​
```bash
vim days.txt
```
​
```bash
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```
- Display the content of days.txt.
```bash
cat days.txt
```
- Show what cat command does when used in a pipe.
​
```bash
cat days.txt | cat | cat | cat | cat
```
- Create a `text` file named `count.txt`.
​
```bash
nano count.txt
```
```text
one
two
three
four
five
six
seven
eight
nine
ten
eleven 
```
- Display the content of count.txt.

```bash
cat count.txt
```

**tee**

- Read from standard input and write to standard output and files
​
- Write the content of the count.txt file in reverse order to another file named temp.txt and display the content of temp.txt in reverse order.

```bash
tac count.txt | tee temp.txt | tac
```
- Check whether the temp.txt file created and display the content.
​
```bash
ls
cat temp.txt
```

**grep**
​
- Print lines that match patterns. The most common use of grep is to filter lines of text containing (or not containing) a certain string.

- Create a `text` file named `tennis.txt`.
​
```bash
cat > tennis.txt
​
Amelie Mauresmo, Fra
Justine Henin, BEL
Serena Williams, USA
Venus Williams, USA
```
>**press ctrl+d for EOF**
​
- Display the content of tennis.txt.

```bash
cat tennis.txt
```

- Display only the lines of tennis.txt that includes 'Williams'.
​
```bash
cat tennis.txt | grep Williams
```

- Display only the lines of tennis.txt that includes 'us'.
​
```bash
cat tennis.txt | grep us
```

- Display the owners column (3rd column) of all the files in current directory.
​
**cut**

- The cut filter can select columns from files, depending on a delimiter or a count of bytes
​
```bash
ls -l | cut -d' ' -f3
```

- Display the content of /etc/passwd directory.
​
```bash
cat /etc/passwd
```

- Display only the usernames.
​
```bash
cut -d: -f1 /etc/passwd
```

**tr**
​
- The command 'tr' stands for 'translate’. It is used to translate, like from lowercase to uppercase and vice versa or new lines into spaces.

- Create a `text` file named `clarusway.txt`.
​
```bash
cat << EOF > clarusway.txt
Clarusway:Road to reinvent yourself.
EOF
```

- Display the content of clarusway.txt.
​
```bash
cat clarusway.txt
```

- In the content of clarusway.txt, replace or translate aer letters with 'QAZ'.
​
```bash
cat clarusway.txt | tr aer QAZ
```
​
- Write the content of count.txt on the same line.
​
```bash
cat count.txt | tr '\n' ' '
```
​
- Delete all the vowels in the content of clarusway.txt.
​
```bash
cat clarusway.txt | tr -d aeiou
```
​
- Write the whole content of clarusway.txt in capital letters.
​
```bash
cat clarusway.txt | tr [a-z] [A-Z]
```

**wc**
​
- Print line, word, and charecters for each file.

- Count the lines, words and letters of the content of count.txt.
​
```bash

wc count.txt
```

- Find how many users are there in the computer.

```bash
wc -l /etc/passwd
```

**sort**
​
- The sort filter will default to an alphabetical sort. The sort filter will default to an alphabetical sort.

- Create a `text` file named `marks.txt`.
​
```bash
cat << EOF > marks.txt
aeron-9
albert-9
james-9
john-10
oliver-7
tom-7
victor-10
walter-8
EOF
```

- Display the content of marks.txt.
​
```bash
cat marks.txt
```

- Sort the content of marks.txt.
​
```bash
sort marks.txt
```

- Sort the content of marks.txt in reverse order.
​
```bash
sort -r marks.txt
```

**uniq**
​
- report or omit repeated lines. With the help of uniq command you can form a sorted list in which every word will occur only once.

- Create a `text` file named `trainees.txt`.
​
```bash
cat << EOF > trainees.txt
john
james
aeron
oliver
walter
albert
james
john
travis
mike
aeron
thomas
daniel
john
aeron
oliver
mike
john
EOF
```

- Display the content of trainees.txt.
​
```bash
cat trainees.txt
```

- Display only the unique names in the content of trainees.txt.
​
******before using uniq command, the file must be sorted******
​
```bash
sort trainees.txt | uniq
```

**comm**

- Compare two sorted files line by line. By default, `comm` will always display three columns. 
First column indicates non-matching items of first file, second column indicates non-matching items 
of second file, and third column indicates matching items of both the files. 

- Both the files has to be in sorted order for 'comm' command to be executed.
​
- Create a `text` file named `file1.txt`.
​
```bash
cat << EOF > file1.txt
Aeron
Bill
James
John
Oliver
Walter
EOF
```

- Create another `text` file named `file2.txt`.
​
```bash
cat << EOF > file2.txt
Guile
James
John
Raymond
EOF
```

- Compare file1.txt and file2.txt.
​
******before using comm command, files must be sorted******
​
```bash
comm file1.txt file2.txt
```

- EXERCISE:
​
  - Create a file named `countries.csv`.
​
```bash
cat << EOF > countries.csv
Country,Capital,Continent
USA,Washington,North America
France,Paris,Europe
Canada,Ottawa,North America
Germany,Berlin,Europe
EOF
```
  - Cut only 'Continent' column | Remove header | Sort the output | List distinct values | Save it to 'continent.txt' and display on the screen.
​
```bash
********************************
```
## Part 2 - Using Control Operators
​
>**;**
​
- More than one command can be used in a single line with `;`.

- Write two seperate cat command on the same line using ;.
​
```bash
cat days.txt ; cat count.txt 
```

```bash
echo Hello ; echo World! 
```

>**&**

- When a line ends with an ampersand &, the shell will not wait for the command to finish. You will get your shell prompt back, and the command is executed in background. You will get a message when this command has finished executing in background.
​
- Run sleep 10 command and show that the kernel is busy until the process of this command ends.
​
```bash
sleep  10
```

- Run sleep 20 command and let this command work behind while you're running other commands.
​
```bash
sleep  20 &
ls -l
cat count.txt
cat days.txt
```

>**$?**
​
- This control operator is used to check the status of last executed command. If status shows '0' then command was successfully executed and if shows '1' then command was a failure.

- Run ls command and show that it is executed successfully.
​
```bash
ls
echo $?
```

- Run lss command and show that it failed.
​
```bash
lss
echo $?
```

>**&&**

- The command shell interprets the && as the logical AND. When using this command, the second command will be executed only when the first one has been successfully executed.
​
- Display days.txt and if it runs properly display count.txt.
​
```bash
cat days.txt && cat count.txt
```

- Display days.text and if it runs properly display count.txt.
​
```bash
cat days.text && cat count.txt
```

>**||**

- The command shell interprets the (||) as the logical `OR`. This is opposite of logical `AND`. Means second command will execute only when first command will be a failure.
​
- Display days.txt or write 'clarusway' on the screen, then write 'one'.
​
```bash
cat days.txt || echo clarusway ; echo one
```

- Write 'first' or write 'second' on the screen, then write 'third'.
​
```bash
echo first || echo second ; echo third
zecho first || echo second ; echo third
```

>**&& and ||**

- We can use this logical AND and logical OR to write an if-then-else structure on the command line. This example uses echo to display whether the rm command was successful.
​
- Make a copy of file1.txt and named it file11.txt.
​
```bash
cp file1.txt file11.txt
```
- Delete file11.txt and write a message if it is deleted properly.
​
```bash
rm file11.txt && echo 'it worked' || echo 'it failed'
```
- Run the last command again.
​
```bash
rm file11.txt && echo 'it worked' || 'it failed'
```

>**#**

- Everything written after a pound sign (#) is ignored by the shell. This is useful to write a shell comment but has no influence on the command execution or shell expansion.​

- Run the echo command and add a comment line.
​
```bash
echo '# is the comment sign' # echo command displays the string comes after it.
echo # is the comment sign
echo \# is the comment sign
```

>** \ **

- Lines ending in a backslash are continued on the next line. The shell does not interpret the newline character and will wait on shell expansion and execution of the command line until a newline without backslash is encountered.

- Escaping characters are used to enable the use of control characters in the shell expansion but without interpreting it by the shell.
​
- Run a single command on multipe lines.
​
```bash
echo this command is written \
not only on a single line \
but also on multiple lines.
```
- Write the following sentence on the screen: The special characters are *, \, ", #, $, '.
​
```bash
echo The special characters are \*, \\, \", \#, \$, \'.
```

- EXERCISE:
​
  1.a. Search for “clarusway.doc” in the current directory
    b. If it exists display its content
    c. If it does not exist print message “Too early!”
  2.Create a file named “clarusway.doc” that contains “Congratulations”
  3.Repeat Step 1
​
```bash
********************************
```# Hands-on Linux-10 : sed & awk command and crontab

Purpose of the this hands-on training is to teach the students how to use sed & awk command and crontab.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- use sed & awk command and crontab.

## Outline

- Part 1 - sed command

- Part 2 - awk command

- Part 3 - crontab

## Part 1 - sed command

- Sed is a stream editor. A stream editor is used to perform a lot of function on a file like searching, find and replace, insertion or deletion.

- Create a folder and name it `sed-awk-command`.

```bash
mkdir sed-awk-command && cd sed-awk-command
```

- Create a file named `sed.txt`. 

```txt
Linux is an OS. Linux is life. Linux is a concept.
I like linux. You like linux. Everyone likes linux.
Linux is free. Linux is good. Linux is hope.
```

### Replacing or substituting string

The following sed command replaces the word “linux” with “ubuntu” in the file.

```bash
sed 's/linux/ubuntu/' sed.txt
```
- `s` specifies the substitution operation. 
- The `/` are delimiters. 
- The `linux` is the search pattern and the `ubuntu` is the replacement string.

**Output:**
```bash
Linux is an OS. Linux is life. Linux is a concept.
I like ubuntu. You like linux. Everyone likes linux.
Linux is free. Linux is good. Linux is hope.
```
> Pay attention that, by default, the sed command replaces the `first occurrence` of the pattern in each line.


### 

### Replacing the any occurrence of a pattern in a line 
Use the /1, /2 etc flags to replace the first, second occurrence of a pattern in a line. The following command replaces the third occurrence of the word “linux” with “ubuntu” in a line.

```bash
sed 's/linux/ubuntu/3' sed.txt
```

**Output:**
```bash
Linux is an OS. Linux is life. Linux is a concept.
I like linux. You like linux. Everyone likes ubuntu.
Linux is free. Linux is good. Linux is hope.
```

### Replacing a string by ignoring case distinctions.

By, default sed command do not ignore case distinctions. For this `i` pattern can be used.

```bash
sed 's/linux/ubuntu/i' sed.txt
```

**Output:**
```bash
ubuntu is an OS. Linux is life. Linux is a concept.
I like ubuntu. You like linux. Everyone likes linux.
ubuntu is free. Linux is good. Linux is hope.
```

#### Replacing all the occurrence of the pattern in a line 

`g flag` (global replacement) defines the sed command to replace all the occurrences of the string in the line.

```bash
sed 's/linux/ubuntu/g' sed.txt
```

**Output:**
```bash
Linux is an OS. Linux is life. Linux is a concept.
I like ubuntu. You like ubuntu. Everyone likes ubuntu.
Linux is free. Linux is good. Linux is hope.
```

- We can do the same by ignoring case distinctions. Use the combination of `/i` and `/g`.

```bash
sed 's/linux/ubuntu/ig' sed.txt
```

**Output:**
```bash
ubuntu is an OS. ubuntu is life. ubuntu is a concept.
I like ubuntu. You like ubuntu. Everyone likes ubuntu.
ubuntu is free. ubuntu is good. ubuntu is hope.
```

#### Replacing from any occurrence to all occurrences in a line

We can replace all the patterns from the any occurrence of a pattern in a line by using the combination of /1, /2 etc and /g. The sed command below replaces the second, third, and so on “linux” word with “ubuntu” word in a line.

```bash
sed 's/linux/ubuntu/2ig' sed.txt
```

**Output:**
```bash
Linux is an OS. ubuntu is life. ubuntu is a concept.
I like linux. You like ubuntu. Everyone likes ubuntu.
Linux is free. ubuntu is good. ubuntu is hope.
```

#### Replacing string on a specific line number

We can limit the sed command to replace the string on a specific line number. The following command only replaces the second line.

```bash
sed '2 s/linux/ubuntu/ig' sed.txt
```

**Output:**
```bash
Linux is an OS. Linux is life. Linux is a concept.
I like ubuntu. You like ubuntu. Everyone likes ubuntu.
Linux is free. Linux is good. Linux is hope.
```

## Part 2 - awk command

- Awk is a text pattern scanning and processing language, created by Aho, Weinberger & Kernighan (hence
the name). It searches one or more files to see if they contain lines that matches with the specified patterns and then performs the associated actions. 

- While the sed program works well with character-based processing, the awk program works well with delimited field processing.

- Create a file named `awk.txt`. 

```txt
This is line 1
This is line 2
This is line 3
This is line 4
This is line 5
```

### Syntax of awk command

> awk options 'selection _criteria {action }' file

- By default Awk prints every line of data from the specified file.

```bash
awk '{print}' awk.txt
```

**Output:**
```bash
This is line 1
This is line 2
This is line 3
This is line 4
This is line 5
```

### Print the lines which matches with the given pattern

```bash
awk '/This/ {print}' awk.txt
```

**Output:**
```bash
This is line 1
This is line 2
This is line 3
This is line 4
This is line 5
```

### Splitting a Line Into Fields

By default, the awk command splits the record delimited by a whitespace character.  Awk assigns some variables for each data field as below:

$0 for the whole line.
$1 for the first field.
$2 for the second field.
$n for the nth field.

```bash
awk '{print $2}' awk.txt
```

**Output:**
```bash
is
is
is
is
is
```

We can display more field. The example below only display two field.

```bash
awk '{print $2,$4}' awk.txt
```

**Output:**
```bash
is 1
is 2
is 3
is 4
is 5
```

- We can change delimiter by using –F option. First, update the awk.txt as below.

```txt
This is part 1 of line 1 : This is part 2 of line 1
This is part 1 of line 2 : This is part 2 of line 2
This is part 1 of line 3 : This is part 2 of line 3
This is part 1 of line 4 : This is part 2 of line 4
This is part 1 of line 5 : This is part 2 of line 5
```

- Let's separate the fields by `:`.

```bash
awk -F: '{print $2}' awk.txt
```

**Output:**
```bash
 This is part 2 of line 1
 This is part 2 of line 2
 This is part 2 of line 3
 This is part 2 of line 4
 This is part 2 of line 5
```

- We can use awk command as filter. 

```bash
ls -l | awk '{print $9}'
```

**Output:**
```bash
awk.txt
sed.txt
```

- We can find any string in any specific column. 

```bash
awk '{ if($7 == "3") print $0;}' awk.txt
```

**Output:**
```bash
This is part 1 of line 3 : This is part 2 of line 3
```

## Part 3 - crontab

- Crontab, stands for `cron table`, which is a list of commands scheduled to run at regular time intervals on the system. 

- Installing and configuring cronjob for 2023 AMI

```bash
sudo yum install cronie -y
sudo systemctl enable crond.service
sudo systemctl start crond.service
```

- Verify if the cronie service works or not

```bash
sudo systemctl status crond.service
```

- If we need to schedule any task on Linux, we should basically edit the crontab file. We can do that using the below command.

```bash
crontab -e              # edit the crontab file
crontab -l              # list current cron tasks
crontab -u username -e  # edit other users's crontab file
```

- Editing the crontab file is not complex, but we should first learn how to set a date and time using 5 * on that file. There are six fields that we use on every cron task line. Those are explained in detail in the below picture.

- Let’s see few examples;

```bash
* * * * * <shell command>   # execute cron job every minute
0 1 * * * <shell command>   # execute cron job every day at 1 a.m.
* * * 1 * <shell command>   # execute every minute in January
* * * * 6 <shell command>   # execute every minute on every saturday
0 1/15 * jan,jun mon,fri <command> # execute at every 1 a.m. and 3
                                     p.m. every monday and friday on
                                     january and june
```

- We can also use some regular expressions to define the date part.

```bash
* = Any/All values           # e.g. *
- = Range of values          # e.g. 1-5 
, = Multiple/List of values  # e.g. 1,2,3
/ = Step values              # e.g. 1/3
```

- Finally let’s create some crontab tasks. Create a cron task writes the system date information every day at 1 p.m. to the date.log file.

```bash
crontab -e
0 13 * * * date >> /home/ec2-user/date.log
```

- Create a cron task updates and upgrades our server every Sunday at 3 a.m.

```bash
0 3 * * sun sudo yum update -y
```

-  List the cron tasks.

```bash
crontab -l
```# Hands-on Linux-06 : Shell Scripting Basics

Purpose of the this hands-on training is to teach the students how to script in shell.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- explain shell scripting basics.

- explain shell variables.

- do simple arithmetic.

## Outline

- Part 1 - Shell Scripting Basics

- Part 2 - Shell Variables

- Part 3 - Simple Arithmetic

## Part 1 - Shell Scripting Basics

- Create a folder and name it shell-scripting.

```bash
mkdir shell-scripting && cd shell-scripting
```

- Create a `script` file named `basic.sh`. Note all the scripts would have the .sh extension.

```bash
#!/bin/bash
echo "Hello World"
```

- Before we add anything else to our script, we need to alert the system that a shell script is being started.
This is done specifying `#!/bin/bash` on the first line, meaning that the script should always be run with bash, rather than another shell. `#!` is called a `shebang` because the `#` symbol is called a hash, and the `!` symbol is called a bang.

- After to save the above content, we need to make the script executable.

```bash
chmod +x basic.sh
```

- Then we can execute the `basic.sh`. To execute basic.sh, it is required to add `./` beginning of the `basic.sh`. `./` means we're calling something in the current working directory. We have to specify the path for executables if they're outside our $PATH variable.

```bash
./basic.sh
```

- We can add the other shell commands to our script.

```bash
#!/bin/bash
echo "hello"
date
pwd
ls
```

- And execute again.

```bash
./basic.sh
```

### Shell Comments

- Bash ignores everything written on the line after the hash mark `(#)`. The only exception to this rule is the first line of the script that starts with the `#!` characters. 

- Comments can be added at the beginning on the line or inline with other code. Let's update `basic.sh`.

```bash
#!/bin/bash
echo "hello"
# date
pwd # This is an inline comment
# ls
```

- Unlike most of the programming languages, Bash doesn’t support multiline comments. But, we can use `here document` for this. In Linux, here document (also commonly referred to as `heredoc`) refers to a special block of code that contains multi-line strings that will be redirected to a command. If the `HereDoc block` is not redirected to a command, it can serve as a multiline comments placeholder.

### HEREDOC syntax

- A heredoc consists of the **<<** `(redirection operator)`, followed by a delimiter token. After the delimiter token, lines of string can be defined to form the content. Finally, the delimiter token is placed at the end to serve as the termination. The delimiter token can be any value as long as it is unique enough that it won’t appear within the content.

- Let's see how to use HereDoc.

```bash
cat << EOF
Welcome to the Linux Lessons.
This lesson is about the shell scripting
EOF
```

- Update the `basic.sh`.

```bash
#!/bin/bash
echo "hello"
# date
pwd # This is an inline comment
# ls

cat << EOF
Welcome to the Linux Lessons.
This lesson is about the shell scripting
EOF

<< multiline-comment
pwd
ls
Everything inside the
HereDoc body is
a multiline comment
multiline-comment
```

- Execute the basic.sh.

```bash
./basic.sh
```

## Part 2 - Shell Variables

- A variable is pointer to the actual data. The shell enables us to create, assign, and delete variables.

- The name of a variable can contain only letters (a to z or A to Z), numbers ( 0 to 9) or the underscore character (_) and beginning with a letter or underscore character.

- The following examples are valid variable names.

```bash
KEY=value
_VAR=5
clarus_way=test
```

> Note that there is no space on either side of the equals ( = ) sign. 

- The following examples are invalid.

```bash
3_KEY=value
-VAR=5
clarus-way=test
KEY_1?=value1
```

- The reason we cannot use other characters such as `?`, `*`, or `-` is that these characters have a special meaning for the shell.

- Create a new file and name it `variable.sh`.

```bash
#!/bin/bash
NAME=Joe
echo $NAME
```

- Make the script executable and then execute it.

```bash
chmod +x variable.sh && ./variable.sh
```

### Command Substitution

- Command substitution empowers us to take the output of a command or program (which would usually be written on the screen) and save it as the value of a variable. To do this we put it inside brackets, followed by a $ symbol.

```bash
content=$(ls)
echo $content
```

- or we can use `(backtick)

```bash
content=`ls`
echo $content
```

- let's see that in a script. Create a file and name it `command-substitution.sh`.

```bash
#!/bin/bash
working_directory=$(pwd)
echo "Welcome, your working directory is $working_directory."
```

- Make the script executable and execute it. 

```bash
chmod +x command-substitution.sh
./command-substitution.sh
```

- We can also get same result without using variables. Update the `command-substitution.sh` file as below.

```bash
#!/bin/bash
echo "Welcome, your working directory is $(pwd)."
echo "Today is `date`"
echo "You are `whoami`"
```

- And execute it. 

```bash
./command-substitution.sh
```

### Console input

- The Bash `read` command is a powerful built-in utility used take user input. 

- Update the `variable.sh` file.

```bash
#!/bin/bash
echo "Enter your name: "
read NAME
echo "Welcome $NAME"
```

- When writing interactive bash scripts, we can use the read command to get the user input. To specify a prompt string, use the -p option. The prompt is printed before the read is executed and doesn’t include a newline.

```bash
read -p "Enter your name: " NAME
echo "Welcome $NAME"
```

- When entering sensitive information we do not want to display input coming. For this we can use `read -s`

```bash
read -p "Enter your name: " NAME
echo "Welcome $NAME"

read -s -p "Enter your password: " PASSWORD
echo -e "\nYour password is $PASSWORD"
```

### Command Line Arguments

- Command-line arguments are given after the name of the program in command-line shell of Operating Systems. The command-line arguments $1, $2, $3, ...$9 are positional parameters, with $0 pointing to the actual command, program, shell script, or function and $1, $2, $3, ...$9 as the arguments to the command.

- Create a new file and name it `argument.sh`.

```bash
#!/bin/bash
echo "File Name is $0"
echo "First Parameter is $1"
echo "Second Parameter is $2"
echo "Third Parameter is $3"
echo "All the Parameters are $@"
echo "Total Number of Parameters : $#"
echo "$RANDOM is a random number"
echo "The current line number is $LINENO"
```

- Make the script executable. 

```bash
chmod +x argument.sh
```

- Execute it with following command.

```bash
./argument.sh Joe Matt Timothy James Guile
```

### Arrays

- In our programs, we usually need to group several values to render as a single value. In shell, arrays can hold multiple values at the same time.

#### Defining arrays

- Following is the simplest method of creating an array variable. 

```bash
DISTROS[0]="ubuntu"
DISTROS[1]="fedora"
DISTROS[2]="debian"
DISTROS[3]="centos"
DISTROS[4]="alpine"
```

- We can also use following method.

```bash
devops_tools=("docker" "kubernetes" "ansible" "terraform" "jenkins")
```

#### Working with arrays

- We can access a value in an array by using the following method.

```bash
echo ${DISTROS[0]}
echo ${DISTROS[1]}
```

- We can access all elements by putting `@` instead of number.

```bash
echo ${DISTROS[@]}
```

- With the following method, we can learn number of elements.

```bash
echo ${#DISTROS[@]}
```

## Part 3 - Simple Arithmetic

- There are many ways to evaluate arithmetic expression in Bash scripting

### expr

- `expr` command print  the value of expression to standard output. Let's see this.

```bash
expr 3 + 5
expr 6 - 2
expr 7 \* 3
expr 9 / 3
expr 7 % 2
```

- Using `expr` command, we must have spaces between the items of the expression and must not put quotes around the expression. If we do that, the expression will not be evaluated but printed instead. See the difference.

```bash
expr "3 + 5"
expr 3-2
```

- Let's create a simple calculator. Create a file and name it `calculator.sh`.

- Make the script executable. 

```bash
chmod +x calculator.sh
```

```bash
#!/bin/bash
read -p "Input first number: " first_number
read -p "Input second number: " second_number

echo "SUM="`expr $first_number + $second_number`
echo "SUB="`expr $first_number - $second_number`
echo "MUL="`expr $first_number \* $second_number`
echo "DIV="`expr $first_number / $second_number`
```

> How can we do with Command Line Arguments?

### let

- `let` is a builtin function of Bash that helps us to do simple arithmetic. It is similar to `expr` except instead of printing the answer it saves the result to a variable. Unlike expr we need to enclose the expression in quotes. 

```bash
let "sum = 3 + 5"
echo $sum
```

- Note that if we don't put quotes around the expression then it must be written with no spaces.

```bash
let sub=8-4
echo $sub
```

- We can also increase or decrease the variable by 1 with `let` function. Let's see this.

```bash
x=5
let x++
echo $x

y=3
let y--
echo $y
```

- Create a file and name it `let-calculator.sh`.

```bash
#!/bin/bash
read -p "Input first number: " first_number
read -p "Input second number: " second_number

let "sum = $first_number + $second_number"
let "sub = $first_number - $second_number"
let "mul = $first_number * $second_number"
let "div = $first_number / $second_number"
echo "SUM=$sum"
echo "SUB=$sub"
echo "MUL=$mul"
echo "DIV=$div"

let first_number++
let second_number--
echo "The increment of first number is $first_number"
echo "The decrement of second number is $second_number"
```

- Make the script executable and execute it. 

```bash
chmod +x let-calculator.sh
./let-calculator.sh
```

#### Difference between `num++` and `++num`, or `num--` and `--num`

- Create a file and name it number.sh.

```bash
number=10
let new_number=number++   # This firstly assigns the number then increases.
echo "Number = $number"
echo "New number = $new_number"

number=10
let new_number=--number   # This firstly decreases the number then assigns.
echo "Number = $number"
echo "New number = $new_number"
```

- Make the script executable and execute it. 

```bash
chmod +x number.sh
./number.sh
```

### Double Parentheses

- We can also evaluate arithmetic expression with double parentheses. We have learned that we could take the output of a command and save it as the value of a variable. We can use this method to do basic arithmetic.

```bash
sum=$((3 + 5))
echo $sum
```

- As we can see below, it works just the same if we take spacing out.

```bash
sum=$((3+5))
echo $sum
```

- Create a file and name it `parantheses-calculator.sh`.

```bash
#!/bin/bash
read -p "Input first number: " first_number
read -p "Input second number: " second_number

sum=$(($first_number + $second_number)) 
sub=$(($first_number - $second_number)) 
mul=$(($first_number * $second_number)) 
div=$(($first_number / $second_number)) 


echo "SUM=$sum"
echo "SUB=$sub"
echo "MUL=$mul"
echo "DIV=$div"

(( first_number++ ))
(( second_number-- ))

echo "The increment of first number is $first_number"
echo "The decrement of second number is $second_number"
```

- Make the script executable and execute it. 

```bash
chmod +x parantheses-calculator.sh
./parantheses-calculator.sh
```# Hands-on Linux-07 : Shell Scripting/Conditional Statements

Purpose of the this hands-on training is to teach the students how to use conditional statements in shell.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- explain conditional statements in shell.

- use if statements in shell scripting

- use case statements in shell scripting

## Outline

- Part 1 - If Statements

- Part 2 - If Else Statements

- Part 3 - If Elif Else Statements

- Part 4 - Nested If Statements

- Part 5 - Boolean Operations

- Part 6- Case Statements

## Part 1 - If Statements

- Unix Shell supports conditional statements that are used to perform different actions on the basis of different conditions.

- A simple if statement essentially states, if a particular test is true, then perform a specified set of actions. If it's not true, don't take those acts.

- Create a folder and name it `conditional-statements`.

```bash
mkdir conditional-statements && cd conditional-statements
```

- Create a `script` file named `if-statement.sh`. 

```bash
#!/bin/bash
read -p "Input a number: " number

if [[ $number -gt 50 ]]
then
  echo "The number is big."
fi
```

- Make the script executable and execute it.

```bash
chmod +x if-statement.sh
./if-statement.sh
```

- We can use `Relational Operators`, `String Operators` or `File Test Operators` inside the square brackets ( [ ] ) in the if statement above. 

### Relational Operators

- Bourne Shell supports the relational operators below that are specific to numeric values. These operators do not work for string values.

| Operator | Description |
| -------- | ----------- |
| -eq   | equal                  |
| -ne   | not equal              |
| -gt   | greater than           |
| -lt   | less than              |
| -ge   | greater than or equal  |
| -le   | less than or equal     |

### String Operators

- The string operators below are supported by Bourne Shell.

| Operator | Description |
| -------- | ----------- |
| =    | equal            |
| !=   | not equal        |
| -z   | Empty string     |
| -n   | Not empty string |

- Let's see this. Create a file and name it `string-operators.sh`

```bash
#!/bin/bash

if [[ "a" = "a" ]]
then
  echo "They are same"
fi

if [[ "a" != "b" ]]
then
  echo "They are not same"
fi

if [[ -z "" ]]
then
  echo "It is empty"
fi

if [[ -n "text" ]]
then
  echo "It is not empty"
fi
```

- Notice that there are spaces between the opening bracket `[` and the parameters "text" = "text", and then between the parameters and the closing bracket `]`. That is precisely because the brackets here act as a command, and you are separating the command from its parameters.

- Make the script executable and execute it.

```bash
chmod +x string-operators.sh
./string-operators.sh
```

### File Test Operators

- There are a few operators that can be used to test various properties associated with a Linux file.

| Operator | Description |
| -------- | ----------- |
| -d file   | directory  |
| -e file   | exists     |
| -f file   | ordinary file     |
| -r file   | readable          |
| -s file   | size is > 0 bytes |
| -w file   | writable          |
| -x FILE   | executable        |

- Let's try this. Create files below and configure them.

```bash
mkdir folder
touch file 
chmod 400 file
```

Create a file and name it `file-operators.sh`

```bash
#!/bin/bash

if [[ -d folder ]]
then
  echo "folder is a directory"
fi

if [[ -f file ]]
then
  echo "file is an ordinary file"
fi

if [[ -r file ]]
then
  echo "file is a readable file"
fi

if [[ -w file ]]
then
  echo "file is a writable file"
fi

if [[ -s file ]]
then
  echo "file is > 0 bytes"
fi

if [[ -x $0 ]]
then
  echo "$0 is an executable file "
fi
```

- Make the script executable and execute it.

```bash
chmod +x file-operators.sh
./file-operators.sh
```

## Part 2 - If Else Statements

- Sometimes we want to execute a block of code if a statement is true, and another block of code if it is false.

- Create a `script` file named `ifelse-statement.sh`. 

```bash
#!/bin/bash
read -p "Input a number: " number

if [[ $number -ge 10 ]]
then
  echo "The number is bigger than or equal to 10."
else 
  echo "The number is smaller than 10"
fi
```

- Make the script executable and execute it.

```bash
chmod +x ifelse-statement.sh
./ifelse-statement.sh
```

> - Create a script. Ask user to enter `a file name` to create.
> - If there is a file with the same name, print the message "The file already exists."
> - If not, create the file and print the message "The file is created."

## Part 3 - If Elif Else Statements

- The elif statement is used when it requires to specify several conditions in our program.

- Create a `script` file named `elif-statement.sh`. 

```bash
#!/bin/bash
read -p "Input a number: " number

if [[ $number -eq 10 ]]
then
  echo "The number is equal to 10."
elif [[ $number -gt 10 ]]
then
  echo "The number is bigger than 10"
else 
  echo "The number is smaller than 10"
fi
```

- Make the script executable and execute it.

```bash
chmod +x elif-statement.sh
./elif-statement.sh
```

## Part 4 - Nested If Statements

- If statements can be nested. Let's see the nested structure on the followig example.

- Create a `script` file named `nested-if-statement.sh`. 

```bash
#!/bin/bash

read -p "Input a number: " number

if [[ $number -gt 10 ]]
then
  echo "Number is bigger than 10"

  if (( $number % 2 == 1 ))
  then
    echo "And is an odd number."
  else
    echo "And is an even number"
  fi
else 
  echo "It is not bigger than 10"
fi
```

- Make the script executable and execute it.

```bash
chmod +x nested-if-statement.sh
./nested-if-statement.sh
```

## Part 5 - Boolean Operations

- The Boolean operators below are supported by the Bourne Shell.

| Operator | Description |
| -------- | ----------- |
| !        | negation    |
| &&       | and         |
| ||       | or          |

- `!`  inverts a true condition into false and vice versa.

- `&&` is logical AND. If both the operands are true, then the condition becomes true otherwise false.

- `||`	is logical OR. If one of the operands is true, then the condition becomes true.	

- Create a `script` file named `boolean.sh`. 

```bash
#!/bin/bash

read -p "Input your name: " name
read -sp "Input your password: " password

if [[ $name = $(whoami) ]] && [[ $password = Aa1234 ]]
then
  echo -e "\nWelcome $(whoami)"
else
  echo -e "\nIt is wrong account"
fi
```

- Make the script executable and execute it.

```bash
chmod +x boolean.sh
./boolean.sh
```

## Part 6- Case Statements

- To execute a multiway branch, we can use several if-elif statements but that would soon become complicated. Bash case statements are similar to if-else statements but are easier and simpler. It helps to match one variable against several values.

- Create a `script` file named `case-statement.sh`. 

```bash
#!/bin/bash

read -p "Input first number: " first_number
read -p "Input second number: " second_number
read -p "Select an math operation
1 - addition
2 - subtraction
3 - multiplication
4 - division
" operation

case $operation in
  "1") 
     echo "result= $(( $first_number + $second_number))"
  ;;
  "2")
     echo "result= $(( $first_number - $second_number))"
  ;;
  "3")
     echo "result= $(( $first_number * $second_number))" 
     ;;
  "4")
     echo "result= $(( $first_number / $second_number))"
  ;;
  *)
     echo "Wrong choice..." 
  ;;
esac
```

- Make the script executable and execute it.

```bash
chmod +x case-statement.sh
./case-statement.sh
```# Hands-on Linux-08 : Shell Scripting/Loops

Purpose of the this hands-on training is to teach the students how to use loops in shell.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- explain loops in shell.

- use while loops in shell scripting

- use until loops in shell scripting

- use for loops in shell scripting

- use continue and break statements in shell scripting

- use select loops in shell scripting

## Outline

- Part 1 - While loops

- Part 2 - Until loops

- Part 3 - For loops

- Part 4 - Continue and Break Statements

- Part 5 - Select loops

## Part 1 - While loops

- When writing programs in shell, in some cases it is not enough to execute our block of code only once. The loops are used to repeat (iterate) the execution of a block of code.

- while loops have a boolean logic, similar to if statements. As long as the result of the condition returns True, the code block under while loop runs. When the condition returns to False, the loop execution is terminated and the program control moves further to the next operation.

- Create a folder and name it `loops`.

```bash
mkdir loops && cd loops
```

- Let's display numbers from 1 to ten with `while loop`. Create a `script` file named `while-loop.sh`. 

```bash
#!/bin/bash

number=1

while [[ $number -le 10  ]]
do
  echo $number
  ((number++))
done
echo "Now, number is $number"
```

- Make the script executable and execute it.

```bash
chmod +x while-loop.sh
./while-loop.sh
```

## Part 2 - Until loops

- The until loop is identical to the while loop, except that it will execute the commands within it until the test becomes true.

- Create a `script` file named `until-loop.sh`. 

```bash
#!/bin/bash

number=1

until [[ $number -ge 10  ]]
do
  echo $number
  ((number++))
done
echo "Now, number is $number"
```

- Note that, this time we write `-ge` instead of `-le`. So in first sitiuation, condition is false. It will execute the code until the condition is true. 

- Make the script executable and execute it.

```bash
chmod +x until-loop.sh
./until-loop.sh
```

## Part 3 - For loops

- Sometimes we want to iterate a block of code for each of the items in a given list. For this we use `for loop`. 

- Here is a simple example. Create a `script` file named `for-loop.sh`. 

```bash
#!/bin/bash

echo "Numbers:"

for number in 0 1 2 3 4 5 6 7 8 9
do
   echo $number
done

echo "Names:"

for name in Joe David Matt John Timothy
do
   echo $name
done

echo "Files in current folder:"

for file in `pwd`/*
do
   echo $file
done
```

- Make the script executable and execute it.

```bash
chmod +x for-loop.sh
./for-loop.sh
```

### Using arrays with the for loop

- Create a `script` file named `for-array.sh`. 

```bash
#!/bin/bash

devops_tools=("docker" "kubernetes" "ansible" "terraform" "jenkins")

for tool in ${devops_tools[@]}
do
   echo $tool
done
```

- Make the script executable and execute it.

```bash
chmod +x for-array.sh
./for-array.sh
```

## Part 4 - Continue and Break Statements
 
 - A loop will continue forever unless the necessary condition is not met. A loop that runs endlessly without terminating can run for an infinite number of times. For this reason, these loops are named infinite loops.

- Create a `script` file named `infinite-loop.sh`. 

```bash
#!/bin/bash

number=1

until [[ $number -lt 1  ]]
do
  echo $number
  ((number++))
done
echo "Now, number is $number"
```

- Make the script executable and execute it.

```bash
chmod +x infinite-loop.sh
./infinite-loop.sh
```

- Push the `ctrl + C` and terminate the process.

### Break Statement

- As we see above the infinite loop run forever. The break statement is used to terminate the execution of the entire loop.

- Let's modify the `infinite-loop.sh`.

```bash
#!/bin/bash

number=1

until [[ $number -lt 1  ]]
do
  echo $number
  ((number++))
  if [[ $number -eq 100 ]]
  then
    break
  fi
done
```

- Execute the script.

```bash
./infinite-loop.sh
```

### Continue Statement

- The Continue statement is similar to the Break command, except it causes the current iteration of the loop to exit, instead of the whole loop.

- Let's modify the `infinite-loop.sh`. This time we do not display 10 and its multiples (10, 20 ..)

```bash
#!/bin/bash

number=1

until [[ $number -lt 1  ]]
do
  ((number++))
  
  tens=$(($number % 10))
  
  if [[ $tens -eq 0 ]]
  then
    continue
  fi

  echo $number
    
  if [[ $number -gt 100 ]]
  then
    break
  fi
done
```

- Execute the script.

```bash
./infinite-loop.sh
```

## Part 5 - Select loops

- The Select Loop generates a numbered menu from which users can select options. It's helpful when you need to ask the user to select one or more items from a list of options.

- Create a `script` file named `select-loop.sh`. 

```bash
#!/bin/bash

read -p "Input first number: " first_number
read -p "Input second number: " second_number

PS3="Select the operation: "

select operation in addition subtraction multiplication division exit
do
  case $operation in
    addition) 
      echo "result= $(( $first_number + $second_number))"
    ;;
    subtraction)
       echo "result= $(( $first_number - $second_number))"
    ;;
    multiplication)
       echo "result= $(( $first_number * $second_number))" 
       ;;
    division)
       echo "result= $(( $first_number / $second_number))"
    ;;
    exit)
       break
    ;;   
    *)
       echo "Wrong choice..." 
    ;;
  esac
done
```

- Note that we can change the `system variable PS3` to modify the prompt that is displayed.

- Make the script executable and execute it.

```bash
chmod +x select-loop.sh
./select-loop.sh
```
# Hands-on Linux-09 : Shell Scripting/Functions

Purpose of the this hands-on training is to teach the students how to use functions in shell.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- explain and use functions in shell.

## Outline

- Part 1 - Creating Functions

- Part 2 - Passing Arguments to Functions

- Part 3 - Returning Values from Functions

- Part 4 - Nested Functions

- Part 5 - Variables Scope

## Part 1 - Creating Functions

- A Bash function is a piece of code that only runs when it is called. Functions enable you to reuse code. We can call the functions numerous times.

- Create a folder and name it `functions`.

```bash
mkdir functions && cd functions
```

- It is pretty easy to declare and call a function. Create a `script` file named `functions.sh`. 

```bash
#!/bin/bash

Welcome () {
    echo "Welcome to Linux Lessons"
}

Welcome
```

- Make the script executable and execute it.

```bash
chmod +x functions.sh
./functions.sh
```

## Part 2 - Passing Arguments to Functions

- We can pass any number of arguments to the bash function in a similar way to passing command line arguments to a script. We simply supply them right after the function’s name, separated by a space. These parameters would be represented by $1, $2 and so on, corresponding to the position of the parameter after the function’s name.

- Let's update the `functions.sh` script to see this.

```bash
#!/bin/bash

Welcome () {
    echo "Welcome to Linux Lessons $1 $2 $3"
}

Welcome Joe Matt Timothy
```

- And execute it.

```bash
./functions.sh
```

## Part 3 - Returning Values from Functions

- Functions in other programming languages return a value when called. But, Bash functions don’t return a value when called. But we can define a return status similar to exit status of a command.

- When any shell command terminates, it returns an exit code, which indicates `0` for success and non-zero decimal number in the `1 - 255` range for failure. The special variable `$?` returns the exit status of the last executed command. Let's see this.

```bash
pwd
echo $?  #0
pwt  # It is wrong command
echo $?  #127
```

- When a bash function completes, its return value is the status of the last statement executed in the function. We can speciy return status by using the `return` keyword. We can think the `return` keyword as exit status of function. 

- Add `return 3` line to `Welcome function`.

```bash
#!/bin/bash

Welcome () {
    echo "Welcome to Linux Lessons $1 $2 $3"
    return 3
    }

Welcome Joe Matt Timothy
echo $?
```

- And execute it.

```bash
./functions.sh
```

## Part 4 - Nested Functions

- One of the useful features of functions is that they can call themselves and other functions. 

- Create a `script` file named `nested-functions.sh`.

```bash
#!/bin/bash

function_one () {
   echo "This is from the first function"
   function_two
}

function_two () {
   echo "This is from the second function"
}

function_one
```

- Make the script executable and execute it.

```bash
chmod +x nested-functions.sh
./nested-functions.sh
```

## Part 5 - Variables Scope

- Global variables are variables that can be accessed from anywhere in the script regardless of the scope. In Bash, by default all variables are defined as global, even if declared inside the function.
Local variables can be declared within the function body with the local keyword and can be used only inside that function. 

- Create a `script` file named `variables-scope.sh`.

```bash
#!/bin/bash

var1='global 1'
var2='global 2'

var_scope () {
  local var1='function 1'
  var2='function 2'
  echo -e "Inside function:\nvar1: $var1\nvar2: $var2"
}

echo -e "Before calling function:\nvar1: $var1\nvar2: $var2"

var_scope

echo -e "After calling function:\nvar1: $var1\nvar2: $var2"
```

- Make the script executable and execute it.

```bash
chmod +x variables-scope.sh
./variables-scope.sh
```
