# Explication of every task

### 0. Hello World
#### Write a script that prints “Hello, World”, followed by a new line to the standard output.
Script:
```ruby
#!/bin/bash

echo Hello, World
```
#### The 'echo' command is used to display a message.

### 1. Confused smiley
#### Write a script that displays a confused smiley "(Ôo)'.
Script:
```ruby
#!/bin/bash
echo "\"(Ôo)'"
```
The string have double quotes (") so to ignore it we use a backslash (\) to avoid misinterpretation by the shell.

### 2. Let's display a file
#### Display the content of the /etc/passwd file.
Script:
```ruby
#!/bin/bash
cat /etc/passwd
```
The 'cat' command is for looking inside of an file. passwd is the file that we are looking.

### 3. What about 2?
#### Display the content of /etc/passwd and /etc/hosts
Script:
```ruby
#!/bin/bash
cat /etc/passwd /etc/hosts
```
We can use cat to look in differents files. In this case passwd and hosts

### 4. Last lines of a file
#### Display the last 10 lines of /etc/passwd
Script:
```ruby
#!/bin/bash
tail -n 10 /etc/passwd
```
The 'tail' command is used to display the last lines of the file. we use the '-n' option to specify the number of lines to display. '10' are the number of lines.

### 5. I'd prefer the first ones actually
#### Display the first 10 lines of /etc/passwd
Script
```ruby
#!/bin/bash
head -n 10 /etc/passwd
```
The 'head' command is for display the first lines on the file. the rest is like the task 4.

### 6. Line #2
#### Write a script that displays the third line of the file iacta.
#### The file iacta will be in the working directory.
#### You’re not allowed to use 'sed'.
Script
```ruby
#!/bin/bash
head -3 iacta | tail -1
```
For this activity first we have to get the first 3 lines of the file. We use the '|' to send the output of the head to the next command 'tail' and we use this output to get last line of that result that will be the third line of the file. 

### 7. It is a good file that cuts iron without making a noise
#### Write a shell script that creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.

Script:
```ruby
#!/bin/bash
echo "Best School" >> "\\*\\\'\"Best School\"\'\\\*$\\?\*\*\*\*\*:)"
```
We use the command 'echo' to print the text 'Best School' and the redirection operator (>>). in this task we have to varius special characters like backslashees to get our file name. The  backslash (\) prevents the next character from being interpreted as a special character. so if we need one '\' in the script we have to write '\\'. if we need two then '\\\'.

### 8. Save current state of directory
#### Write a script that writes into the file ls_cwd_content the result of the command ls -la. If the file ls_cwd_content already exists, it should be overwritten. If the file ls_cwd_content does not exist, create it.
Script:
```ruby
#!/bin/bash
ls -la >> ls_cwd_content
```
The 'ls' command is for listing the contents of a directory. The '-l' options tells to display the content in a long format which includes details such as permissions, owner, group, size, and date modified. The '-a' options thells to show hidden files and directories.

'>>'  is the redirection operator that get the output of the command and save it on a file (with this operator if the file exist the output is saved at the end of the file).

### 9. Duplicate last line
#### Write a script that duplicates the last line of the file iacta
#### The file iacta will be in the working directory.
Script:
```ruby
#!/bin/bash
tail -1 iacta >> iacta
```
We use the command 'tail' to get the last line and the operaton '>>' to save at the end of the file

### 10. No more javascript
#### Write a script that deletes all the regular files (not the directories) with a .js extension that are present in the current directory and all its subfolders.

Script:
```ruby
#!/bin/bash
find . -type f -name '*.js' -delete
```
Using the command 'find' we search the files with a '.js' extension in the current directory and the sub-directories. The '-type f' option is for limit the search to only files. The '-name' is used to specify the pattern of the files to be searched. And we use the '-delete' for deleting the files that match the criteria.

### 11. Don't just count your directories, make your directories count
#### Write a script that counts the number of directories and sub-directories in the current directory.
#### The current and parent directories should not be taken into account
#### Hidden directories should be counted
Script:
```ruby
#!/bin/bash
find . -mindepth 1 -type d | wc -l
```
We use the 'find' command to search directories in the current directory. The '-mindepth 1' is used to exclude the current directory from the search, so that only sub-directories are counted. '-type d' option is for limit the search for only directories. the output of the command find is passed to the command 'wc' (word count) with the '-l' option, which counts the number of lines and return the result.

### 12. What’s new
#### Create a script that displays the 10 newest files in the current directory.
#### Requirements:
#### One file per line
#### Sorted from the newest to the oldest
Script:
```ruby
#!/bin/bash
ls -t . | head
```
The '-t' option is used for sorting by modification time and we use a pipe to pass the output to the head and this shows the first 10 items.

### 13. Being unique is better than being perfect
#### Create a script that takes a list of words as input and prints only words that appear exactly once.
#### Input format: One line, one word
#### Output format: One line, one word
#### Words should be sorted
Script:
```ruby
#!/bin/bash
sort | uniq -u
```
'sort' sorts the data lbl (line by line)
'uniq -u' remove the duplicate lines. only displaying the unique lines.

### 14. It must be in that file
#### Display lines containing the pattern “root” from the file /etc/passwd
Script:
```ruby
#!/bin/bash
grep 'root' /etc/passwd
```
The 'grep' command is used to search specified patterns, in this case we look for the text 'root' in the /etc/passwd file.

### 15. Count that word
#### Display the number of lines that contain the pattern “bin” in the file /etc/passwd
Script:
```ruby
#!/bin/bash
grep -c 'bin' /etc/passwd
```
Using the command 'grep' with the option '-c' we count the number of line that match the pattern.

### 16. What's next?
#### Display lines containing the pattern “root” and 3 lines after them in the file /etc/passwd.
Script:
```ruby
#!/bin/bash
grep -A 3 'root' /etc/passwd
```
The option '-A' of 'grep' is used to specify that grep should also show the three lines following each match.

### 17. I hate bins
#### Display all the lines in the file /etc/passwd that do not contain the pattern “bin”.
Script:
```ruby
#!/bin/bash
grep -v 'bin' /etc/passwd
```
With the option '-v' we tell 'grep' to invert the match (which means it will return all lines in the file that do not match the pattern).

### 18. Letters only please
#### Display all lines of the file /etc/ssh/sshd_config starting with a letter.
#### include capital letters as well
Script:
```ruby
#!/bin/bash
grep ^[[:alpha:]] /etc/ssh/sshd_config
```
The '[[:alpha:]]' means any character. the caret (^) symbol matches the start of a line, so the pattern ^[[:alpha:]] will match any line that starts with an alphabetic character.

### 19. A to Z
#### Replace all characters A and c from input to Z and e respectively.
Script:
```ruby
#!/bin/bash
tr 'Ac' 'Ze'
```
The translate command (tr) is used to remplace the characters 'Ac' for 'Ze'

### 20. Without C, you would live in hiago
#### Create a script that removes all letters c and C from input.
Script:
```ruby
#!/bin/bash
tr -d Cc
```
The option '-d' is used to specify that the 'Cc' characters have to be deleted.

### 21. esreveR
#### Write a script that reverse its input.
Script:
```ruby
#!/bin/bash
rev
```
### 22. DJ Cut Killer
#### Write a script that displays all users and their home directories, sorted by users.
#### Based on the the /etc/passwd file.
Script:
```ruby
#!/bin/bash
cut -f 1,6 -d ':' /etc/passwd | sort
```
The command 'cut' is used to extract specific columns (or fields) from the file. The option '-f' is for specify the fields to extract and the '-d' is used to specify the delimiter.

### 23. Empty casks make the most noise
#### Write a command that finds all empty files and directories in the current directory and all sub-directories.
#### Only the names of the files and directories should be displayed (not the entire path)
#### Hidden files should be listed
#### One file name per line
#### The listing should end with a new line
#### You are not allowed to use basename, grep, egrep, fgrep or rgrep
Script:
```ruby
#!/bin/bash
find . -empty -printf "%f\n"
```
We use the 'find' command to search in the current directory '.' the empty files '-empty' and we specify that we have to print the files found with '-print "%f\n"'.

The '%f' means to print only the name.
