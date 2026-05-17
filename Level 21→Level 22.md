# Bandit Level 21 → Level 22

## Goal
The password for the next level is obtained by analyzing a cron job in `/etc/cron.d/` that runs a script at regular intervals.

## Solution

1. Connected to the server using SSH: 
```
ssh -p 2220 bandit21@bandit.labs.overthewire.org
```
2. Navigated to `/etc/cron.d/` and listed the scheduled cron jobs.
```
cd /etc/cron.d/
ls
```
3. Found `cronjob_bandit22` and inspected its configuration to see what command is being executed.
```
cat cronjob_bandit22
```
4. Found `/usr/bin/cronjob_bandit22.sh` and analyzed it to understand its behavior; it writes the bandit22 password into a temporary file in `/tmp`.
```
cat /usr/bin/cronjob_bandit22.sh
```
5. Accessed the generated file in `/tmp` to retrieve the password.
```
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
## Result
The password for the next level was found in a temporary file created by a cron job script.

## Learning
- I learned that `cron` is used to automatically execute scripts or commands at predefined intervals.

- I learned that cron jobs can run with different user privileges and may generate or modify files in locations like `/tmp`.

- I learned that analyzing `/etc/cron.d/` can help identify automated system tasks and potential privilege-related behaviors.
