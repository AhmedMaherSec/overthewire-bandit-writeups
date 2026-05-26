# Bandit Level 31 → Level 32

## Goal
The password for the next level is obtained by interacting with the remote Git repository and completing the required repository task.

## Solution

1. Cloned the remote Git repository:
```
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
```
2. Entered the repository and read the instructions:
```
cd repo
cat README.md
```
3. Created the required file with the specified content:
```
echo 'May I come in?' > key.txt
```
4. Attempted to add the file, then discovered it was ignored by `.gitignore`:
```
git add key.txt
```
5. Forced Git to add the ignored file:
```
git add -f key.txt
```
6. Configured Git username and email, then committed the changes:
```
git config --global user.email "maher@local"
git config --global user.name "maher"

git commit -m "new"
```
7. Pushed the commit to the remote repository:
```
git push origin master
```

## Result
The remote repository validated the submitted file and returned the password for the next level.

## Learning
- I learned that `.gitignore` can prevent files from being tracked, but ignored files can still be added manually using force options.

- I learned how to create, commit, and push changes to a remote Git repository .
