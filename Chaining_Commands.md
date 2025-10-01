# Chaining Commands

## 1. Chaining with semicolons

### Solve
**Flag:** `pwn.college{QQYcRDnA5G6_E1BYcTsP3LR_G5T.QX1UDO0wiMwIzNzEzW}`

Had to chain together two given commands with ; to get the flag.
```
~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{QQYcRDnA5G6_E1BYcTsP3LR_G5T.QX1UDO0wiMwIzNzEzW}
```
### New Learnings
How to chain commands with ';'.

## 2. Building on Success

### Solve
**Flag:** `pwn.college{QJ3hDlJ1HcbKr8M0LjjbevPgRDO.0lM0MDOxwiMwIzNzEzW}`

Had to chain together two given commands with && to get the flag. This meant the second command would run only if the first was successful.
```
~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{QJ3hDlJ1HcbKr8M0LjjbevPgRDO.0lM0MDOxwiMwIzNzEzW}
```
### New Learnings
How to conditionally chain commands using '&&'.

## 3. Handling Failure

### Solve
**Flag:** `pwn.college{Al2F__t24WrZm1xkcd-DUcNAPrF.01M0MDOxwiMwIzNzEzW}`

Had to chain together two given commands with || to get the flag. This meant the second command would run only if the first failed.
```
~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{Al2F__t24WrZm1xkcd-DUcNAPrF.01M0MDOxwiMwIzNzEzW}
```
### New Learnings
How to conditionally chain commands using '||'.

## 4. Your first shell script

### Solve
**Flag:** `pwn.college{coB1SefpqmsQ-lUTGkK-QEiOJb9.QXxcDO0wiMwIzNzEzW}`

Had to create a file x.sh using touch and then write /challenge/college and /challenge/pwn to it using echo and then run the shell script using 'bash x.sh'.
```
~$ touch x.sh
~$ echo /challenge/pwn > x.sh
hacker@chaining~your-first-shell-script:~$ echo /challenge/college > x.sh
hacker@chaining~your-first-shell-script:~$ cat x.sh
/challenge/college
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh
hacker@chaining~your-first-shell-script:~$ echo /challenge/college >> x.sh
hacker@chaining~your-first-shell-script:~$ cat x.sh
/challenge/pwn
/challenge/college
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{coB1SefpqmsQ-lUTGkK-QEiOJb9.QXxcDO0wiMwIzNzEzW}
```
### New Learnings
How to create and run a shell script.

## 5. Redirecting Script output

### Solve
**Flag:** `pwn.college{Ems6V5AnE29GsMV7nuU73NerInH.QX4ETO0wiMwIzNzEzW}`

Similar to the last challenge i had to write a script but this time the output had to be redirected (piped using |) to another program to get the flag.
```
~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ echo /challenge/pwn > x.sh
hacker@chaining~redirecting-script-output:~$ echo /challenge/college >> x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{Ems6V5AnE29GsMV7nuU73NerInH.QX4ETO0wiMwIzNzEzW}
```
### New Learnings
Outputs of scripts can also be piped just like any other command.

## 6. Executable Shell Scripts

### Solve
**Flag:** `pwn.college{c91O8SqQ-CGQO1_cfIBtJzmqoWD.QX0cjM1wiMwIzNzEzW}`

Had to create a shell script in my home directory containing /challenge/solve. Then set its permissions to executable using 'chmod' and then run it directly. Used ls -l  and cat to make sure permissions and file contents of the shell script were correct.
```
~$ cd ~
hacker@chaining~executable-shell-scripts:~$ touch script.sh
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > script.sh
hacker@chaining~executable-shell-scripts:~$ chmod a+x script.sh
hacker@chaining~executable-shell-scripts:~$ ls -l script.sh
-rwxr-xr-x 1 hacker hacker 17 Oct  1 15:43 script.sh
hacker@chaining~executable-shell-scripts:~$ cat script.sh
/challenge/solve
hacker@chaining~executable-shell-scripts:~$ script.sh
bash: script.sh: command not found
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{c91O8SqQ-CGQO1_cfIBtJzmqoWD.QX0cjM1wiMwIzNzEzW}
```

### New Learnings
How to run a shell script without using bash.

## 7. Understanding Shebangs

### Solve
**Flag:** ` pwn.college{g5_Bix8QWQqVsmcvCHDsZkorh66.0VOzMDOxwiMwIzNzEzW}`

Had to set the shebang #!/bin/bash for the script solve to eliminate the need to use '.sh' extension. The had to write echo "hack the planet" to the script and set permissions to executable to get the output. Running /challenge/run would verify the output and give flag. 
```
~$ echo '#!/bin/bash' > solve.sh
hacker@chaining~understanding-shebangs:~$ printf "hack the planet" >> solve.sh
hacker@chaining~understanding-shebangs:~$ cat solve.sh
#!/bin/bash
hack the planethacker@chaining~understanding-shebangs:~$ chmod a+x solve.sh
hacker@chaining~understanding-shebangs:~$ ~/solve.sh
/home/hacker/solve.sh: line 2: hack: command not found
hacker@chaining~understanding-shebangs:~$ echo "hack the planet"
hack the planet
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Your script did not give the expected output.
Expected: hack the planet
Got: 
hacker@chaining~understanding-shebangs:~$ echo '#!/bin/bash' > solve.sh
hacker@chaining~understanding-shebangs:~$ echo "hack that planet" >> solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Your script did not give the expected output.
Expected: hack the planet
Got: 
hacker@chaining~understanding-shebangs:~$ echo echo "hack the planet" >> solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{g5_Bix8QWQqVsmcvCHDsZkorh66.0VOzMDOxwiMwIzNzEzW}

```
### New Learnings
How to set shebangs for files to eliminate extensions.

## 8. Scripting with Arguments

### Solve
**Flag:** `pwn.college{U1eJxWur6iESIkCZBZuPS9d5USU.0VNzMDOxwiMwIzNzEzW}`

Had to write a command that accepts arguments in reverse order into the shell script and then pass arguments and run /challenge/run to verify that the script executes as required and get the flag.
```
~$ echo 'echo $2 $1' > solve.sh
hacker@chaining~scripting-with-arguments:~$ cat solve.sh
echo $2 $1
hacker@chaining~scripting-with-arguments:~$ bash solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{U1eJxWur6iESIkCZBZuPS9d5USU.0VNzMDOxwiMwIzNzEzW}
```
### New Learnings
How to pass arguments to shell scripts.

## 9. Scripting with Conditionals

### Solve
**Flag:** `pwn.college{MJ3Za5kbywnsvMMhOurVQrSn5MN.0lNzMDOxwiMwIzNzEzW}`

Had to write a conditional into a script that would print "college" for the argument "pwn" and nothing for any other argument. Then had to run /challenge/run to verify if the script did as required and get flag. The condition was implemented with an 'if' statement.
```
~$ echo if [ "$1" == "pwn" ] > solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo then >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo echo "college" >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo fi >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ cat solve.sh
if [  == pwn ]
then
echo college
fi
hacker@chaining~scripting-with-conditionals:~$ echo if [ '$1' == "pwn" ] > solve.sh
hacker@chaining~scripting-with-conditionals:~$ cat solve.sh
if [ $1 == pwn ]
hacker@chaining~scripting-with-conditionals:~$ echo then >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo echo "college" >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo fi >> solve.sh
hacker@chaining~scripting-with-conditionals:~$ cat solve.sh
if [ $1 == pwn ]
then
echo college
fi
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{MJ3Za5kbywnsvMMhOurVQrSn5MN.0lNzMDOxwiMwIzNzEzW}
```
### New Learnings
How to write conditional statements in bash.

## 10. Scripting with Default Case

### Solve
**Flag:** `pwn.college{Eev0-AqmIc-bChFGjHEcUWa6Y03.01NzMDOxwiMwIzNzEzW}`

Had to write a conditional into a script that prints "college" when argument is "pwn" and nope for anything else. Accomplished using an if-else block and then ran /challenge/run to get the flag.
```
~$ echo -e "if [ '$1' == "pwn" ]\nthen\n  echo college\nelse\n echo nope\nfi" > solve.sh
hacker@chaining~scripting-with-default-cases:~$ cat solve.sh
if [ '' == pwn ]
then
  echo college
else
 echo nope
fi
hacker@chaining~scripting-with-default-cases:~$ echo -e "if [ '\$1' == "pwn" ]\nthen\n  echo college\nelse\n echo nope\nfi" > solve.sh
hacker@chaining~scripting-with-default-cases:~$ cat solve.sh
if [ '$1' == pwn ]
then
  echo college
else
 echo nope
fi
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Test failed for input 'pwn'
Expected: 'college'
Got: 'nope'
hacker@chaining~scripting-with-default-cases:~$ echo -e 'if [ "$1" == "pwn" ]\nthen\n  echo college\nelse\n echo nope\nfi' > solve.sh
hacker@chaining~scripting-with-default-cases:~$ cat solve.sh
if [ "$1" == "pwn" ]
then
  echo college
else
 echo nope
fi
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{Eev0-AqmIc-bChFGjHEcUWa6Y03.01NzMDOxwiMwIzNzEzW}
```
### New Learnings
How to use else along with if block.

## 11. Scripting with Multiple Conditions

### Solve
**Flag:** `pwn.college{gPKV_MhQRHl8twKueUx6wZ1BCKT.0FOzMDOxwiMwIzNzEzW}`

Had to write a else-if ladder conditional block in the script and run /challenge/run to see if all conditions were met. If yes then /challenge/run gave me the flag.
```
~$ echo -e 'if [ "$1" == "hack" ]\nthen\n echo "the planet"\nelif [ "$1" == "pwn" ]\nthen\n echo "college"\nelif [ "$1" == "learn" ]\nthen\n echo "linux"\nelse\n echo "unknown"\nfi' > solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{gPKV_MhQRHl8twKueUx6wZ1BCKT.0FOzMDOxwiMwIzNzEzW}
```
### New Learnings
How to write else-if block in bash.

## 12. Reading Shell Scripts

### Solve
**Flag:** `pwn.college{UO4XJa4weqOEK131JKghj4shuBz.0lMwgDOxwiMwIzNzEzW}`

Had to read the script to find the correct password and then enter the password when running /challenge/run.
```
~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run hack the PLANET

Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ /challenge/run hack the PLANET

Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{UO4XJa4weqOEK131JKghj4shuBz.0lMwgDOxwiMwIzNzEzW}
```
### New Learnings
How to read scripts for clues.

### References
`https://www.youtube.com/watch?v=tK9Oc6AEnR4' [bash scripting basics]
