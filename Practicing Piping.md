# Practicing Piping

## Challenge 1 : Redirecting Output
n this challenge, the task was to use  the `> ` redirection operator to write the word "PWN" (in uppercase) to a file named "COLLEGE" (in uppercase). The objective was to demonstrate an understanding of how to redirect output to a file in Linux using the shell.

### Method 
1. Firstly, I connected to the pwn.college server via the SSH.
2. Then, I used the `echo` command  to print `PWN` with `>` operator which redirects the output to the file `COLLEGE`.
   ```
   echo PWN > COLLEGE
   ```
   which gave me the following output and the flag to proceed.
   ```
   Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
   flag:
   pwn.college{oB8uCjXBujQMvGOIW6CBmqJdLDN.dRjN1QDLzAjN0czW}
   ```
### Flag
```
pwn.college{oB8uCjXBujQMvGOIW6CBmqJdLDN.dRjN1QDLzAjN0czW}
```

## Challenge 2: Redirecting more output
In this challenge, the goal was to redirect the output of a command `/challenge/run` to a specific file named `myflag`. The challenge focused on the concept how standard output (stdout) can be redirected while still allowing standard error (stderr) messages to be displayed in the terminal.

### Method 
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then, I ran the command to execute `/challenge/run` while redirecting its output to the file `myflag`:
   ```
   /challenge/run > myflag
   ```
   The command printed information and instructions to the terminal via standard error (stderr), while the actual flag was written to the myflag file and the following output was displayed.
   ```
   [INFO] WELCOME! This challenge makes the following asks of you:
   [INFO] - the challenge will check that output is redirected to a specific file path : myflag
   [INFO] - the challenge will output a reward file if all the tests pass : /flag

   [HYPE] ONWARDS TO GREATNESS!

   [INFO] This challenge will perform a bunch of checks.
   [INFO] If you pass these checks, you will receive the /flag file.

   [TEST] You should have redirected my stdout to a file called myflag. Checking...

   [PASS] The file at the other end of my stdout looks okay!
   [PASS] Success! You have satisfied all execution requirements.
   ```
3. After executing the command, I checked the contents of ` myflag`.
   ```
   cat myflag
   ```
   which displayed the flag.
   ```
   [FLAG] Here is your flag:
   [FLAG] pwn.college{4QlBxr_b3560PLyykez1xIPdWPi.dVjN1QDLzAjN0czW}
   ```
### Flag
```
pwn.college{4QlBxr_b3560PLyykez1xIPdWPi.dVjN1QDLzAjN0czW}
```

## Challenge 3: Appending output
In this challenge, the task  focused on output redirection in append mode utilizing the `>>` operator. The objective was to guarantee that when executing the `/challenge/run` command, both segments of the flag would be accurately recorded in a designated file without erasing any pre-existing content.

### Method
1.  Firstly, I reconnected to the pwn.college server via the SSH.
2.  Then I ran the command `/challenge/run` with output redirected to the file `/home/hacker/the-flag` in append mode:
    ```
    /challenge/run >> /home/hacker/the-flag
    ```
   After executing the command the following output was displayed and the first half of the flag was written directly to the file, while the second half was displayed on stdout . By using the append mode, both halves of the flag were correctly saved in the file.
   ```
   [INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
```
3. Then, I verified the contents of the file to ensure both halves of the flag were present which displayed the flag to proceed.
   ```
   cat /home/hacker/the-flag
   ```
   Output:
   ```
    |
   \|/ This is the first half:
    v
   pwn.college{A2-gr6Xyrf9Oi4gyjLA1uKdaGhF.ddDM5QDLzAjN0czW}
                              ^
     that is the second half /|\
                              |

   If you only see the second half above, you redirected in *truncate* mode (>)
   rather than *append* mode (>>), and so the write of the second half to stdout
   overwrote the initial write of the first half directly to the file. Try append
   mode!
   ```
### Flag
```
   pwn.college{A2-gr6Xyrf9Oi4gyjLA1uKdaGhF.ddDM5QDLzAjN0czW}
```

## Challenge 4







