# Bandit Level 26 → Level 27

## Goal
The password for the next level can be retrieved using a setuid binary that allows executing commands as another user.

## Solution

1. Listed files in the home directory:
```
ls
```
2. Identified a setuid binary owned by `bandit27`:
```
ls -lh bandit27-do
```
3. Executed the binary to understand its usage:
```
./bandit27-do
```
4. Used the binary to run a command as bandit27 and read the password file:
```
./bandit27-do cat /etc/bandit_pass/bandit27
```

## Result
The password for the next level was obtained using a setuid binary that executes commands with elevated privileges.

## Learning
I learned that setuid binaries can allow users to execute commands with the permissions of the file owner.

