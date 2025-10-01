# Perceiving Permissions

## 1. Changing File Ownership

### Solve
**Flag:** `pwn.college{01g3xHwKhIeG-i7CHAdpacGzXEr.QXxEjN0wiMwIzNzEzW}`

Had to change the ownership of /flag from root to hacker and then read it.
```
~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{01g3xHwKhIeG-i7CHAdpacGzXEr.QXxEjN0wiMwIzNzEzW}
```

### New Learnings
How to change file ownership with 'chown'.

## 2. Groups and Files

### Solve
**Flag:** `pwn.college{I3FDHCpXAhILBIqnOUJ2stnMJGa.QXxcjM1wiMwIzNzEzW}`

Had to change the group of /flag from root to hacker and hacker was not a part of the root group and then read it.
```
~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{I3FDHCpXAhILBIqnOUJ2stnMJGa.QXxcjM1wiMwIzNzEzW}
```

### New Learnings
How to change group using 'chgrp'. Multiple users can be part of a group.

## 3. Fun with groups names

### Solve
**Flag:** `pwn.college{cTv5nt7wF-YcY0dlB8V8F36nKME.QXycjM1wiMwIzNzEzW}`

Had to use 'id' command to find out the current group and then use 'chgrp' to change file ownership and then read the flag.
```
~$ id
uid=1000(hacker) gid=1000(grp4690) groups=1000(grp4690)
hacker@permissions~fun-with-groups-names:~$ chgrp grp4690 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{cTv5nt7wF-YcY0dlB8V8F36nKME.QXycjM1wiMwIzNzEzW}
```

### New Learnings
How to figure out current group using 'id' command.

## 4. Changing Permissions

### Solve
**Flag:** `pwn.college{gCxsb8Ac4jcUcV972DxXCxXiaBr.QXzcjM1wiMwIzNzEzW}`

Had to change the permissions of /flag to allow all users to read it using chmod and then read it using cat.
```
~$ ls -l /flag
-r-------- 1 root root 60 Oct  1 14:13 /flag
hacker@permissions~changing-permissions:~$ chmod o+r MODE /flag
chmod: cannot access 'MODE': No such file or directory
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{gCxsb8Ac4jcUcV972DxXCxXiaBr.QXzcjM1wiMwIzNzEzW}
```

### New Learnings
How to change file permissions using 'chmod'.

## 5. Executable files

### Solve
**Flag:** `pwn.college{QGypW6VqqE_olSJHiUHdSGjOSbL.QXyEjN0wiMwIzNzEzW}`

I checked the permissions of /challenge/run using 'ls -l' and saw that i need to make it executable by the user. I did that using chmod and then ran the program to get the flag.
```
~$ ls -l /challenge/run
-r--r--r-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{QGypW6VqqE_olSJHiUHdSGjOSbL.QXyEjN0wiMwIzNzEzW}
```

### New Learnings
How to change file permission to make it executable.

## 6. Permission Tweaking Practice

### Solve
**Flag:** `pwn.college{EOhT4Dz3T2PKA93Tus1ATtMWpTm.QXwEjN0wiMwIzNzEzW}`

Had to go through 8 rounds of permission resetting challenges for /challenge/pwn before i could make /flag file readable and then read it using cat.
```
~$ /challenge/run
~$ chmod a+rwx /challenge/pwn
:~$ chmod uo-r /challenge/pwn
~$ chmod uo-x /challenge/pwn
~$ chmod o+r /challenge/pwn
~$ chmod u+x /challenge/pwn
~$ chmod g-x /challenge/pwn
~$ chmod u-x,g-r,o-r /challenge/pwn
~$ chmod uo+rx /challenge/pwn
~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{EOhT4Dz3T2PKA93Tus1ATtMWpTm.QXwEjN0wiMwIzNzEzW}
```

### New Learnings
Extensive permission changing practice

## 7. Permissions Setting Practice

### Solve
**Flag:** `pwn.college{QPd6up4U7ypdzhovbLI0sBcO9z4.QXzETO0wiMwIzNzEzW}`

Had to go through 8 rounds of permission resetting challenges for /challenge/pwn before i could make /flag file readable and then read it using cat.

```
~$ /challenge/run
:~$ chmod g=rw,o=wx /challenge/pwn
~$ chmod u=w,o=x /challenge/pwn
~$ chmod u=r,g=r,o=w /challenge/pwn
~$ chmod u=-,g=rx,o=x /challenge/pwn
~$ chmod u=rwx,g=wx,o=w /challenge/pwn
~$ chmod u=wx,g=rw,o=w /challenge/pwn
~$ chmod u=x,g=r,o=rx /challenge/pwn
~$ chmod u=w,g=-,o=wx /challenge/pwn
~$ chmod a+r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{QPd6up4U7ypdzhovbLI0sBcO9z4.QXzETO0wiMwIzNzEzW}
```

### New Learnings
Extensive permission setting practice.

## 8. The SUID Bit

### Solve
**Flag:** `pwn.college{03pDhTVqHmxekAEC4Rr-nX3RjDo.QXzEjN0wiMwIzNzEzW}`

Had to set SUID bit for /challenge/getroot and then run it so that i could read /flag as root user.
```
~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~the-suid-bit:~$ cat /challenge/getroot
#!/opt/pwn.college/bash

fold -s <<< "SUCCESS! You have set the suid bit on this program, and it is running as root! Here is your shell..."
exec /bin/bash
hacker@permissions~the-suid-bit:~$ /bin/bash
hacker@permissions~the-suid-bit:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~the-suid-bit:~$ chmod a+r /flag
This challenge restricts chmod to ONLY work on /challenge/getroot! You may not 
chmod any other file in this challenge.
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# /flag
bash: /flag: Permission denied
root@permissions~the-suid-bit:~# cat /flag
pwn.college{03pDhTVqHmxekAEC4Rr-nX3RjDo.QXzEjN0wiMwIzNzEzW}
```

### New Learnings
How to set SUID bit for programs in order to run a program as respective file owner.

### References
```
https://www.youtube.com/watch?v=mdWa1SHkxmM&list=PL-ymxv0nOtqotjW-uK_YSj9pm5tTKf87J [Access Control]
https://www.youtube.com/watch?v=OGhKjwJ7PKE&list=PL-ymxv0nOtqotjW-uK_YSj9pm5tTKf87J [Implementing Access Control]
```
