# Bandit Level 29 → Level 30

## Goal
The password for the next level is hidden somewhere inside the remote Git repository and must be retrieved by investigating the repository data and branches.

## Solution

1. Cloned the remote Git repository:
```
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```
2. Entered the repository and inspected its contents:
```
cd repo
ls
cat README.md
```
3. Reviewed the commit history, but no password was exposed in previous commits:
```
git log
git show <commit_hashs>
```
4. Listed all available local and remote branches:
```
git branch -a
```
5. Switched to the remote `dev` branch:
```
git checkout remotes/origin/dev
```
6. Inspected the files in the `dev` branch:
```
cat README.md
```
## Result
The password for the next level was found inside the `README.md` file in the remote `dev` branch.

## Learning
- I learned that Git repositories can contain multiple branches with different versions of files and data.

- I learned that sensitive information may still exist in development branches that are not part of the main branch.
