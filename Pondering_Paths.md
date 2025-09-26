# Pondering Paths

## 1. The Root

### Solve
**Flag:** `pwn.college{AxZOPICDftIH70rxrubwKz3YIo8.QX4cTO0wiMwIzNzEzW}`

Had to give the absolute path to a program pwn in order to run it which gave the flag. Below are all the commands written and outputs produced on the terminal.
```
~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{AxZOPICDftIH70rxrubwKz3YIo8.QX4cTO0wiMwIzNzEzW}
```


## 2. Program and absolute paths

### Solve
**Flag:** `pwn.college{Mrww6GJNHzbR_n4lpAdct4rqpq2.QX1QTN0wiMwIzNzEzW}`

Had to type a longer absolute path /challenge/run in order to execute the program named 'run' and obtain the flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{Mrww6GJNHzbR_n4lpAdct4rqpq2.QX1QTN0wiMwIzNzEzW}
```


## 3. Position thy self

### Solve
**Flag:** `pwn.college{Q7U9HEETMUXXa8B4n8OjNEg8w_l.QX2QTN0wiMwIzNzEzW}`

Had to navigate to a given directory and execute the program 'run' again and obtain the flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ /challenge/run
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-thy-self:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Q7U9HEETMUXXa8B4n8OjNEg8w_l.QX2QTN0wiMwIzNzEzW}
```


## 4. Position elsewhere

### Solve
**Flag:** `pwn.college{0TRo_Mhfkgke4r6SH1eKamjoJUv.QX3QTN0wiMwIzNzEzW}`

Had to navigate to a given directory and execute the program 'run' again to get the flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ /challenge/run
Incorrect...
You are not currently in the /proc/138 directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /proc/138
hacker@paths~position-elsewhere:/proc/138$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{0TRo_Mhfkgke4r6SH1eKamjoJUv.QX3QTN0wiMwIzNzEzW}
```


## 5. Position yet elsewhere

### Solve
**Flag:** `pwn.college{AtzJD0wPBQqI9Ag3ummdiLFsG8D.QX4QTN0wiMwIzNzEzW}`

Had to navigate to a given directory and execute the program 'run' again to show absolute path is independent of current directory to obtain the flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ /challenge/run
Incorrect...
You are not currently in the /tmp directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /tmp
hacker@paths~position-yet-elsewhere:/tmp$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AtzJD0wPBQqI9Ag3ummdiLFsG8D.QX4QTN0wiMwIzNzEzW}
```


## 6. implicit relative paths,from /

### Solve
**Flag:** `pwn.college{omh28g5Zmm8_MIWHoqpghnrA-IO.QX5QTN0wiMwIzNzEzW}`

Used a relative path syntax to run a program by not speicifying initial directory program is stored in to obtain the flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{omh28g5Zmm8_MIWHoqpghnrA-IO.QX5QTN0wiMwIzNzEzW}
```


## 7. explicit relative paths,from /

### Solve
**Flag:** `pwn.college{8h8b3f3rkIn6ILgJBYJN5daK2nr.QXwUTN0wiMwIzNzEzW}`

Had to use '.' implicity entry to refer to current directory '/' in relative path in order to obtain flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ ./challenge/run
bash: ./challenge/run: No such file or directory
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8h8b3f3rkIn6ILgJBYJN5daK2nr.QXwUTN0wiMwIzNzEzW}
```


## 8. implicit relative path

### Solve
**Flag:** `pwn.college{EN6Vw_ZlmM3Zl4BAQZaCfGL1XR0.QXxUTN0wiMwIzNzEzW}`

Had to use implict entry '.' to execute correct file as naked path doesn't run in order to obtain flag. Below are all the commands written and outputs produced on the terminal.

```
:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{EN6Vw_ZlmM3Zl4BAQZaCfGL1XR0.QXxUTN0wiMwIzNzEzW}
```


## 9. home sweet home

### Solve
**Flag:** `pwn.college{co-w7VWv4DkESapEownQriL7cG4.QXzMDO0wiMwIzNzEzW}`

Had to provide an explicit path under 3 characters to a directory under '/home/hacker' where the copy of the flag would be received. Below are all the commands written and outputs produced on the terminal.

```
:~$ cd /
hacker@paths~home-sweet-home:/$ challenge/run ~/asdf
The argument you provided must not have been longer than 3 characters (it's 
currently 6 characters long)!
hacker@paths~home-sweet-home:/$ challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{co-w7VWv4DkESapEownQriL7cG4.QXzMDO0wiMwIzNzEzW}
```


### New Learnings
How to use 'cd' to change current directory. Absolute paths are not affected by current directory. How to write relative paths. Using '.' to refer to current directory and '~' to refer to home directory where most files are stored.


### References 
None
