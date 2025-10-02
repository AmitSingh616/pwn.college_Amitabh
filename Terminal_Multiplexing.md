# Terminal Multiplexing

## 1. Launching Screen

### Solve
**Flag:** `pwn.college{0Ux1S-X1bmtKE-kOrimhcXex0sL.0VN4IDOxwiMwIzNzEzW}`

Had to open a virtual terminal inside the current terminal using the 'screen' command to get the flag. 
```
~: screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{0Ux1S-X1bmtKE-kOrimhcXex0sL.0VN4IDOxwiMwIzNzEzW}
```
### New Learnings
How to open a virtual terminal.

## 2. Detaching and Attaching

### Solve
**Flag:** `pwn.college{wpbOAagMwWrgRNELhSVHiojgEAX.0lN4IDOxwiMwIzNzEzW}`

Had to open a virtual terminal and then detach it. Then i had to run /challenge/run and reattach the virtual terminal to get the flag.
```
[Main Terminal]
~$ screen
[detached from 148.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[detached from 148.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 148.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[detached from 148.pts-0.terminal-multiplexing~detaching-and-attaching]

[Virtual Terminal]
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{wpbOAagMwWrgRNELhSVHiojgEAX.0lN4IDOxwiMwIzNzEzW}
Yes! Flag is: pwn.college{wpbOAagMwWrgRNELhSVHiojgEAX.0lN4IDOxwiMwIzNzEzW}
```
### New Learnings
How to detach and reattach virtual terminal.

## 3. Finding Sessions

### Solve
**Flag:** `pwn.college{4j1zVEV9lowg2U8KA1E-nmbBOm1.01N4IDOxwiMwIzNzEzW}`

Had to list all running terminals and then reattach and detach them one by one till flag is found.
```
[Main Terminal]
~$ screen -ls
There are screens on:
        168.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        188.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        148.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_be02ef2480154bd4    (Detached)
        147.session_5ea964df321a5de4    (Detached)
        150.session_cddab03d47d38903    (Detached)
6 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
[detached from 144.session_be02ef2480154bd4]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
[detached from 147.session_5ea964df321a5de4]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 150
[detached from 150.session_cddab03d47d38903]

[Virtual Terminal]
~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{4j1zVEV9lowg2U8KA1E-nmbBOm1.01N4IDOxwiMwIzNzEzW}
pwn.college{4j1zVEV9lowg2U8KA1E-nmbBOm1.01N4IDOxwiMwIzNzEzW}
```
### New Learnings
How to list all running terminals using screen -ls.

## 4. Switching Windows

### Solve
**Flag:** `pwn.college{823pJ5msZIPaCyQKlWlBomEawkt.0FO4IDOxwiMwIzNzEzW}`

Had to reattach to a screen and then navigate to window 0 using <Ctrl-A 0> to get the flag.
```
[Main Terminal]
~$ screen -ls
There are screens on:
        168.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        188.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        148.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_be02ef2480154bd4    (Remote or dead)
        147.session_5ea964df321a5de4    (Remote or dead)
        150.session_cddab03d47d38903    (Remote or dead)
        136.challenge_session   (Detached)
7 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r 136
[detached from 136.challenge_session]

[Virtual Terminal]
~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{823pJ5msZIPaCyQKlWlBomEawkt.0FO4IDOxwiMwIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{823pJ5msZIPaCyQKlWlBomEawkt.0FO4IDOxwiMwIzNzEzW}
```
### New Learnings
How to navigate multiple windows in a screen using <Ctrl-A> shortcuts.

## 5. Detaching and Attaching (tmux)

### Solve
**Flag:** `pwn.college{sMSkgRM1FwEhvxMA5HAIu23Ld6A.0VO4IDOxwiMwIzNzEzW}`

Had to open a virtual terminal and then detach it using 'tmux' and <Ctrl-B> shortcuts. Then i had to run /challenge/run and reattach the virtual terminal to get the flag.
```
[Main Terminal]
~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]

[Virtual Terminal]
~$  echo Congratulations, here is your flag: pwn.college{sMSkgRM1FwEhvxMA5HAIu23Ld6A.0VO4IDOxwiMwIzNzEzW}
```
### New Learnings
How to use command 'tmux'.

## 6. Switching Windows (tmux)

### Solve
**Flag:** `pwn.college{UyfjOeEe-9lvLdeBHLHNP8zvsvs.0FM5IDOxwiMwIzNzEzW}`

Had to reattach to a screen and then navigate to window 0 using <Ctrl-B 0> to get the flag.
```
[Main Terminal]
~$ tmux ls
challenge_session: 2 windows (created Thu Oct  2 04:12:47 2025)
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
[detached (from session challenge_session)]

[Virtual Terminal]
~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{UyfjOeEe-9lvLdeBHLHNP8zvsvs.0FM5IDOxwiMwIzNzEzW}
```
### New Learnings
How to navigate multiple windows in a screen using <Ctrl-B> shortcuts.

### References
None
