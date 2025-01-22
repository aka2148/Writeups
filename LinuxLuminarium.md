# Pondering Paths

## 1. The root
basic /pwn command to be run and flag is found

## 2. Program and Absolute Paths
simply run /challenge/run to get the flag

## 3. Position thyself
Have to change directory to the /etc directory in order to run the /challenge/run command

## 4. Position elsewhere
Very similar to the above challenge but we used the absolute path here instead.

## 5. Position yet elsewhere
Same as above 2

## 6. Implicit relative paths
Explains relative path working with respect to cwd. We just had to specify the root  first, and then type challenge/run

## 7. Explicit relative paths
Learned about  how every directory has two implicit entries that we can reference in paths
Ex:challenge
./challenge are both equivalent to each other. Used ./challenge/run to get the flag

## 8. Implicit relative path
We need to explicitly specify what we want using ./ so that the system does not mistake our command as an access to core system utilities.

## 9. Home sweet Home
Change to the /challenge directory and then invoke run explicitly using ./ into a file of  your choice. (file must be in home directory.)
Flag:pwn.college{cNye7STfs-ZcEwHzHNtw439vOBW.dNzM4QDLzAzMykzW}




# Comprehending Commands

## 1. Cat, the command not the pet
simply cat the flag file to get the flag
Flag:pwn.college{05ETKr5D1MW9DVe4vgO5t8_9AgR.dFzN1QDLzAzMykzW}

## 2. Catting absolute paths
Here we cat the absolute path /flag to get the file
Flag:pwn.college{IftzSeEF1p3vktOBf7OHyQWyRTR.dlTM5QDLzAzMykzW}

## 3. More catting practice
Here we again cat with absolute path. Cannot cd
Flag: pwn.college{QLO-FBjG1hERp-IDJUo-gFhampP.dBjM5QDLzAzMykzW}

## 4. Grepping for needle in a haystack
Used grep command (syntax: grep SEARCH_STRING /path/to/file) to search for the flag
Flag:

## 5. Listing files
USed ls command to find the file in the /challenge directory to which run had been renamed
Flag:pwn.college{AX0ajdHLXAcUNFcHddAq2mL9fx9.dhjM4QDLzAzMykzW}

## 6. Touching files
the touch command allows us to create new blank files by touching it.
IWe had to use the touch command to create two new files and then run /challenge/run.
Flag:pwn.college{ksV9acpLlVlGAx-V62C1Lid9---.dBzM4QDLzAzMykzW}

## 7.Removing files
Use rm command to delete unwanted files
Flag: pwn.college{YIrLyt1dyGzTnZW7teB4mNVcLLP.dZTOwUDLzAzMykzW}

## 8. Hidden files
ls does not list all files by default. The suffix -a must be added to see hidden files. We use ls -a to find the file with the flag.
Flag:pwn.college{8brdh3mrZU5bC_JOllGHTMl05R0.dBTN4QDLzAzMykzW}

## 9. An epic filesystem quest
Here we use the cd, ls and cat commands to follow the hints left by the system.
We cannot cd into the last directory and must use absolute path to get the flag.
Flag: pwn.college{QErWRbXrPoqi9OD-p7j-_QD3U-w.dljM4QDLzAzMykzW}

## 10. Making Directories
Use mkdir command to make directories and touch a file(college) to get the flag.
Flag:pwn.college{03s_EvFohL0f1ns_Uo8OMkbwcpP.dFzM4QDLzAzMykzW}

## 11. Finding Files
Used find -name flag to get all files with flag in the name and then catted them until I got the file with the flag
Flag:pwn.college{AgaBrdKL9y9cNDKL7y1CPHGuZGx.dJzM4QDLzAzMykzW}

## 12. Linking Files
Here we learn about symlinks. First you delete the /home/hacker/not-the-flag file and then symlink the flag to the file.
flag:pwn.college{0qXs_T1M6V5rfVV1hlJvrDT7PiU.dlTM1UDLzAzMykzW}




# Digesting Documentation

## 1. Leearning from documentation
Here we simply pass the argument --giveflag to the command /challenge/challenge and we get the flag.
Flag:pwn.college{cE-tc9bypLyFXY6746pao2r5YDA.dRjM5QDLzAzMykzW}

## 2. Learning complex Usage
Here we pass an argument to an argument in order to get the flag
Flag:pwn.college{cXjLhfjTIL-IIyINPS3gW-tLJQ2.dVjM5QDLzAzMykzW}

## 3. Reading Manuals
Here we go to the man page of the challenge command and find the argument that must be passed in order to get the flag.
Flag: pwn.college{IuP-BJzTqQfBmnYQOcKNXoYZbY3.dRTM4QDLzAzMykzW}

## 4. Searching Manuals
Here we again search the manpage of the challenge command and use the / command to search the page for the correct argument.
Flag: pwn.college{ALuc-FD5m43zcTdJDpcfjbZpf7r.dVTM4QDLzAzMykzW}

## 6. Searching for Manuals
Here we use the -k command to search for the hidden manpage that gives us the correct argument.
Flag: pwn.college{8yJW18ROVJ6O0Z3nQWre9WElrdz.dZTM4QDLzAzMykzW}

## 7.Helpful Programs
This challenge involves using --help to find more information about the commands when the manpagel is not present We had to pass an argument -g to /challenge/challenge with a secret number.\
Flag: wn.college{YwrI9hVqPirMPAa_nKo6S9_Qy9C.ddjM4QDLzAzMykzW}

## 8. Help for builtins
we had to use help challenge to find the '--secret' argument along with its special value to get the flag.
Flag:



# File Globbing

## 1. Matching with *
Here we cd'd using cd /ch* in order to keep the argument less than 4 words. 
Flag:pwn.college{I4BGX2faTcifZgmv7viWLsZzIYX.dFjM4QDLzAzMykzW}

## 2. Matching with ?
Here we use the ? command which replaces one letter and pass ?ha??enge in cd command.
Flag:pwn.college{suEd292egulQxVE47oYJsxAeYqq.dJjM4QDLzAzMykzW}

## 3. Matching with []
Here we use the /challenge/run file_[bash] command to list the specified files 
Flag:pwn.college{EGuwjW5bmn3ervWXKirgjnL4Y6r.dNjM4QDLzAzMykzW}

##4. matching paths with []
Here we specify the path to the files we are globbing using /challenge/run /challenge/files/file_[bash] as argument.
Flag:pwn.college{AZXBUVmrQtiLxHk5aFpFbuS2sVr.dRjM4QDLzAzMykzW}

## 5. Mixing globs
Here the pattern is found in the fact that all files start with a different letter.
We use [cep]* as the ncesarry glob
Flag:pwn.college{gqXsXMBzabNNJ3hOZzfq5_mhGC-.dVjM4QDLzAzMykzW}

## 6. Exclusionary globs
Here we use the ! to exclude the letters in the glob. We pass [!pwn]* to get the flag.
Flag: pwn.college{M35Pvqm3B9tT8_zzSbDFJnjg8lb.dZjM4QDLzAzMykzW}




# practicing Piping

## 1. Redirecting output
Here we redirect the PWN text to the COLLEGE file using >
Flag:pwn.college{Ihlq61o__mYqwn7LijnnvRz2oGb.dRjN1QDLzAzMykzW}

## 2. Redirecting More Output
Here we redirect the /challenge/run output to myflag file and cat it.
flag:pwn.college{4qAMPDZRv60pB1SJh3lt8n8_HTb.dVjN1QDLzAzMykzW}

## 3. Appending Output
Here we use the append >> in order to avoid wiping the previous text present in the file.
Flag:pwn.college{08FOpUWEva2rJh0iCpvhwP0TSia.ddDM5QDLzAzMykzW}

## 4. Redirecting errors
Here we redirect output to the myflag file and errors  to the instruction file by using 2 as the File directory number.
Flag:[FLAG] pwn.college{0jVb7yeWkt5KbzQzRTItfW61lhm.ddjN1QDLzAzMykzW}

## 5.Redirecting Input
The < character is used to redirect the standard input to programs.
In this challenge, we used echo,<and > collectively to redirect the flag
Flag : The < character is used to redirect the standard input to programs.
In this challenge, we used echo,<and > collectively to redirect the flag

## 6. Grepping stored results
Here we redirect ouput of /challenge/run to txt file and we grep for the flag using pwn.college.
Flag: pwn.college{oMc8pbJz4Z00_qQh7twd4-_0Y4V.dhTM4QDLzAzMykzW}

## 7. Grepping Live output
Here we use the Pipe operator to search the command for the flag. /challenge/run | grep pwn.college.
Flag: pwn.college{QaKN6Bb3YKt369yDSHWYrOuMFh6.dlTM4QDLzAzMykzW}

## 8.Grepping errors
Here we use the >& operator to redirect the file descriptor to another file descriptor. 
/challenge/run 2>&1 | grep pwn.college
Flag:pwn.college{4pfFUWwtyT0DazHYt2uSvYIRY-N.dVDM5QDLzAzMykzW}

## 9.Duplicating Piped data with tee
The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line.
Flag: pwn.college{EnTqoXMxsKeg1c-i4-EGe0ll4Ks.dFjM5QDLzAzMykzW}

## 10. Writing to multiple Programs
Here we have to duplicate the output of /challenge/hack and redirect it as input to both /challenge/the and /challenge/world. Use parentheses in the commands to avoid error.
/challenge/hack | tee >(/challenge/the) >(/challenge/planet)
Flag:pwn.college{UFgItamIPOVQmx-bqXeibK6-nIu.dBDO0UDLzAzMykzW}


## 11 Split Piping
Got really stuck trying to use | in this manner :/challenge/hack 2> | /challenge/the 1> | /challenge/planet. Didn't work at all. Found out that >() is equivalent to | so i changed it to /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Which got me the flag but not exactly sure why the normal pipe doesn't work.
Flag:pwn.college{QJcziLYRO3Y73sWBqBrR0eMnL4U.dFDNwYDLzAzMykzW}



# Shell variables

## 1. Printing Variables
We simply use echo $(variable) to print the variables value. Here the variable is FLAG
Flag: pwn.college{stnxRtJCgb57WBgAnx4AvBk3IAu.ddTN1QDLzAzMykzW}

## 2. Setting variables
Here we use = to give the variable PWN the value of COLLEGE. We do not use $ as it is only used to access variables
Flag:wn.college{Q1G0C-eb8u-U3YrhbA8G1kgIhHB.dlTN1QDLzAzMykzW}

## 3.Multi word variables
HEre we put the enitre argument in " " in order to make multi word variables.
Flag: pwn.college{8CzHiaBBynWVXnASTMo_TPbTTTg.dBjN1QDLzAzMykzW}

## 4. Exporting Variables
Here we export the value of PWN to COLLEGE which allows it to pass into the environment variables of child processes. We then pass it as an argument to /challenge/run
Flag:pwn.college{4wSxW509mfsOC87aQB_YL4CsYUK.dJjN1QDLzAzMykzW}

## 5.Printing exported variables
Here I redirected the output of env which prints all exported variables to a file i created. I then used grep to find the flag.
Flag:pwn.college{o7Eai8WGNWtJla5xzGQFeqpFPbh.dhTN1QDLzAzMykzW}


## 6.Sorting command output
HEre we read the output of /challenge/run into the PWN variable and then echo it to get the flag.
Flag:pwn.college{I0qDJqVij_V4HnnRma4_Ykbi9FE.dVzN0UDLzAzMykzW}

## 7. Reading input
Here we use the read function to set the value of PWN to COLLEGE
Flag:pwn.college{UsiB2eUN4y3AgQkYZX2ej7fhyoj.dhzN1QDLzAzMykzW}

## 8. Reading Files
Here we read the contents of the file by passing it as standard input to the variable which is apssed to read function and we get the flag.

Flag:pwn.college{Qva0P19m7ctoSMHR1BcJaGyxaLi.dBjM4QDLzAzMykzW}



# Processes and Jobs

## 1.Listing processes
Here we learn the ps command which lists all procceses running. We use this to find the hidden run command,
Flag:pwn.college{M3f3Mq2Zjxty2QnTDCj1Cditx4b.dhzM4QDLzAzMykzW}

## 2. Killing processes
Here we must kill the dont_run process by using grep to find it within the ps-ef list.
Flag: pwn.college{YsapGv8Ja5wLWbZvjIPdbK3aspn.dJDN4QDLzAzMykzW}

## 3. Interrupting processes
Just use Ctrl+c to interrupt the current process
Flag:pwn.college{QE7m2WHeRKYZekEtzMqUKrlVCA4.dNDN4QDLzAzMykzW}

## 4. SUspending processes
Here we have to suspend a process using Ctrl+z and then launch another of the same process to get the flag.
Flag :pwn.college{0uwKnIKAao9mzCkC8YvIm-mwT4M.dVDN4QDLzAzMykzW}

## 5. resuming processes
Here we suspend the process with CtrlZ and resume it using fg
Flag:pwn.college{YM4j754D87MYqP8fjyFVwON1Xrp.dZDN4QDLzAzMykzW}

## 6. Background processing
Here we need to use bg to resume to process in the background and rerun the command to get the flag.
Flag:pwn.college{QoPXZYij9QhjW_d7AeFpKME7aqw.ddDN4QDLzAzMykzW}

## 7. Foreground processing
Same as above but instead of rerunning command we use fg to foreground it.
Flag:pwn.college{8yDYoZKjkC5IzKj2q6WNdOIerrd.dhDN4QDLzAzMykzW}

## 8. Starting background processes
Here we use the & suffix to run the process in the background from the start.
Flag: pwn.college{YE8KntRp0UBHhcK-wMjHpk4iyY2.dlDN4QDLzAzMykzW}

## 9. Process exit codes
Here we get the error code by using the $ operator to read ?. 
Flag: pwn.college{07fvAqX6h-Mi_DRTSQSirVhHVY0.dljN4UDLzAzMykzW}



# Perceiving Permissions

## 1. Changing file ownership
Here we use the chown (change owner) command to change the owner of the file from root to hacker so we can cat it.
Flag:pwn.college{wUHhRK9nObBpF4mhCL3cN2Sgob7.dFTM2QDLzAzMykzW}

## 2. groups and files
Same as above but we change the group ownership instead of user.
Flag: pwn.college{s0Wa63DX8kNpkltS9Hi_lZQMJvi.dFzNyUDLzAzMykzW}

## 3. Fun with group names
Here we have to use the id cmmand to find the group name which has our file. We then use chgrp to change the group and we get the flag.
Flag :pwn.college{clDxG5Tkq4HRTXtdTNbPvIe6p-Q.dJzNyUDLzAzMykzW}

## 4. Changing permissions
Here we are introduced to chmod to change permissions. Format of WHO+/-WHAT, where WHO is user/group/other and WHAT is read/write/execute. For example, to add read access for the owning user, you would specify a mode of u+r. We use chmod a+rwx to add all permissions and we get the flag by catting
Flag:pwn.college{IJPgd0XZmDqGRdtzeVs8Dg2ZkT3.dNzNyUDLzAzMykzW}

## 5. Executable files
Same as above
Flag:pwn.college{woiZlmR4ef-f3zSeoW1w1ieAPbH.dJTM2QDLzAzMykzW}

## 6. Permissions tweaking practice
Here we have to adjust the permissions 8 times in a row correctly to get the flag
Flag:pwn.college{I-aLHIDp6CNjYdjjdAT2h6lq2bd.dNTM5QDLzAzMykzW}

## 7. Permission settings practice
Here we use = operator to set permissions 8 times in a row correctly and get the flag.
Flag:wn.college{I-aLHIDp6CNjYdjjdAT2h6lq2bd.dNTM5QDLzAzMykzW}

## 8. The SUID bit
Here we learn about the SUID bit which allows anyone to run the file as a root user as long as they have access to it.
Flag:pwn.college{o9Qq9njKYqGGBcKIvh2fzY8mH1H.dNTM2QDLzAzMykzW}



# Untangling Users

## 1. Becoming root with su
Note:  Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell! Of course, su is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password:
This check against the root password is what obsoletes su. Modern systems very rarely have root passwords, and different mechanisms (that we will learn later) are used to grant administrative access.
Here we use the su command and enter the password to get root access and cat the flag.
Flag:pwn.college{UYBbqLXQhv8EML4sT9ti-WIxGQU.dVTN0UDLzAzMykzW}

## 2. Other users with su
Here we pass a user as an argument to the su command in order to switch to that user and run /challenge/run.
Flag:pwn.college{UYBbqLXQhv8EML4sT9ti-WIxGQU.dVTN0UDLzAzMykzW}

## 3.Cracking passwords
Here we learn about the /etc/shadow command which stores the password in a hashed form. If we can get this hashed form we can crack it using tools like john the ripper. Here we do exactly that and get the flag.
Flag:pwn.college{0HsL2QKbpO-0x6va4VwSZutCrF8.ddTN0UDLzAzMykzW}

## 4 Using sudo
Note:Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root:
Also unlike su, rather than authenticating via password, sudo relies on policies that it checks to determine the user's authorization run things as root.
Here we use the sudo command to cat the flag
flag: Also unlike su, rather than authenticating via password, sudo relies on policies that it checks to determine the user's authorization run things as root.



# Chaining Commands

## 1. Chaining with semicolons
Here we use the ; to chain commands together. ex 
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
Flag:pwn.college{EzJxS1Ci81vKtWua_Sd16Q75XGE.dVTN4QDLzAzMykzW}

## 2.Your first Shell script
Note:We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix)
Important to remember to append the second command and not just redirect to avoid wiping the initial data.
Here we echo both /challenge/pwn and /challenge/college to pwn.sh and use bash to execute.
Flag:pwn.college{o52yE5CxRuNoWRYhivqPgVwnuOZ.dFzN4QDLzAzMykzW}

## 3. Redirecting shell script
Here we pipe the shellscript to another command.
echo /challenge/pwn > pwn.sh
echo /challenge/college >> pwn.sh
 bash pwn.sh | /challenge/solve
 Flag:pwn.college{slQaY8RGrMskAlrdiQ8qKslU_Bq.dhTM5QDLzAzMykzW}
 
 ## 4. Executable shell scripts
 Here we change permmissions to allow us to execute the pwn.sh file without bash and get the flag.
 Flag:pwn.college{Ep2d2GTMrdrzxMX81776XsNWcEH.dRzNyUDLzAzMykzW}



 # Pondering Path

## 1. The path variable
Here we learn about PATH which stores a bunch of directory paths in which the shell will search for programs corresponding to commands.
We must remove the path to the rm command in order to prevent the flag from being deleted when running /challenge/run.
Flag:pwn.college{UjWWZHGkUfMRjsxfVVS4YmGmcpr.dZzNwUDLzAzMykzW}

## 2.Setting path
In this challenge we set paths using the PATH command. By setting PATH=/challenge/more_commands
we allow ourselves to call the function by its barename instead of having to type the entire path.
Flag:pwn.college{IwwzMfiDf_HfdVHYsxDBEybwjfX.dVzNyUDLzAzMykzW}

## 3. Adding commands
Ok this one was very annoying. Here we have to find the absolute path of cat which can be found using the which cat command (had to google how to find absolute path of command lol). After that we need to echo that into the win file like:

echo /run/dojo/bin/cat /flag > win.

This is the same as echoing cat /flag but we have to use the absolute path since win cannot find where cat is since we are changing the path. We then set the path as the path to the win file and run /challenge/run to get the flag.
Flag:pwn.college{QbJ_ly22kVlKd6y_abjr85F-YLg.dZzNyUDLzAzMykzW}

## 4. Hijacking Commands
Spent way too much time trying to create another win file and passing that to challenge.
Upon changing path flag wasnt removed as system could not find rm but nothing was printed. 

Tried to echo cat to a seperate file but that failed since after changing path i couldn't run anything anyway.

Figured out that since the system was always going to try to rm the flag if i could replace rm with cat it would be very nice.

Got a big hint from the name of the challenge being hijacking commands lol.
echoed /run/dojo/bin/cat /flag into rm to get the system to give me the flag.

Also curious on if I can just replace the function of any command this way.
Tried doing this but idk can't seem to make it work. Anyways got the flag.
Flag:pwn.college{o0Skll06y542QLk6c8uvXSdaSps.ddzNyUDLzAzMykzW}
