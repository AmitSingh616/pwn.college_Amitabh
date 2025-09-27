# Digesting Documentation

## 1. Learning from Documentation

###Solve
**Flag:** `pwn.college{oH0k_cmUp2md0VYt78PeJragcR_.QX0ITO0wiMwIzNzEzW}`

Had to specify an argument --givename to the program /challenge/challenge to get the correct flag.
```
~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{oH0k_cmUp2md0VYt78PeJragcR_.QX0ITO0wiMwIzNzEzW}
```

### New Learnings
Any program can have arguemnts that allow for better usage of said programs.


## 2. Learning Complex Usage

###Solve
**Flag:** `pwn.college{w9L4RqzA8IINy1rWnFGFVyRpdfd.QX1ITO0wiMwIzNzEzW}`

Had to use complex argument (argument --printfile with path parameter) to print the flag contained in /flag.
```
~$ ls /challenge
~$ /challenge/challenge --printfile /challenge/challenge
~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{w9L4RqzA8IINy1rWnFGFVyRpdfd.QX1ITO0wiMwIzNzEzW}
```

### New Learnings
How to use complex arguments.


## 3. Reading Manuals

###Solve
**Flag:** `pwn.college{wI9XTmd_DZJonOuwzqlJZDmu-fF.QX0EDO0wiMwIzNzEzW}`

Had to access the manual of a command to figure out what argument to use to access flag in challenge directory.
```
~$ man challenge
hacker@man~reading-manuals:~$ /challenge --wmdonu 900
bash: /challenge: Is a directory
hacker@man~reading-manuals:~$ /challenge/challenge --wmdonu 900
Correct usage! Your flag: pwn.college{wI9XTmd_DZJonOuwzqlJZDmu-fF.QX0EDO0wiMwIzNzEzW}
```

### New Learnings
How to open manuals for different  commands.


## 4. Searching Manuals

###Solve
**Flag:** `pwn.college{w6YHb2hi-rFqn_8u-r0nkHWTWT4.QX1EDO0wiMwIzNzEzW}`

Had to open the manual of challenge command and navigate it to find arguments that will give the flag using 'n','/' and 'N'.
```
~$ man challenge
hacker@man~searching-manuals:~$ 
hacker@man~searching-manuals:~$ /challenge/challenge --zw
Initializing...
Correct usage! Your flag: pwn.college{w6YHb2hi-rFqn_8u-r0nkHWTWT4.QX1EDO0wiMwIzNzEzW}
```

### New Learnings
How to navigate a command manual for specific arguments.


## 5. Searching for Manuals

###Solve
**Flag:** `pwn.college{sCq0mM8N7mmrTYnzlSaWA6wCiZ1.QX2EDO0wiMwIzNzEzW}`

Had to search the manual for man command to find the argument that lets you search for a specific manual. Found the manual using -k and then opened to check the argument needed for flag.
```
~$ man man
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ man -k challenge
sqmmmrnzla (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man sqmmmrnzla
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ /challenge/challenge --sqmmmr 087
Correct usage! Your flag: pwn.college{sCq0mM8N7mmrTYnzlSaWA6wCiZ1.QX2EDO0wiMwIzNzEzW}
```

### New Learnings
How to look for a hidden manual. The man command also has its own manual.

## 6. Helpful Programs

###Solve
**Flag:** `pwn.college{s8RO_l3pifxQm4LK2t-dplQbpRQ.QX3IDO0wiMwIzNzEzW}`

Had to invoke help command to look for the argument needed for flag.
```
~$ challenge --help
bash: challenge: command not found
hacker@man~helpful-programs:~$ /challenge/challenge --help
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 834
hacker@man~helpful-programs:~$ /challenge/challenge -g 834
Correct usage! Your flag: pwn.college{s8RO_l3pifxQm4LK2t-dplQbpRQ.QX3IDO0wiMwIzNzEzW}
```

### New Learnings
How to use help argument in case the program doesn't have a manual.

 
## 7. Help for Builtins

###Solve
**Flag:** `pwn.college{04OuyrPI7nyNl2e6Iv0n6PrxJuW.QX0ETO0wiMwIzNzEzW}`

Had to use help for a builtin command to get instructions on how to get the flag.
```
~$ help challenge
hacker@man~help-for-builtins:~$ challenge --secret 04OuyrPI
Correct! Here is your flag!
pwn.college{04OuyrPI7nyNl2e6Iv0n6PrxJuW.QX0ETO0wiMwIzNzEzW}
```

### New Learnings
How to use help for builtins.

##References
`https://man7.org/linux/man-pages/`
