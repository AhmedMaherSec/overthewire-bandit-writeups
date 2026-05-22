# Bandit Level 27 → Level 28

## Goal
The password for the next level is stored in a remote Git repository. The task is to clone the repository, inspect its contents, and retrieve the password.

## Solution

1. Cloned the remote Git repository using SSH on port 2220:
```
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```
2. Entered the cloned repository directory:
```
cd repo
```
3. Listed the files inside the repository:
```
ls
```
4. Read the file containing the password:
```
cat README
```

## Result
The password for the next level was found inside the README file in the cloned Git repository.

## Learning
- I learned how to clone a remote Git repository using SSH and a custom port.

- I learned how to inspect the contents of a cloned Git repository to search for useful information such as passwords or configuration files.
