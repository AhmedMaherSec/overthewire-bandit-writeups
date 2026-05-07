# Bandit Level 18 → Level 19

## Goal
The password is in the `readme` file, but SSH login automatically logs out due to a modified `.bashrc`.

## Solution

1. Used `scp` to transfer the `readme` file from the remote server to a local directory: 
```
scp -P 2220 bandit18@bandit.labs.overthewire.org:/home/bandit18/readme . 
```
2. Read the downloaded `readme` file:
```
cat readme
```

## Result
The password for the next level was obtained after reading the contents of the downloaded file.

## Learning
- I learned that non-interactive access methods can be used to bypass shell restrictions such as forced logout in `.bashrc`.
- - Tools like `scp` can retrieve files directly without requiring an interactive shell.
