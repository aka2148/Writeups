# Bandit wargames writeup

## Level 0
Just connecting to the game through SSH. No problems.

## Level 0-1
Use ls to find the readme file and cat it to get the flag

## Level 1-2
Same as above only file name is different

## Level 2-3
Use / to indicate spaces in the filename and get the flag.

## Level 3-4
Use ls -alps to see the hidden file. Cat it and you get the flag

## Level 4-5
Use find command with find -type f | xargs file. Had to get help on this one. Wasn't able to do it with the commands they had listed.

## Level 5-6
Use find command with the -size argument. Also add ! -executable since the file cannot be executed.

## Level 6-7
Find / to search the entire system arguments needed are user, group, and size.

## Level 7-8
Use the strings command with grep. Strings data.txt | grep 'millionth'

## Level 8-9
We use the uniq command. uniq data.txt or uniq -c data.txt to get the count are both fine.

## Level 9-10
Similar to level 7 strings data.txt | grep '=='. Use 2 = as task specifies multiple preceding it.

## Level 10-11
Use base64 to decode. base64 -d data.txt.

## Level 11-12
I don't know if it was possible to do it without external application but I used Cyberchef and the rot13 option to get the flag.
