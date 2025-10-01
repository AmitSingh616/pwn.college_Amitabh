# Data Manipulation

## 1. Translating Characters 

### Solve
**Flag:** `pwn.college{4_btsboki5MTvnL-cwjJ9s4nEmj.01MxEzNxwiMwIzNzEzW}`

Had to swap the cases of all the characters in the flag obtained by executing /challenge/run. This was done using character classes with tr command.
```
~$ /challenge/run | tr '[:lower:][:upper:]' '[:upper:][:lower:]'
yOUR CASE-SWAPPED FLAG:
pwn.college{4_btsboki5MTvnL-cwjJ9s4nEmj.01MxEzNxwiMwIzNzEzW}
```

### New Learnings
How to use tr command to switch out characters

## 2. Deleting Characters

### Solve
**Flag:** `pwn.college{k_heTRKhMUEMn0Rotu9D33lsebi.0FNxEzNxwiMwIzNzEzW}`

Had to delete certain characters from the fake flag to get the real flag using tr -d.
```
~$ /challenge/run
Your character-stuffed flag:
p%w^n^.^c^o^l%l%e^%g^%e^{k^_^%h^%e^T^%R%K%hM^U^%E^%M%n0^%R%o%t%u9%D^%3^%3^l%se^b%i%.^0^F^N^%x^%E^zN^%x^w^i^M%w%I^%zN%z^E^z^W^}^%
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{k_heTRKhMUEMn0Rotu9D33lsebi.0FNxEzNxwiMwIzNzEzW}
```

### New Learnings
How to delete certain characters from a string.

## 3. Deleting newlines

### Solve
**Flag:** `pwn.college{Uj6vGKMz9VrI_rNFvejxyWcw1MZ.0VNxEzNxwiMwIzNzEzW}`

Had to delete new lines from the fake flag to get the real flag using tr -d "\n".
```
~$ /challenge/run
Your line-split flag: 
p
w
n
.
col
l
e
ge
{Uj6v
G
K
Mz9Vr
I
_r
NFv
e
jxyW
c
w1MZ
.
0
VN
x
E
z
Nx
w
i
M
w
I
z
Nz
EzW}

hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{Uj6vGKMz9VrI_rNFvejxyWcw1MZ.0VNxEzNxwiMwIzNzEzW}
```

### New Learnings
How to delete new lines from files.

## 4. Extracting the first lines with head

### Solve
**Flag:** `pwn.college{0Cro8uojO_4byYkSD8jEvFhcyls.0lNxEzNxwiMwIzNzEzW}`

Had to pipe the first 7 lines of a file to another file to get the correct flag using 'head -n' command.
```
~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{0Cro8uojO_4byYkSD8jEvFhcyls.0lNxEzNxwiMwIzNzEzW}
```

### New Learnings
How to get the first 'n' lines of a file using 'head'.

## 5. Extracting specific sections of text

### Solve
**Flag:** `pwn.college{wMpW1udj5pUDhAUQ9vMzUo9Sznv.01NxEzNxwiMwIzNzEzW}`

Had to use both 'cut' and 'tr' commands to select the 2nd column and then delete new lines from the file /challenge/run in order to get the actual flag.
```
~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{wMpW1udj5pUDhAUQ9vMzUo9Sznv.01NxEzNxwiMwIzNzEzW}
```

### New Learnings
How to use cut command to separate a column from the file.

## 6. Sorting data

### Solve
**Flag:** `pwn.college{IH25YNrsZnp2ALh-6uQGtjhHNct.0FM0MDOxwiMwIzNzEzW}`

Had to use the 'sort' command to sort a file with 100 flags in alphabetical order where the last flag in the sorted list was the real flag.
```
~$ sort /challenge/flags.txt
. 
.
.
.
`pwn.college{IH25YNrsZnp2ALh-6uQGtjhHNct.0FM0MDOxwiMwIzNzEzW}`
```

### New Learnings
How to use 'sort' command to sort a file. 

### References
NONE
