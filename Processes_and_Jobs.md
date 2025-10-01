# Processes and Jobs

## 1. Listing Processes

### Solve
**Flag:** `pwn.college{UtSg7K9UYLLPtexY_kkYLpdtNQr.QX4MDO0wiMwIzNzEzW}`

Had to list all active processes to find the file under /challenge directory as directly using 'ls' wasn't allowed. There was only one file which gave the output upon running it.
```
~$ ps auxww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   12:36   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           8  0.0  0.0 231708  2560 ?        S    12:36   0:00 /run/dojo/bin/sleep 6h
root         133  0.0  0.0   4132  2560 ?        S    12:36   0:00 /challenge/18984-run-17801
root         136  0.0  0.0   2744  1600 ?        S    12:36   0:00 sleep 6h
hacker       147  0.0  0.0  36972 21440 ?        Sl   12:36   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disableLeaveAlert true /run/dojo/bin/bash --login
hacker       151  0.0  0.0 231940  4160 pts/0    Ss   12:36   0:00 /run/dojo/bin/bash --login
hacker       162  0.0  0.0 233600  3840 pts/0    R+   12:38   0:00 ps auxww
hacker@processes~listing-processes:~$ /challenge/18984-run-17801
Yahaha, you found me! Here is your flag:
pwn.college{UtSg7K9UYLLPtexY_kkYLpdtNQr.QX4MDO0wiMwIzNzEzW}
```

### New Learnings
How to see the details of every process running on the computer using ps aux and ps -ef.

## 2. Killing Processes

### Solve
**Flag:** `pwn.college{8Nm6bYRYAghFhaob9m9rKJNLkIt.QXyQDO0wiMwIzNzEzW}`

Had to list all active processes using ps -ef to find the PID of /challenge/dont_run in order to kill it so that /challenge/run would give the flag on running.
```
:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:41 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 12:41 ?        00:00:00 /run/dojo/bin/sleep 6h
root         135       1  0 12:41 ?        00:00:00 su -c /challenge/.launcher hacker
hacker       136     135  0 12:41 ?        00:00:00 /challenge/dont_run
hacker       137     136  0 12:41 ?        00:00:00 sleep 6h
hacker       148       1  0 12:41 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       152     148  0 12:41 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       163     152  0 12:42 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{8Nm6bYRYAghFhaob9m9rKJNLkIt.QXyQDO0wiMwIzNzEzW}
```

### New Learnings
How to kill a process with its PID.

## 3. Interrupting Processes

### Solve
**Flag:** `pwn.college{oRbLpVlIOB_OSLxzwCjkFiwPsob.QXzQDO0wiMwIzNzEzW}`

Had to interrupt the process /challenge/run using Ctrl-C in order to get the flag.
```
:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{oRbLpVlIOB_OSLxzwCjkFiwPsob.QXzQDO0wiMwIzNzEzW}
```

### New Learnings
How to interrupt any ongoing process.

## 4. Killing Misbehaving processes

### Solve
**Flag:** `pwn.college{oMWvhAO4nghOZm4W98Oxl_dzwRB.0FNzMDOxwiMwIzNzEzW}`

Had to run ps -ef to kill the decoy flag generator and then read the pipe and interrupt the process. Then run /challenge/run again, this time only flag will be in the named pipe because the decoy process was killed. Read the flag from the pipe.
```
~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:55 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 12:55 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 12:55 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 12:55 ?        00:00:00 /bin/bash /challenge/.init
root         139       1  0 12:55 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140     137  0 12:55 ?        00:00:00 sleep 6h
root         141     138  0 12:55 ?        00:00:00 sleep 6h
hacker       142     139  0 12:55 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       153       1  0 12:55 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       157     153  0 12:55 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       167     157  0 12:55 pts/0    00:00:00 ps -ef
hacker@processes~killing-misbehaving-processes:~$ kill 142 PID
~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
^C
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
"Lots of dummy files in the pipeline"
.
.
.
~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{oMWvhAO4nghOZm4W98Oxl_dzwRB.0FNzMDOxwiMwIzNzEzW
```

### New Learnings
Learnt how to kill processes and the impact it has on other processes.

## 5. Suspending Processes

### Solve
**Flag:** `pwn.college{obtKKIQqQuMI3NRlmPF0UMxl-kG.QX1QDO0wiMwIzNzEzW}`

I had to run a program /challenge/run and then resign it to the background using Ctrl-Z and then run it again to get the flag.
```
~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 13:04 pts/0    00:00:00 bash /challenge/run
root         148     146  0 13:04 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 13:04 pts/0    00:00:00 bash /challenge/run
root         153     136  0 13:04 pts/0    00:00:00 bash /challenge/run
root         155     153  0 13:04 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{obtKKIQqQuMI3NRlmPF0UMxl-kG.QX1QDO0wiMwIzNzEzW}
```

### New Learnings
How to resign a process to the background.

## 6. Resuming Processes

### Solve
**Flag:** `pwn.college{8CenZVRjVxp0xNyy9FcFMd6yfhb.QX2QDO0wiMwIzNzEzW}`

I had to run the process /challenge/run and then suspend it to the background before resuming it again and getting the flag.
```
~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{8CenZVRjVxp0xNyy9FcFMd6yfhb.QX2QDO0wiMwIzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

### New Learnings
How to resume background processes using 'fg'.

## 7. Backgrounding Processes

### Solve
**Flag:** `pwn.college{gC5gAUVU_04yIu4mqx85Q71WZSG.QX3QDO0wiMwIzNzEzW}`

Had to suspend a process and then background it and run a second copy that would detect that one process is already backgrounded and give me the flag.
```
:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S+   bash /challenge/run
root         148 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S    bash /challenge/run
root         156 S    sleep 6h
root         157 S+   bash /challenge/run
root         159 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{gC5gAUVU_04yIu4mqx85Q71WZSG.QX3QDO0wiMwIzNzEzW}
```

### New Learnings
How to background a suspended process using 'bg'.

## 8. Foregrounding Processes

### Solve
**Flag:** `pwn.college{4x3MS33vhn019ve_cMtryUxe8iA.QX4QDO0wiMwIzNzEzW}`

Similar to the last challenge but instead of running the process again we had to foreground it using 'fg'.
```
~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{4x3MS33vhn019ve_cMtryUxe8iA.QX4QDO0wiMwIzNzEzW}
```

### New Learnings
How to foreground and backgrounded process.

## 9. Starting Backgrounded Processes

### Solve
**Flag:** `pwn.college{EKijaur6wyE7u_CaQybs0U8jSkM.QX5QDO0wiMwIzNzEzW}`

Had to run /challenge/run directly in the background by appending '&' in front of it to get the flag.
```
~$ /challenge/run &
[1] 146
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{EKijaur6wyE7u_CaQybs0U8jSkM.QX5QDO0wiMwIzNzEzW}
```

### New Learnings
How to run a process in the background directly.

## 10. Process exit codes

### Solve
**Flag:** `pwn.college{AqoXNbGWdKNaDZ-NnPFFu3_E1j4.QX5YDO1wiMwIzNzEzW}`

Had to get the exit code of a process and use it as an argument to another process to get the code.
```
~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
24
hacker@processes~process-exit-codes:~$ /challenge/submit-code 24
CORRECT! Here is your flag:
pwn.college{AqoXNbGWdKNaDZ-NnPFFu3_E1j4.QX5YDO1wiMwIzNzEzW}
```

### New Learnings
How to retrieve the exit code (proof of process success) of a process using '?'.

### References
NONE
