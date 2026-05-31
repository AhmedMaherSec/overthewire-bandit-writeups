# Bandit Level 22 → Level 23

## Goal
The password for the next level is obtained by analyzing a cron job that writes it to a temporary file in `/tmp`.

## Solution

1. Connected to the server using SSH: 
```
ssh -p 2220 bandit22@bandit.labs.overthewire.org
```
2. Navigated to the cron configuration directory:
```
cd /etc/cron.d/
ls
```
3. Identified the relevant cron job configuration:
```
cat cronjob_bandit23
```
4. Located the script executed by the cron job and inspected it:
```
ls -lh /usr/bin/cronjob_bandit23.sh
cat /usr/bin/cronjob_bandit23.sh
```
5. Analyzed the script logic and manually reproduced the filename generation process for bandit23:
```
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```
6. Used the generated hash to locate and read the file containing the password.
```
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

## Result
The password for the next level was found in a temporary file created by a cron job.

## Learning
- I learned that cron is a time-based job scheduler used to automatically execute scripts at regular intervals.

- I learned how to analyze scheduled jobs in `/etc/cron.d/` to understand system automation tasks.

- I learned that some scripts generate dynamic file paths based on username hashing (e.g., md5sum), which can be reproduced manually to retrieve hidden data.
