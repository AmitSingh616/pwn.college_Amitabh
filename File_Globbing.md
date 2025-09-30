# File Globbing

## 1. Matching with *

### Solve
**Flag:** `pwn.college{cc02-0paK-iefDaf9yj4l9gqDd3.QXxIDO0wiMwIzNzEzW}`

Had to navigate to /challenge directory using only 4 characters by applying '*' and then run /challenge/run.
```
~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cc02-0paK-iefDaf9yj4l9gqDd3.QXxIDO0wiMwIzNzEzW}
```

### New Learnings
How to use globbing tool '*'(multiple characters) to match arguments.


## 2. Matching with ?

### Solve
**Flag:** `pwn.college{cLl8yTNXgr_47dIWWBA-0ghWf-G.QXyIDO0wiMwIzNzEzW}`

Had to navigate to correct directory using ? in place of specific characters and the run a program to get flag.
```
~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cLl8yTNXgr_47dIWWBA-0ghWf-G.QXyIDO0wiMwIzNzEzW}
```

### New Learnings
How to use globbing tool '?'(one character at a time) to match arguments.


## 3. Matching with []

### Solve
**Flag:** `pwn.college{g1arLNTt9MtUJBUoNO05zECbNDH.QXzIDO0wiMwIzNzEzW}`

Had to navigate to a given directory and then use '[]' to pass an argument to /challenge/run and get the flag.
```
~$ cd /challenge/files
:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{g1arLNTt9MtUJBUoNO05zECbNDH.QXzIDO0wiMwIzNzEzW}
```

### New Learnings
How to use globbing tool '[]'.


## 4. Matching paths with []

### Solve
**Flag:** `pwn.college{8QcjGOpetSLmotEN3hEy4y4NFSK.QX0IDO0wiMwIzNzEzW}`

Had to run /challenge/run directly from home directory and pass an argument using globbing and absolute path.
```
~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{8QcjGOpetSLmotEN3hEy4y4NFSK.QX0IDO0wiMwIzNzEzW}
```

### New Learnings
How to write globbed absolute paths.


## 5. Multiple Globs

### Solve
**Flag:** `pwn.college{QscpiCeVN2WrPz6dpgRzM5_Fy2D.0lM3kjNxwiMwIzNzEzW}`

Had to run /challenge/run with a parameter such that it was no longer than 3 characters and used multiples globs '*' to cover every file name that contained the letter p.
```
~$ cd /challenge/files
$ ls
$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{QscpiCeVN2WrPz6dpgRzM5_Fy2D.0lM3kjNxwiMwIzNzEzW}
```

### New Learnings
How to use multiple globs '*'.


## 6. Mixing Globs

### Solve
**Flag:** `pwn.college{ssnFzJai7olf4hK2j_Cb0kDJirj.QX1IDO0wiMwIzNzEzW}`

Had to use different globbing tools to specify correct files and run them to get the flag. I used [cep] to specify files starting with c,e or p and then * to fill in the rest of it as ls command showed me that only one file starts with each letter.
```
~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{ssnFzJai7olf4hK2j_Cb0kDJirj.QX1IDO0wiMwIzNzEzW}
```

### New Learnings
How to mix multiple different globbing tools in same argument.


## 7. Exclusionary globbing

### Solve
**Flag:** `pwn.college{ITZAqshDzhSclfu0mVjMV1q4kj6.QX2IDO0wiMwIzNzEzW}`

Had to run /challenge/files with all those files not starting with p, w or n. Used [!pwn] to exclude files starting with p, w or n and * to specify variable length of file name.
```
~$ cd /challenge/files
/challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{ITZAqshDzhSclfu0mVjMV1q4kj6.QX2IDO0wiMwIzNzEzW}
```

### New Learnings
How to exclude certain files using globbing tool '[]'.


## 8. Tab completion

### Solve
**Flag:** `pwn.college{E7nw8Wtm1UZk7J64Ib7Um0RBhrn.0FN0EzNxwiMwIzNzEzW}`

On pressing <TAB> bash will attempt to autocomplete what you were trying to type. Its a safer alternative than * to prevent unwanted files from running. I simply had to click TAB to complete a given path and get the flag.
```
~$ cat /challenge/pwn<TAB>(filled with college)
pwn.college{E7nw8Wtm1UZk7J64Ib7Um0RBhrn.0FN0EzNxwiMwIzNzEzW}
```

### New Learnings
<TAB> can be used to autocomplete commands.


## 9. Multiple options for tab completion

### Solve
**Flag:** `pwn.college{I3-WX570utiKVEYOrVkULBIhP4z.0lN0EzNxwiMwIzNzEzW}`

Had to use <TAB> completion to look for files named pwncollege-" " and try to read them one by one to find the flag.
```
~$ cd /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files/pwn
bash: cd: /challenge/files/pwn: Not a directory
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files/pwncollege-
pwncollege-family      pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:~$ cat  /challenge/files/pwncollege-flag
pwn.college{I3-WX570utiKVEYOrVkULBIhP4z.0lN0EzNxwiMwIzNzEzW}
```

### New Learnings
Extensive practice of <TAB> completion.


## 10. Tab completion on commands

### Solve
**Flag:** `pwn.college{Izl060wBLOE07ykMahKYUnaYYXM.0VN0EzNxwiMwIzNzEzW}`

Had to use <TAB> completion to complete a given command and run it for the flag.
```
:~$ pwncollege-22991 
Correct! Here is your flag:
pwn.college{Izl060wBLOE07ykMahKYUnaYYXM.0VN0EzNxwiMwIzNzEzW}
```

### New Learnings
<TAB> completion can also be used with commands not just files or paths.


### References
None