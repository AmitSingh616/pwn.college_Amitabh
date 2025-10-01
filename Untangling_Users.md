# Untangling Users

## 1. Becoming root with su

### Solve
**Flag:** `pwn.college{4eWKXNcVROJtzwg6kRSf1Ooz3ne.QX1UDN1wiMwIzNzEzW}`

Had to become the root user with 'su' using a given password and read the flag.
```
~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{4eWKXNcVROJtzwg6kRSf1Ooz3ne.QX1UDN1wiMwIzNzEzW}
```

### New Learnings
How to become root user with 'su'.

## 2. Other users with su

### Solve
**Flag:** `pwn.college{UlPyVtN68inv8qnW3EnIk2xGc3v.QX2UDN1wiMwIzNzEzW}`

Had to switch to user 'zardus' using su and a given password and then run /challenge/run to get the flag.
```
~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{UlPyVtN68inv8qnW3EnIk2xGc3v.QX2UDN1wiMwIzNzEzW}
```

### New Learnings
How to switch the non-root user using 'su'.

## 3. Cracking passwords

### Solve
**Flag:** `pwn.college{wUAO9XrYcMbxXkn-b0GZ6SxufRA.QX3UDN1wiMwIzNzEzW}`

Tried to run /challenge/shadow-leak but was denied permission. Ran the same with 'john' and it started a process. On process termination i used 'show' argument to see the passwords cracked by john which revealed the password for 'zardus'. I switched to zardus using su and ran /challenge/run for the flag.
```
~$ head -n 5 /challenge/shadow-leak
root:*:20182:0:99999:7:::
daemon:*:20182:0:99999:7:::
bin:*:20182:0:99999:7:::
sys:*:20182:0:99999:7:::
sync:*:20182:0:99999:7:::
hacker@users~cracking-passwords:~$ john --version
Created directory: /home/hacker/.john
Unknown option: "--version"
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:04 54% 1/3 0g/s 283.7p/s 283.7c/s 283.7C/s zrdus..zardus9999994
0g 0:00:00:07 76% 1/3 0g/s 284.7p/s 284.7c/s 284.7C/s 9999945..Z9999932
0g 0:00:00:09 93% 1/3 0g/s 283.5p/s 283.5c/s 283.5C/s zardus999992002..zardus1963
0g 0:00:00:14 0% 2/3 0g/s 285.0p/s 285.0c/s 285.0C/s serena..88888888
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04916g/s 286.2p/s 286.2c/s 286.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ john --show /challenge/shadow-leak
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20362:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wUAO9XrYcMbxXkn-b0GZ6SxufRA.QX3UDN1wiMwIzNzEzW}
```

### New Learnings
How to crack passwords to switch users.

## 4. Using sudo

### Solve
**Flag:** `pwn.college{0nZMUCyc2y8MteU0-7d7q5CbGFt.QX4UDN1wiMwIzNzEzW}`

Had to use sudo to read /flag with root user permissions.
```
~$ sudo cat /flag
pwn.college{0nZMUCyc2y8MteU0-7d7q5CbGFt.QX4UDN1wiMwIzNzEzW}
```

### New Learnings
How to use sudo to run commands as root user.

### References
NONE
