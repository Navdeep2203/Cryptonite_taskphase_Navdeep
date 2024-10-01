# Hello Hackers Module

## Challenge
For this challenge I was tasked with calling a command to access the Linux system and acquire a flag.

## Method
1.  I started by connecting to the pwn.college server via SSH using this command:
```bash
ssh -i /home/navdee2203/key hacker@dojo.pwn.college
```
2.  After logging in, I saw the following prompt:
```
hacker@hello~intro-to-commands:~$
```
3. I entered the command `hello` on the terminal, as it was specified in the challenge description, and it provided the flag.
```bash
hello
```

## Flag
The flag that I got back after solving the challenge was
```bash
pwn.college{0XiGSdZNGxWbRN8dAMACNnPrrEZ.ddjNyUDLzAjN0czW}
