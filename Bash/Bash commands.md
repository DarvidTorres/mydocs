# pwd

pwd: print working directory

## cd

cd
* Asbolute path: cd /usr/bin
* relative parent path: cd ..
* relative subfolder: cd ./bin

If we type `cd` followed by nothing, `cd` will change the working directory to our home directory.

`cd -`: changes the working directory to the previous one.
`cd ~`: gets to home directory

using a dash as an argument of cd will change the current directory to the previous working directory

## List

ls

carpetas son en azul

- `less` (view text files)
- `file` (classify a file's contents [file type])
- `ls /directory`: list the files in the directory

`ls`: List the files in the working directory

`ls /bin`: List the files in the `/bin` directory (or any other directory we care to specify)

`ls -l`: List the files in the working directory in long format

`ls -l /etc /bin`: List the files in the `/bin` directory and the `/etc` directory in long format

`ls -la ..`: List all files (even ones with names beginning with a period character, which are normally hidden) in the parent of the working directory in long format

- `ls -l`: show long format
- `ls -a`: show all directories (including hidden ones)

We can also `ls -l file` to display a single file in long format (maybe to see permissions).

# chmod

r: read
w: write
x: execute

Each of these has a value:

r=4
w=2
x=1

Permissions are listed as follows:

User | Group | All (other)

rwx rwx rwx = 111 111 111

rw- rw- rw- = 110 110 110

rwx --- --- = 111 000 000

rwx = 111 in binary = 7

rw- = 110 in binary = 6

r-x = 101 in binary = 5

r-- = 100 in binary = 4

`-` indicates file, `d` indicates directory

`chmod 600 some_file`: The user can rwx, but others can't do nothing
`chmod 754 hello`: 

`chmod a+x`: add execution permissions to all users

You type chmod followed by a space, and a letter:
* a stands for all
* u stands for user
* g stands for group
* o stands for others

Then you type either + or - to add a permission, or
to remove it. Then you enter one or more permissions
symbols ( r , w , x ).

All followed by the file or folder name.

Here are some examples:

`chmod a+r filename` `#everyone` can now read
`chmod a+rw filename` `#everyone` can now read and write
`chmod o-rwx filename`

For directories we do:

r - Allows the contents of the directory to be listed if the x attribute is also set.

w - Allows files within the directory to be created, deleted, or renamed if the x attribute is also set.

x - Allows a directory to be entered (i.e. cd dir).

If you want to set permissions on all files to a+r, and all directories to a+x, and do that recursively through the complete subdirectory tree, use:

`chmod -R a+rX *`: the `-R` option makes it recursivelly for all files or directories. The X (that is capital X, not small x) is ignored for files (unless they are executable for someone already) but is used for directories.

- Copy permissions: `chmod --reference=file1 file 2`: copy permissions from file1 to file2 (`--reference` is just syntax)

# chown

`chown owner_name file_name`: change owner of the file

To simultaneously change both the owner and group of files or directories in linux use the following command structure:

`chown someusername:somegroupname filename.ext`: 
If you include the colon “:” but omit the group name it will assume whichever group the user belongs to.

On a Linux system, when changing the ownership of a symbolic link using chown, by default it changes the target of the symbolic link (ie, whatever the symbolic link is pointing to).

If you'd like to change ownership of the link itself, you need to use the -h option to chown:
`chown -h mj:mj test1`

`stat -c %U /path` get only owner

`chown --from=current_owner new_owner file.ex`: change owner to new_owner, only if current owner matches current_owner

# View text files

`file name_of_file`: see file type

`cat file`: print the content of file

`cat file1 file2`: we can `cat` multiple files at once

`less` text_file: read text file

`q`: quit

`cat write-content > destination-filename`: The content will be copied in destination file

`cat test test1 test2 > test3`: create a file called test3 and all output will be redirected in a newly created file. `cat "filename1" "filename2" "filename3" > "merged_filename"`

`cat >> file_name`: type text to file and exit with ctrl+C

`cat file1 >> file2`: Will append the contents of one file to the end of another file

`tac filename`: Will display content in reverse order

`cat test test1 test2 test3 | sort > test4`: create a file test4 and the output of the cat command is piped to sort and the result will be redirected to a newly created file

`cat *.txt`: display the content of all text files in the folder

# Sort

`sort` the contents of a text file, line by line according to the following behavior:

- Lines starting with a number will appear before lines starting with a letter.
- Lines starting with a letter that appears earlier in the alphabet will appear before lines starting with a letter that appears later in the alphabet.
- Lines starting with a uppercase letter will appear before lines starting with the same letter in lowercase.

`sort filename.txt`: This command does not actually change the input file, i.e. file.txt.

write the output to a new file, output.txt (both `>` and `-o` works exactly the same in this case)

`sort inputfile.txt > filename.txt`

`sort -o filename.txt inputfile.txt`

`sort -r inputfile.txt`: reverse the output

`sort -n file1.txt`: sort the file with numeric data present inside

`sort -nr filename.txt`: reverse the númeric sort

Use the -k option to sort on a certain column. For example, use “-k 2” to sort on the second column. 

`sort -k 2n employee.txt`: sort númerically based on the second column

`sort -c filename.txt`: check which lines are out of order

`sort -u filename.txt`: sort while removing duplicate lines (the file is altered)

# Create files

`touch file_name`

# Echo

`echo` is the print version of linux shell

`echo 'My first readme' > README.md`

`echo 'hello world'` will print a hello world message, we can use double or single quotes `echo "hello world"`

`echo -e 'something\nelse'`: to print multiple lines use `-e` option and add `\n` to write a new line

`echo "\""`: Prints one " character.

## Manipulating files

`cp` - copy files and directories
`mv` - move or rename files and directories
`rm` - remove files and directories
`mkdir` - create directories

Wildcards allow you to select filenames based on patterns of characters. 

[Learning the shell - Lesson 5: Manipulating Files](http://linuxcommand.org/lc3_lts0050.php)

Wildcards are like regex for the command terminal

## cp

cp file1 file2	Copies the contents of file1 into file2. If file2 does not exist, it is created; otherwise, file2 is silently overwritten with the contents of file1.

cp -i file1 file2	Like above however, since the "-i" (interactive) option is specified, if file2 exists, the user is prompted before it is overwritten with the contents of file1.

cp file1 dir1	Copy the contents of file1 (into a file named file1) inside of directory dir1.

cp -R dir1 dir2	Copy the contents of the directory dir1. If directory dir2 does not exist, it is created. Otherwise, it creates a directory named dir1 within directory dir2.

## rm

`rm file`: remove file

`rm file1 file2`: remove file1 and file2 at once

`rm -i file1 file2`

Like above however, since the "-i" (interactive) option is specified, the user is prompted before each file is deleted.

`rm -r dir1 dir2`

Directories dir1 and dir2 are deleted along with all of their contents.

`rm *~`: remove files ending with ~

## mkdir

`mkdir directory1`: Create directory1
`mkdir directory1 directory2`: Create directory1 and directory2 at once.

With the help of mkdir -p command you can create sub-directories of a directory. It will create parent directory first, if it doesn't exist. But if it already exists, then it will not print an error message and will move further to create sub-directories.

`mkdir -m 777 -p /parent/dirs/to/create/your/dir`

`mkdir -m rwx dirname`: creare a dirname directory in current directory while adding rwx permissions

When the directory already exist: `mkdir -m 777 /path/to/your/dir`

When the directory does not exist and you want to create the parent directories:

## rmdir

remove directory

# Emacs

- Opening: C-x C-f
- Saving: C-x C-s
- Cutting: C-k
- Pasting: C-y
- Searching: C-s
- Undoing: C-/
- Quitting: C-x C-c

# Vi

https://www.cs.colostate.edu/helpdocs/vi.html

Command mode commands which cause action to be taken on the file, and
Insert mode in which entered text is inserted into the file.

- :q<Return>	quit (or exit) vi
- :w!: save without exiting
- :wq!: save and exit
- :w new_file: save what's currently in file to a new_file, then stay in new_file

- \<ESC> enter Command Mode
- To enter Insert mode, press i

- dd	delete entire current line
- p	put (paste) the line(s) in the buffer into the text after the current line
- u	UNDO WHATEVER YOU JUST DID; a simple toggle
- :q! quit vi even though latest changes have not been saved for this vi call

# Git

`git add <file(s) to add>`

`git commit -m <A meaningful commit message>`

`git push`

For all unstaged files in current working directory use: `git restore .`

For a specific file use: `git restore path/to/file/to/revert`

# Bash

`Ctrl+L`: Clear the screen. This is similar to running the “clear” command.
`Ctrl+S`: Stop all output to the screen. This is particularly useful when running commands with a lot of long, verbose output, but you don’t want to stop the command itself with Ctrl+C.
`Ctrl+Q`: Resume output to the screen after stopping it with Ctrl+S.

`Ctrl+A or Home`: Go to the beginning of the line.
`Ctrl+E or End`: Go to the end of the line.
`Alt+B`: Go left (back) one word.
`Ctrl+B`: Go left (back) one character.
`Alt+F`: Go right (forward) one word.
`Ctrl+F`: Go right (forward) one character.
`Ctrl+XX`: Move between the beginning of the line and the current position of the cursor. This allows you to press Ctrl+XX to return to the start of the line, change something, and then press Ctrl+XX to go back to your original cursor position. To use this shortcut, hold the Ctrl key and tap the X key twice.

`Ctrl+D or Delete`: Delete the character under the cursor.
`Alt+D`: Delete all characters after the cursor on the current line.
`Ctrl+H or Backspace`: Delete the character before the cursor.

`Alt+T`: Swap the current word with the previous word.
`Ctrl+T`: Swap the last two characters before the cursor with each other. You can use this to quickly fix typos when you type two characters in the wrong order.
`Ctrl+_`: Undo your last key press. You can repeat this to undo multiple times.

`Ctrl+W`: Cut the word before the cursor, adding it to the clipboard.
`Ctrl+K`: Cut the part of the line after the cursor, adding it to the clipboard.
`Ctrl+U`: Cut the part of the line before the cursor, adding it to the clipboard.
`Ctrl+Y`: Paste the last thing you cut from the clipboard. The y here stands for “yank”.

`Alt+U`: Capitalize every character from the cursor to the end of the current word, converting the characters to upper case.
`Alt+L`: Uncapitalize every character from the cursor to the end of the current word, converting the characters to lower case.
`Alt+C`: Capitalize the character under the cursor. Your cursor will move to the end of the current word.


# Other

`chmod u+x file`: make a file executable

`#!/bin/bash`: https://en.wikipedia.org/wiki/Shebang_%28Unix%29

`wc -l file`: how many lines the script has
`wc -w file`: how many words the script has

`echo 12345 | rev`: reverse 12345 to 54321

`ln -s file link`: create a soft link to a file

# Users

`su <username>`: change user

If you want to execute a small task and do not want to change between users, the su command with the -c option can help you run terminal commands as another user.

`su -c <command> <username>`

Suppose we wanted to change the owner of some_file from "me" to "you". We could:

`sudo chown you some_file`

`whoami`: prints the current user

# Groups

`groups username`: display the groups the username is part of

`groups`: display the groups the current user belongs to (no username specified)

`id -Gn`: display the groups the user is in

`groups userName-Here`

`chgrp school hello`: change group owner to school

# head / tail

To display the 13th line, you can use a combination of head and tail:

head -13 file_name | tail +13

# Uniq

uniq [OPTION] [INPUT]

- `-c – -count `: It tells how many times a line was repeated by displaying a number as a prefix with the line.
- `-d – -repeated `: It only prints the repeated lines and not the lines which aren’t repeated.
- `-D – -all-repeated[=METHOD] `: It prints all duplicate lines and METHOD can be any of the - `following`: 
- `none `: Do not delimit duplicate lines at all. This is the default.
- `prepend `: Insert a blank line before each set of duplicated lines.
- `separate `: Insert a blank line between each set of duplicated lines.
- `-f N – -skip-fields(N) `: It allows you to skip N fields(a field is a group of characters, delimited by whitespace) of a line before determining the uniqueness of a line.
- `-i – -ignore case `: By default, comparisons done are case sensitive but with this option case insensitive comparisons can be made.
- `-s N – -skip-chars(N) `: It doesn’t compare the first N characters of each line while determining uniqueness. This is like the -f option, but it skips individual characters rather than fields.
- `-u – -unique `: It allows you to print only unique lines.
- `-z – -zero-terminated `: It will make a line end with 0 bytes (NULL), instead of a newline.
- `-w N – -check-chars(N) `: It only compares N characters in a line.
- `– – help `: It displays a help message and exit.
- `– – version `: It displays version information and exit.

# Pipping |

rm, like many other programs, takes its arguments from the command line but ignores standard input. You can pipe anything to it you like; it'll just throw that data away. That's where xargs comes in handy. It reads lines on standard input and turns them into command-line arguments, so you can effectively pipe data to the command line of another program. It's a neat trick.

For example:

find . -name ".txt" | xargs rm
find . -name ".txt" | grep "foo" | xargs rm 

`ls -t | head -n 10`: Create a script that displays the 10 newest files in the current directory.

`sort | uniq -u`: Create a script that takes a list of words as input and prints only words that appear exactly once.

`cat words.txt | sort | uniq -u`: if you have a file called words.txt with a list of words, you can run the script like this:

# Globs

`*`: Matches any string, of any length

`foo*`: Matches any string beginning with foo

`*x*`: Matches any string containing an x (beginning, middle or end)

`*.tar.gz`: Matches any string ending with .tar.gz

`*.[ch]`: Matches any string ending with .c or .h

`foo?`: Matches foot or foo$ but not fools

`[abcd]`: Matches a or b or c or d

`[a-d]`: The same as above, if globasciiranges is set or your locale is C or POSIX. Otherwise, implementation-defined.

`[!aeiouAEIOU]`: Matches any character except a, e, i, o, u and their uppercase counterparts

`[[:alnum:]]`: Matches any alphanumeric character in the current locale (letter or number)

`[[:space:]]`: Matches any whitespace character

`[![:space:]]`: Matches any character that is not whitespace

`[[:digit:]_.]`: Matches any digit, or _ or .

# Find

https://explainshell.com/explain?cmd=find%20%2Fusr%2Finclude%20-printf%20%25P%5C%5Cn%20%3E%20found_files

It supports searching by file, folder, name, creation date, modification date, owner and permissions.

`find ./GFG -name sample.txt `: Search sample.txt in ./GFG directory.
`find ./GFG -name *.txt`: It will give all files which have ‘.txt’ at the end.
`find ./GFG -empty`: Search for empty files and directories.
`find ./GFG -perm 664`: Search for file with entered permissions

`find . -name "*.txt" -exec ls -a {} \;`: find within the current directory (`.`) files with extension `.txt`, then all take the files.txt found and pass them onto `ls -a`. The `{}` is a placeholder for filename, so if the `find` command gets `foo.txt` and `bar.txt`, `ls -a` will process them and show the details of each. finally, the `;` tells the `-exec` option to stop processing commands. The `;` is escaped with a `\` because usually `;` is used to separate commands in a single line.

`find . -name "*.bak" -type f -delete`

find . -type d | wc -l

`find . -mindepth 1 -maxdepth 1 -type d | wc -l`

`find . -mindepth 1 -type d | wc -l`: script that counts the number of directories and sub-directories in the current directory. The current and parent directories should not be taken into account. Hidden directories should be counted

`find . -type f -print | wc -l`: Displays the total number of files in the current working directory and all of its subdirectories.

https://www.geeksforgeeks.org/mindepth-maxdepth-linux-find-command-limiting-search-specific-directory/

`find . -type d -empty -o -type f -empty`: locate all empty files and directories in the current directory and all its subdirectories

`find . -type d -empty -printf '%f\n' -o -type f -empty -printf '%f\n'`: use the find command with the -printf option to display only the names of empty files and directories in the current directory and its subdirectories. 

`find . -type f -name '*.gif' -printf '%f\n'`: list all files with a .gif extension in the current directory and all of its subdirectories

# grep

Searches a file (whithin a directory) given a particular pattern of characters, and displays all lines that contain that pattern.

`-c `: This prints only a count of the lines that match a pattern

`-h `: Display the matched lines, but do not display the filenames.

`-i `: Ignores, case for matching

`-l `: Displays list of a filenames only.

`-n `: Display the matched lines and their line numbers.

`-v `: This prints out all the lines that do not matches the pattern

`-e exp `: Specifies expression with this option. Can use multiple times.

`-f file `: Takes patterns from file, one per line.

`-E `: Treats pattern as an extended regular expression (ERE)

`-w `: Match whole word

`-o `: Print only the matched parts of a matching line,

 with each such part on a separate output line.

`-A n `: Prints searched line and nlines after the result.

`-B n `: Prints searched line and n line before the result.

`-C n `: Prints searched line and n lines after before the result.


`grep bin /etc/passwd | wc -l`: count lines containing "bin" in /etc/passwd

`grep -c bin /etc/passwd`: count lines containing "bin" in /etc/passwd

`grep -A 3 "root" /etc/passwd`: show lines with "root" and 3 lines after them

`grep -v "bin" /etc/passwd`: You can use the grep command with the -v option to display all the lines in the file /etc/passwd that do not contain the pattern "bin"

`grep "^[[:alpha:]]" /etc/ssh/sshd_config`: Display all lines of the file /etc/ssh/sshd_config starting with a letter. include capital letters as well

# tr

`cat file | tr [:lower:] [:upper:]`: translate lower case letters for upper case in file
`tr [:lower:] [:upper:] < greekfile`: same as above but take input using redirection

`echo "Welcome To GeeksforGeeks" | tr [:space:] "\t"`: translate spaces for tabs

`tr "{}" "()" < oldfile > newfile`: translate braces into parenthesis in oldfile, then take the output and write newfile

`echo "Welcome    To    GeeksforGeeks" | tr -s " "`: remove repetitive spaces using `-s` option

`echo "Welcome To GeeksforGeeks" | tr -d W`: delete characters using `-d` option

`echo "my ID is 73535" | tr -d [:digit:]`: delete all digits

the `-c` option complements the set of characters in string

`echo "my ID is 73535" | tr -cd [:digit:]`: delete all but digits


`tr 'Ac' 'Ze' < input.txt`: change A for Z and c for e.


https://youtu.be/nyoZ8VeMEq0?t=119

# cut

`cut -b 1,2,3 state.txt`: get characters 1 to 3 from each line in state.txt

`cut -b 1-3,5-7 state.txt`: get characters 1 to 7 except 4

`cut -b 1- state.txt`: 1- indicate from 1st byte to end byte of a line

`cut -b -3 state.txt`: -3 indicate from 1st byte to 3rd byte of a line

To cut by characters, specify the -c option:

`cut -c 10- employees.txt`: The command extracts everything from character 10 until the end of the line from each line of employees.txt.

`cut -c 2,5,7 state.txt`: cut command prints second, fifth and seventh character from each line of the file (space is also a character)

Let's say we `cat /etc/passwd`
```
root:x:0:0:root:/root:/bin/bash                           
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
```

The `cut -d : -f 1,6 /etc/passwd` will get fields 1 and 6 (`-f`) from each line, those fields are identified by the colon delimiter `-d :`

Without specifying the -d option means that the default delimiter is the tab character.

The `--complement` option prints everything except for the character/byte/field at the specified position.

`cut employees.txt -f 1 --complement`: Get all but first field from employees.txt

Specify a delimiter in the output using the `--output-delimiter` option.

`cut employees.txt -f 1,3 --output-delimiter='_'`: get fields 1 and 3 from employees.txt and then output them by "-" delimiter.

# paste

join files horizontally (parallel merging) by outputting lines consisting of lines from each file specified, separated by tab as delimiter, to the standard output. When no file is specified, or put dash (“-“) instead of file name, paste reads from standard input and gives output as it is until a interrupt command [Ctrl-c] is given.

`paste number state capital`: horizontally concatenate files (line by line) by tab delimiter

`paste -d "|" number state capital`: concatenate using | as delimiter

`paste -d "|," number state capital`: concatenate first field with | second with , After that list is exhausted and reused.

`paste -s number state capital`: concatenate vertically, that is, instead of concatenate lines from files as columns in output, take all lines from first file then print as single line (tab separated), then print next file as single line, etc.

`paste -s -d ":" number state capital`: concatenate vertically using : delimiter

`cat capital | paste - -`: take first two lines of capital and concatenate as single line (tab separated), then print next two lines and so on

`paste - - - < capital`: concatenate every three lines of same file


# Quotes

`echo "'"`: will print '

`echo "\""`: will print "

`echo "'\""`: will print '"

`echo abc"'\""`: will print abc'"


Let's say we want to print the following message:

'single quote phrase' "double quote phrase"

We can try: `echo $'\'single quote phrase\' "double quote phrase"'`

Backslash escape sequences, if present, are decoded as follows:

```
 a alert (bell)
 b backspace
 e
 E an escape character
 f form feed
 n new line
 r carriage return
 t horizontal tab
 v vertical tab
 \ backslash
 ' single quote
 " double quote
 nnn the eight-bit character whose value is the octal value nnn (one
 to three digits)
 xHH the eight-bit character whose value is the hexadecimal value HH
 (one or two hex digits)
 cx a control-x character
```

So to do that in Bash we need to escape some quotes from the `echo` command

When we need to suppress all expansions, we use single quotes. Here is a comparison of unquoted, double quotes, and single quotes:

echo "Best School" > \\\*\\\\"'\"Best School\"\\'"\\\\\*\$\\\?\\\*\\\*\\\*\\\*\\\*\:\)

```
[me@linuxbox me]$ echo text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
text /home/me/ls-output.txt a b foo 4 me

[me@linuxbox me]$ echo "text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER"
text ~/*.txt {a,b} foo 4 me

[me@linuxbox me]$ echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER'
text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
```

As we can see, with each succeeding level of quoting, more and more of the expansions are suppressed.

# alias

alias command instructs the shell to replace one string with another while executing commands

`alias name="value"`: when type name, shell exectues value

`alias ls="rm *"`: if type `rm *`, shell will exectue `ls`

`unalias alias_name`: remove an alias

`alias -p`: prints all defined aliases

# variables

`printenv`: get all global defined variables
`set`: lists all local variables and environment variables, and functions

Bash System-defined Variables :

```
$HOME # Home Directory  
$PWD # current working directory  
$BASH # Bash shell name  
$BASH_VERSION # Bash shell Version  
$LOGNAME # Name of the Login User  
$OSTYPE # Type of OS  
```

## User defined variables

`BEST="School"`: create a local variable

`export BEST="School"`: create a global variable (use the command `export` to achieve this)

```
name=Peter  
ROLL_NO=5245325  
echo "The student name is $name and his Roll number is $ROLL_NO." 
```

# alias vs variables:

```
foo="mkdir Directory"
echo $foo  # Prints "mkdir Directory"

alias bar="mkdir Directory"
echo bar  # Nothing gets expanded -- just "bar" is printed

$ myCommand="echo *"
$ $myCommand
file1.x file2.y file3.z
The * is expanded - which isn't what you wanted - so then try this:

$ myCommand="echo \"*\""
$ $myCommand
"*"
But now you have extra quotes appearing - you didn't want that either!

But this works OK:

$ echo "*"
*
And so does this:

$ alias myCommand="echo \"*\""
$ myCommand
*
This is because quotes inside a variable are treated as literal, rather than syntactical when a variable is expanded - so in this case they become part of the parameter that is passed to the echo command - whereas with an alias the command is executed "as is" and the quotes are treated as syntactical and are parsed out before echo is called, just as they are when you type the same command in directly from the command line.
```

# Arithmetic operations

https://linuxhint.com/bash_arithmetic_operations/

# Brace expansion

`echo {one,two,three,four}`: print one two three four

`echo {4,2,3,1}`: print 4 2 3 1

`echo {1..10}`: print the digits from 1 to 10.

`echo {3..12}`: print from 3 to 12

`echo {5..1}`: 5 4 3 2 1

`echo {4..-4}`: 4 3 2 1 0 -1 -2 -3 -4

`echo {q..v}`: q r s t u v w

`echo {f..a}`: f e d c b a

`echo {q..v}{1..3}`: q1 q2 q3 r1 r2 r3 ... v1 v2 v3

`echo {part-1,part-2{a,b,c,d},part-3}`: part-1 part-2a part2.b ... part-2d part3

`echo {{5..0},{1..5}}`: 5 4 3 2 1 0 1 2 3 4 5

# C Learning objectives

How to print text using printf, puts and putchar
How to get the size of a specific type using the unary operator sizeof
How to compile using gcc
What is the default program name when compiling with gcc
What is the official C coding style and how to check your code with betty-style
How to find the right header to include in your source code when using a standard library function
How does the main function influence the return value of the program



