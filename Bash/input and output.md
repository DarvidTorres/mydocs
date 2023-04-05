# I/O

we can redirect the output of many commands to files, devices, and even to the input of other commands.

`ls > file_list.txt`: To redirect standard output to a file, the ">" character

Each time the command above is repeated, file_list.txt is overwritten from the beginning with the output of the command ls.

`ls >> file_list.txt`: To have the new results appended to the file instead, we use ">>"

- Standard input (keyboard): 0
- Standard output (display): 1
- Error output (display default message): 2

Let's say an error comes back in the shell, but you want it in a file 
`ls asdfasdf >> listoutput`: It's going to display an error (2)
So, to append the error output to the file we need: `2>` or `2>>` like so: `ls asdf 2> errorfile`

You can print the errors and standard output to a single file by using the &1 command to redirect the output for STDERR to STDOUT and then sending the output from STDOUT to a file:

`dir file.xxx 1> output.msg 2>&1`