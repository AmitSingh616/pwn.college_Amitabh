# Shell Variables

## 1. Printing Variables

### Solve
**Flag:** `pwn.college{g0qpjXZ0gEIcxrI9qB2WoUiKkNf.QX3UTN0wiMwIzNzEzW}`

Had to print a variable containing the flag using echo $"<variable_name>.
```
~$ echo $FLAG
pwn.college{g0qpjXZ0gEIcxrI9qB2WoUiKkNf.QX3UTN0wiMwIzNzEzW}
```

### New Learnings
How to print variables to terminal using echo $.

## 2. Setting Variables

### Solve
**Flag:** `pwn.college{0Nw2oG8dR6AdI7u7spaWCP9ITpa.QX5UTN0wiMwIzNzEzW}`

Had to set the value of variable PWN to COLLEGE.
```
~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{0Nw2oG8dR6AdI7u7spaWCP9ITpa.QX5UTN0wiMwIzNzEzW}
```

### New Learnings
How to set variable values.

## 3. Multi-word variables

### Solve
**Flag:** `pwn.college{MmPvNEULn_8eHwPClsFhYpVHsSi.QXwYTN0wiMwIzNzEzW}`

Had to set the variable PWN to the multi word value "COLLEGE YEAH".
```
~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MmPvNEULn_8eHwPClsFhYpVHsSi.QXwYTN0wiMwIzNzEzW}
```

### New Learnings
How to give variables multi-word values.

## 4. Exporting Variables

### Solve
**Flag:** `pwn.college{M51hvF3kCNpj1agGbch55nOjWm1.QXyYTN0wiMwIzNzEzW}`

Had to set the values of two variables and export PWN but not export college. The i had to run /challenge/run with PWN as a parameter in a child shell to get the flag.
```
~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run PWN
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{M51hvF3kCNpj1agGbch55nOjWm1.QXyYTN0wiMwIzNzEzW}
```

### New Learnings
How to export variables to other processes.

## 5. Printing exported variables

### Solve
**Flag:** `pwn.college{wS89z9AqEcmGOXSf__htScaCP_l.QX4UTN0wiMwIzNzEzW}`

Had to simply run the env command to print out the list of exported variables which included the flag.
```
~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=83e803ad0b392ea33dae66f998c9e21fa6890ae3e2bf824436b0648ffaf45d6a
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{wS89z9AqEcmGOXSf__htScaCP_l.QX4UTN0wiMwIzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

### New Learnings
How to print vales of all exported variables using 'env'.

## 6. Storing command output

### Solve
**Flag:** `pwn.college{gkti6nBq0exsktv3WtRS05wiRWp.QX1cDN1wiMwIzNzEzW}`

Had to store the value given my running the command /challenge/run in variable PWN and the print out the flag.
```
~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{gkti6nBq0exsktv3WtRS05wiRWp.QX1cDN1wiMwIzNzEzW}
```

### New Learnings
How to store command outputs in variables.

## 7. Reading Input

### Solve
**Flag:** `pwn.college{ch4nfh8FEGTSSLlTPyybvmfba7c.QX4cTN0wiMwIzNzEzW}`

Had to read the value COLLEGE into a variable PWN using 'read'.
```
~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{ch4nfh8FEGTSSLlTPyybvmfba7c.QX4cTN0wiMwIzNzEzW}
```

### New Learnings
How to read values into a variable from the user.

## 8. Reading Files

### Solve
**Flag:** `pwn.college{wMIht2MJ9URqTK_DjzWc-Qfltkd.QXwIDO0wiMwIzNzEzW}`

Had to read a file into the variable PWN using '<' and 'read'.
```
~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wMIht2MJ9URqTK_DjzWc-Qfltkd.QXwIDO0wiMwIzNzEzW}
```

### New Learnings
How to read a file into a variable

### References
NONE