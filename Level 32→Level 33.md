# Bandit Level 32 → Level 33

## Goal
Escape the restricted shell and retrieve the password for the next level.

## Solution

1. Logged in to the server via SSH:
```
ssh -p 2220 bandit32@bandit.labs.overthewire.org
```
2. After login, the environment was a restricted shell where normal commands were blocked or transformed.
3. Attempting standard commands failed due to uppercase conversion and restrictions.
4. The current shell was invoked directly using:
```
$0
```
5. This dropped into a normal shell where commands worked properly.
  
6. Retrieved the password from the system file:
```
cat /etc/bandit_pass/bandit33
```

## Result
The password for the next level was successfully obtained from the system password file.

## Learning
- I learned that restricted shells can sometimes be bypassed by invoking the underlying shell directly

- I learned that shell restrictions often limit command parsing rather than removing access to system binaries.
