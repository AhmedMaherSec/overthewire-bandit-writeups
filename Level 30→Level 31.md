# Bandit Level 30 → Level 31

## Goal
The password for the next level is hidden inside the Git repository and must be discovered by exploring its internal data.

## Solution

1. Cloned the remote Git repository:
```
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
```
2. Entered the repository and inspected the contents:
```
cd repo
ls
cat README.md
```
3. Checked commit history and branches, but no useful data was found:
```
git log
git branch -a
```
4. Searched for additional Git references and found a tag:
```
git tag
```
5. Inspected the tag content to retrieve hidden data:
```
git show secret
```

## Result
The password for the next level was found inside a Git tag.

## Learning
- I learned that Git tags can point to specific commits and may contain hidden or sensitive information not visible in branches or files.

- I learned that important data in Git repositories is not limited to branches and commit history only, but can also exist in tags.
