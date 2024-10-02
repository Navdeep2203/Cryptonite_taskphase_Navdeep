# Hello Hackers Module

## Challenge 1: Intro to Commands
For this challenge, I was tasked with calling a command to access the Linux system and acquire a flag.

### Method
1.  I started by connecting to the pwn.college server via SSH using this command:
```
ssh -i /home/navdee2203/key hacker@dojo.pwn.college
```
2.  After logging in, I saw the following prompt:
```
hacker@hello~intro-to-commands:~$
```
3. I entered the command `hello` on the terminal, as it was specified in the challenge description, and it provided the flag.
```
hello
```

### Flag
The flag that I got back after solving the challenge was
```
pwn.college{0XiGSdZNGxWbRN8dAMACNnPrrEZ.ddjNyUDLzAjN0czW}

```

## Challenge 2: Intro to Arguments

For this challenge, I was tasked with running a 'hello' command with the argument 'hackers' and obtaining the flag.

### Method

1. Firstly I reconnected via SSH to the Linux system and I was shown the following prompt:
   ```
   hacker@hello~intro-to-commands:~$

   ```
2. Then I executed the command
   ```
   hello hackers

   ```
   where the command 'hello' was passed with the argument 'hackers', which then returned the flag to proceed.

### Flag
```
pwn.college{wsK_RHzzKn3JNzZFyQCV-XHm4W_.dhjNyUDLzAjN0czW}

```

   


