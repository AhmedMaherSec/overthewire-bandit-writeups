# Bandit Level 28 → Level 29

## Goal
The password for the next level is hidden in the Git repository history and can be retrieved by inspecting previous commits.

## Solution

1. Cloned the remote Git repository:
```
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
```
2. Inspected the repository contents:
```
cd repo
ls
cat README.md
```
3. Observed that the password was replaced with `xxxxxxxxxx`, indicating that sensitive information had been removed.

4. Viewed the Git commit history:
```
git log
```
5. Inspected the latest commit to identify what was changed:
```
git show 00daa614aac60bd2981c381484191eb7bc4dcfd9
```

## Result
The password for the next level was recovered from a previous Git commit that exposed sensitive information.

## Learning
- I learned that sensitive information such as passwords may still exist in older Git commits even after being removed from current files.

- I learned that Git stores previous versions of files and changes, allowing old data to be reviewed through commands like `git log` and `git show`.
