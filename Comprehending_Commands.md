# Comprehending Commands

## 1.cat:not the pet,but the command

###Solve
**Flag:** `pwn.college{IBc9-juVIuXzQG44Z3Cyl6DZODd.QXxcTN0wiMwIzNzEzW}`

Had to use the cat command to print the contents of a file flag.
```~$ cat flag
pwn.college{IBc9-juVIuXzQG44Z3Cyl6DZODd.QXxcTN0wiMwIzNzEzW}
```

### New Learnings
How to use the cat command to read file contents.


## 2.catting absolute paths

###Solve
**Flag:** `pwn.college{4MxuEQOO8PK8vp3RnUs5RuAmaq4.QX5ETO0wiMwIzNzEzW}`

Had to read the file flag again but this time by specifying the absolute path.
```~$ cat /flag
pwn.college{4MxuEQOO8PK8vp3RnUs5RuAmaq4.QX5ETO0wiMwIzNzEzW}
```

### New Learnings
Absolute path can be specified to cat command to read a file.


## 3.more catting practise

###Solve
**Flag:** `pwn.college{AvV4ZjIsCbGvRLuwHSZR1F7RC4c.QXwITO0wiMwIzNzEzW}`

Had to use given absolute path to read a file in another directory without changing directory.
```~$ cat /lib/apache2/modules/flag
pwn.college{AvV4ZjIsCbGvRLuwHSZR1F7RC4c.QXwITO0wiMwIzNzEzW}
```

### New Learnings
More practise on using absolute paths with cat.


## 4.grepping for a needle in a haystack

###Solve
**Flag:** `pwn.college{UhX4n4n7zDYuPd7BRCYQsvpUrEY.QX3EDO0wiMwIzNzEzW}`

Used grep command on a given file to find the flag among thousands of line.
```~$ grep "pwn.college" /challenge/data.txt
pwn.college{UhX4n4n7zDYuPd7BRCYQsvpUrEY.QX3EDO0wiMwIzNzEzW}
```

### New Learnings
How to use the grep command.


## 5.comparing files

###Solve
**Flag:** `pwn.college{8avYFIQWS-hT34LMziAZVZOvcqN.01MwMDOxwiMwIzNzEzW}`

Had to use diff command to find the difference between a real and fake flag file. The difference was the real flag present in only one file. 
```~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
13a14
pwn.college{8avYFIQWS-hT34LMziAZVZOvcqN.01MwMDOxwiMwIzNzEzW}
```

### New Learnings
How to use the diff command.


## 6.listing files

###Solve
**Flag:** `pwn.college{4w_TvmsWoeoXFOwpMncIATSAGnU.QX4IDO0wiMwIzNzEzW}`

Had to list all the files inside given directory to find the flag file and then run it for the flag.
```~$ ls /challenge
30681-renamed-run-28447  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/30681-renamed-run-28447
Yahaha, you found me! Here is your flag:
pwn.college{4w_TvmsWoeoXFOwpMncIATSAGnU.QX4IDO0wiMwIzNzEzW}
```

### New Learnings
How to use ls command to list files in a directory.

## 7.touching files

###Solve
**Flag:** `pwn.college{g8QHcUQG0aqrZrZkop9DWKE6NDJ.QXwMDO0wiMwIzNzEzW}`

Had to create two files using the touch command and then run '/challenge/flag'.
```~$ touch /tmp/pwn /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{g8QHcUQG0aqrZrZkop9DWKE6NDJ.QXwMDO0wiMwIzNzEzW}
```

### New Learnings
How to use the touch command.

## 8.removing files

###Solve
**Flag:** `pwn.college{0_r-Ms2rymHYxk5JMreC6STeh7Y.QX2kDM1wiMwIzNzEzW}`

Had to delete a file and then run 'challenge/check'.
```~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{0_r-Ms2rymHYxk5JMreC6STeh7Y.QX2kDM1wiMwIzNzEzW}
```

### New Learnings
How to use the 'rm' command to delete files.

## 9.moving files

###Solve
**Flag:** `pwn.college{QdZrxXzGSu_P9ES8YLZqoPXdiGA.0VOxEzNxwiMwIzNzEzW}`

Had to move the flag file into another file and then run /challenge/check.
```~$ mv /flag /tmp/hack-the-planet
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{QdZrxXzGSu_P9ES8YLZqoPXdiGA.0VOxEzNxwiMwIzNzEzW}
```

### New Learnings
How move files using 'mv' command.

## 10.hidden files

###Solve
**Flag:** `pwn.college{YRu1Fppa_yWiL9_UHU9djhnNKZj.QXwUDO0wiMwIzNzEzW}`

Had to list all the files including hidden ones to look for the flag file and then read it using cat.
```~$ ls -a /
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-242091151025547  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-242091151025547
pwn.college{YRu1Fppa_yWiL9_UHU9djhnNKZj.QXwUDO0wiMwIzNzEzW}
```

### New Learnings
Listing hidden files using -a argument with ls.

## 11.An Epic Filesystem Quest

###Solve
**Flag:** `pwn.college{8cZ34SLddY3NjjnfHciH88HkDtq.QX5IDO0wiMwIzNzEzW}`

Had to extensively use ls,cd and cat to sleuth through different files and hints and eventually land at the correct flag file.
```~$ ls /
$ cat /WHISPER
$ ls -A | grep '^\.'
.
.
.
$ cat /usr/lib/python3/dist-packages/sage/cpython/__pycache__/SPOILER-TRAPPED
It is: pwn.college{8cZ34SLddY3NjjnfHciH88HkDtq.QX5IDO0wiMwIzNzEzW}
```

### New Learnings
Extensive pracise on the use of cat,ls and cd along with learning how to use grep with ls.

## 12.making directories

###Solve
**Flag:** `pwn.college{goQQQibNHxfWlWmc2KPRFUzh3b6.QXxMDO0wiMwIzNzEzW}`

Had to make a directory and create a file in it and then run /challenge/run for the flag.
```~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{goQQQibNHxfWlWmc2KPRFUzh3b6.QXxMDO0wiMwIzNzEzW}
```

### New Learnings
How to make a directory using mkdir.


## 13.finding files

###Solve
**Flag:** `pwn.college{Qg5t1UHLHcXJb4sfzyub1R3N76q.QXyMDO0wiMwIzNzEzW}`

Had to search for all files with the name flag in the system and read them one by one with cat to find the flag.
```~$ find / -name flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX-Web/Misc/Regular/flag
hacker@commands~finding-files:~$ cat /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX-Web/Misc/Regular/flag
pwn.college{Qg5t1UHLHcXJb4sfzyub1R3N76q.QXyMDO0wiMwIzNzEzW}
```

### New Learnings
Using 'find' command and its arguments to find files in the system.

## 14.linking files

###Solve
**Flag:** `pwn.college{A4YLajne6Du6EzhY6vRL9_GVzqz.QX5ETN1wiMwIzNzEzW}`

Tried to read the flag file but permission denied. Then deleted given file to estabilish a symbolic link between it and the flag file and ran /challenge/catflag which is printing contents of /home/hacker/not-the-flag which is linked to /flag. Therefore it printed the correct flag.
```~$ cat /home/hacker/not-the-flag
cat: /home/hacker/not-the-flag: Permission denied
hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ cat /challenge/catflag
#!/opt/pwn.college/bash
fold -s <<< "About to read out the /home/hacker/not-the-flag file!"
cat /home/hacker/not-the-flag
hacker@commands~linking-files:~$ file /home/hacker/not-the-flag
/home/hacker/not-the-flag: symbolic link to /flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{A4YLajne6Du6EzhY6vRL9_GVzqz.QX5ETN1wiMwIzNzEzW}
```

### New Learnings
The concepts of hard and soft/symbolic links which allow multiple adresses to point to the same file.

### References 
None
