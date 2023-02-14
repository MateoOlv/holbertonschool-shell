# Explication of every task

### 0. Hello World

Write a script that prints “Hello, World”, followed by a new line to the standard output.

Script:
```ruby
#!/bin/bash

echo Hello, World
```
The 'echo' command is used to display a message.


### 1. Confused smiley

Write a script that displays a confused smiley "(Ôo)'.

Script:
```ruby
#!/bin/bash

echo "\"(Ôo)'"
```
The string have double quotes (") so to ignore it we use a backslash (\) to avoid misinterpretation by the shell.

### 2. Let's display a file

Display the content of the /etc/passwd file.

Script:
```ruby
#!/bin/bash

cat /etc/passwd
```
The 'cat' command is for looking inside of an file. passwd is the file that we are looking.

### 3. What about 2?

Script:
```ruby
#!/bin/bash

cat /etc/passwd /etc/hosts
```
We can use cat to look in differents files. In this case passwd and hosts

### 4. Last lines of a file

Display the last 10 lines of /etc/passwd

Script:
```ruby
#!/bin/bash

tail -n 10 /etc/passwd
```
The 'tail' command is used to display the last lines of the file. we use the '-n' option to specify the number of lines to display. '10' are the number of lines.

### 5. I'd prefer the first ones actually

Script
```ruby
#!/bin/bash

head -n 10 /etc/passwd
```
The 'head' command is for display the first lines on the file. the rest is like the task 4.

### 6. Line #2

Write a script that displays the third line of the file iacta.

The file iacta will be in the working directory

You’re not allowed to use 'sed'

Script
```ruby
#!/bin/bash

head -3 iacta | tail -1
```
For this activity first we have to get the first 3 lines of the file. We use the '|' to send the output of the head to the next command 'tail' and we use this output to get last line of that result that will be the third line of the file. 

### 7. It is a good file that cuts iron without making a noise

Write a shell script that creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.

Script:
```ruby
#!/bin/bash

echo "Best School" >> "\\*\\\'\"Best School\"\'\\\*$\\?\*\*\*\*\*:)"
```
We use the command 'echo' to print the text 'Best School' and the redirection operator (>>). in this task we have to varius special characters like backslashees to get our file name. The  backslash (\) prevents the next character from being interpreted as a special character. so if we need one '\' in the script we have to write '\\'. if we need two then '\\\'.

### 8. Save current state of directory

Write a script that writes into the file ls_cwd_content the result of the command ls -la. If the file ls_cwd_content already exists, it should be overwritten. If the file ls_cwd_content does not exist, create it.

Script:
```ruby
#!/bin/bash

ls -la >> ls_cwd_content
```
The 'ls' command is for listing the contents of a directory. The '-l' options tells to display the content in a long format which includes details such as permissions, owner, group, size, and date modified. The '-a' options thells to show hidden files and directories.

'>>'  is the redirection operator that get the output of the command and save it on a file (with this operator if the file exist the output is saved at the end of the file).

### 9. Duplicate last line

Write a script that duplicates the last line of the file iacta
The file iacta will be in the working directory
