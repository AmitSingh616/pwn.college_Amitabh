# Practicing Piping

## 1. Redirecting Output

### Solve
**Flag:** `pwn.college{8XNJR6vgOhEdkr6OG8DF5oKrWMB.QX0YTN0wiMwIzNzEzW}`

Had to redirect the output of echo to a different file using '>'.
```
~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{8XNJR6vgOhEdkr6OG8DF5oKrWMB.QX0YTN0wiMwIzNzEzW}
```

### New Learnings
How to redirect output of echo command.

## 2. Redirecting more output

### Solve
**Flag:** `pwn.college{w18mlSoCBLdJ6xjTKGyBUfh-bPz.QX1YTN0wiMwIzNzEzW}`

Had to write the output of a command to a file myflag and then read it to get the output.
```
~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{w18mlSoCBLdJ6xjTKGyBUfh-bPz.QX1YTN0wiMwIzNzEzW}
```

### New Learnings
How to write the output of any command to a file.

## 3. Appending output

### Solve
**Flag:** `pwn.college{QlN1fFLmACLzbcOwRZwd10GO_1Y.QX3ATO0wiMwIzNzEzW}`

Had to redirect the flag to a given file. The flag was split into two halves to make sure that we use append '>>' to redirect and not '>'. If append was correctly use then we can read the flag.
```
~$ /challenge/run >> /home/hacker/the-flag
~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{QlN1fFLmACLzbcOwRZwd10GO_1Y.QX3ATO0wiMwIzNzEzW}
                              ^
     that is the second half /|\
                              |

```

### New Learnings
How to use append '>>' to write multiple outputs to the same file.

## 4. Redirecting Errors

### Solve
**Flag:** `pwn.college{YBpxYorHFqW67HMBXnv7wAugnNX.QX3YTN0wiMwIzNzEzW}`

Used modified '>' to redirect both error and output to different files and then read the flag.
```
~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{YBpxYorHFqW67HMBXnv7wAugnNX.QX3YTN0wiMwIzNzEzW}
```

### New Learnings
How to redirect error using '2>'.

## 5. Redirecting Inputs

### Solve
**Flag:** `pwn.college{s7KChO2d0G2R9jGVgNJSalPFRvy.QXwcTN0wiMwIzNzEzW}`

Had to use '>' to write COLLEGE to a file PWN and then read the input in PWN through /challenge/run using '<'.
```
~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{s7KChO2d0G2R9jGVgNJSalPFRvy.QXwcTN0wiMwIzNzEzW}
```

### New Learnings
How to read inputs from other files using '<'.

## 6. Grepping stored results

### Solve
**Flag:** `pwn.college{UIhYM1CaZ-zAJBiBhsNAuVkXYZ3.QX4EDO0wiMwIzNzEzW}`

I had to use redirect output of challenge/run and then use grep to look for the file with the flag in it. Since all flags are of type 'pwn.college{}' i used grep on that string.
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{MOmvIgrWsEGkIdJUbBNNeUOvfZl.dhTM4QDLwMjN0czW}
```

### New Learnings
Practice use of grep and redirection.

## 7. Grepping live output

### Solve
**Flag:** `pwn.college{kvPBSVwdvYBY7JS9tID3LEkxKgF.QX5EDO0wiMwIzNzEzW}`

I had to use the '|' operator to feed output of challenge/run into a grep statement to look for the flag.
```
~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{kvPBSVwdvYBY7JS9tID3LEkxKgF.QX5EDO0wiMwIzNzEzW}
```

### New Learnings
How to use the pipe '|' operator.

## 8. Grepping errors

### Solve
**Flag:** `pwn.college{ESWAo3TJc0qZeUaer72wBOUn0Ga.QX1ATO0wiMwIzNzEzW}`

Had to redirect stderr to stdout and then use '|' to feed the output to a grep statement looking for a the flag.
```
~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{ESWAo3TJc0qZeUaer72wBOUn0Ga.QX1ATO0wiMwIzNzEzW}
```

### New Learnings
How to grep errors by redirecting error to output.

## 9. Filtering with grep -v

### Solve
**Flag:** `pwn.college{EJMSrHH4G9OxXxyYro2UvqnNFWp.0FOxEzNxwiMwIzNzEzW}`

The stdout for /challenge/run had 100s of decoys. I had to grep for the correct file by using -v with grep to exclude any flags with the words DECOY.
```
~$ /challenge/run | grep -v DECOY
pwn.college{EJMSrHH4G9OxXxyYro2UvqnNFWp.0FOxEzNxwiMwIzNzEzW}
```

### New Learnings
How to exclude certain strings using grep -v.

## 10. Duplicating piped data with tee

### Solve
**Flag:** `pwn.college{EizHIMyTh40lPjwBVD-1tllUjcr.QXxITO0wiMwIzNzEzW}`

The description wants us to pipe /challenge/pwn to /challenge/college. We also have use tee command to take the output from /challenge/pwn.
```
~$ /challenge/pwn | tee pwn1_output | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn1_output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "EizHIMyT"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret cuWwv2Cf | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{EizHIMyTh40lPjwBVD-1tllUjcr.QXxITO0wiMwIzNzEzW}
```

### New Learnings
How to intercept an output using tee before piping it.

## 11. Process substitution for input

### Solve
**Flag:** `pwn.college{gLz4s9wwdGCtNJG4io3U0uRaAO4.0lNwMDOxwiMwIzNzEzW}`

Had to use process substitution to compare the outputs of two different files using diff command and get the flag.
```
~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
91a92
> pwn.college{gLz4s9wwdGCtNJG4io3U0uRaAO4.0lNwMDOxwiMwIzNzEzW}
```

### New Learnings
How to perform process substitution for input to commands.

## 12. Writing to multiple programs

### Solve
**Flag:** `pwn.college{krp9Crfas_KMsiBIMmWbeg-mgDk.QXwgDN1wiMwIzNzEzW}`

Had to pipe the output of a file /challenge/hack to two different files to /challenge/the and /challenge/planet using process substitution and 'tee'.
```
~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{krp9Crfas_KMsiBIMmWbeg-mgDk.QXwgDN1wiMwIzNzEzW}
```

### New Learnings
How to write the output of a program to multiple programs.

## 13. Split-piping stderr and stdout

### Solve
**Flag:** `pwn.college{YX4jtuBU0aaLpB-ErATwpHtloof.QXxQDM2wiMwIzNzEzW}`

The description asks us to redirect /challenge/hack stderr to /challenge/the and stdout to /challenge/planet. This can be done by using |, 2>(). we have to use 2>() before |, otherwise /challenge/planet stderr will redirected to /challenge/the. This we don't want to happen.
```
~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{YX4jtuBU0aaLpB-ErATwpHtloof.QXxQDM2wiMwIzNzEzW}
```

### New Learnings
Extensive practice of piping and out redirecting of both stdout and stderr

## 14. Named pipes

### Solve
**Flag:** `pwn.college{08MynaZEBqNblaNJp5ehSaisNHm.01MzMDOxwiMwIzNzEzW}`

Created a named pipe with mkfifo /tmp/flag_fifo, then launched /challenge/run > /tmp/flag_fifo, which blocked because writing to a FIFO waits for a reader. An attempt to cat /tmp/flag_FIFO (wrong filename/case) was stopped, bg resumed the blocked writer in the background, and finally cat /tmp/flag_fifo (correct name) read from the FIFO, unblocking the writer so /challenge/run could output the flag and exit.
```
~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!
cat /tmp/flag_FIFO
q
^Z
[1]+  Stopped                 /challenge/run > /tmp/flag_fifo
hacker@piping~named-pipes:~$ bg
[1]+ /challenge/run > /tmp/flag_fifo &
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{08MynaZEBqNblaNJp5ehSaisNHm.01MzMDOxwiMwIzNzEzW}
[1]+  Done                    /challenge/run > /tmp/flag_fifo
```

### New Learnings
How to keep a process running in the background. How to create a named pipe for data transfer without saving to disk.

### References
None