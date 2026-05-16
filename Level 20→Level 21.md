# Bandit Level 20 → Level 21

## Goal
The password for the next level is obtained using a setuid binary that connects to a localhost port, verifies the current password, and returns the next password.

## Solution

1. Connected to the server using SSH: 
```
ssh -p 2220 bandit20@bandit.labs.overthewire.org
```
2. Listed the files in the home directory and found a setuid binary named `suconnect`.
```
ls
```
3. Executed the binary to understand its behavior and found that it requires a port as an argument.
```
./suconnect
```
4. Created a local listener using `netcat` and sent the previous level password to it.
```
echo "...." | netcat -lp 5555 &
```
5. Executed the setuid binary and provided the listening port as an argument.
```
./suconnect 5555
```
## Result
The binary connected to the listener, verified the previous password, and returned the password for the next level.

## Learning
- I learned how setuid binaries can interact with local network services.
- I learned how to use `netcat` as a simple TCP listener.
- I learned how background processes (`&`) allow simultaneous command execution.
