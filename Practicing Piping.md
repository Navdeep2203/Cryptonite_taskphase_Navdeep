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

## Challenge 4: Redirecting errors

In this challenge, the task to redirect the standard output and standard error of a command into distinct files. The objective was to verify that the output generated by the `/challenge/run ` command was captured in `myflag`, while the error messages were stored in `instructions`.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then, I used the following command to run `/challenge/run` with
   * `>` which  redirects the standard output (FD 1) to the file `myflag`.
   * `2>` which  redirects the standard error (FD 2) to the file `instructions``.
   ```
   /challenge/run > myflag 2> instructions
   ```
3. Then, I checked the contents of `myflag` file.
   ```
   cat myflag
   ```
   which gave me the flag to proceed.
   ```
   [FLAG] Here is your flag:
   [FLAG] pwn.college{kksumkhTfqwaMPWG81XZaBovscu.ddjN1QDLzAjN0czW}
   ```
   and also I checked the contents of the file `instructions`.
   ```
   cat instructions
   ```
   Content:

   ```
   [INFO] WELCOME! This challenge makes the following asks of you:
   [INFO] - the challenge will check that output is redirected to a specific file path : myflag
   [INFO] - the challenge will check that error output is redirected to a specific file path : instructions
   [INFO] - the challenge will output a reward file if all the tests pass : /flag
 
   [HYPE] ONWARDS TO GREATNESS!

   [INFO] This challenge will perform a bunch of checks.
   [INFO] If you pass these checks, you will receive the /flag file.

   [TEST] You should have redirected my stdout to a file called myflag. Checking...

   [PASS] The file at the other end of my stdout looks okay!
   
   [TEST] You should have redirected my stderr to instructions. Checking...

   [PASS] The file at the other end of my stderr looks okay!
   [PASS] Success! You have satisfied all execution requirements.
   ```

### Flag 
```
pwn.college{kksumkhTfqwaMPWG81XZaBovscu.ddjN1QDLzAjN0czW}
```

## Challenge 5: Redirecting input
In this challenge, I got to know how to redirect input to a command using the < operator. The goal was to write the value `COLLEGE` to a file named `PWN` and then redirect this file as input to the `/challenge/run` program.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then, I used the echo command with output redirection (>) to write "COLLEGE" to the PWN file:
   ```
   echo COLLEGE > PWN
   ```
3. Then, I used the < operator to pass the contents of the PWN file as input to the /challenge/run command:
   ```
   /challenge/run < PWN
   ```
   which gave me the following output and the flag to proceed.
   ```
   Reading from standard input...
   Correct! You have redirected the PWN file into my standard input, and I read
   the value 'COLLEGE' out of it!
   Here is your flag:
   pwn.college{gzKz66fWCCNDCFT4-ObD1qUoTND.dBzN1QDLzAjN0czW}
   ```
### Flag
```
pwn.college{gzKz66fWCCNDCFT4-ObD1qUoTND.dBzN1QDLzAjN0czW}
```


## Challenge 6: Grepping stored results
In this challenge, I learned to combine the techniques of output redirection and searching through text files using grep. The task was to redirect the output of the `/challenge/run` command, which generates a large amount of data, to a file and then search that file for the flag.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then ,I executed `/challenge/run`, redirecting its output to `/tmp/data.txt` using the `>` operator.
   ```
   /challenge/run > /tmp/data.txt
   ```
3. Then, I used `grep` to search through the file for the line containing the flag by matching the pwn.college{} pattern.
   ```
   grep "pwn.college" /tmp/data.txt
   ```
   which found the flag and gave me the flag to proceed.
   ```
   pwn.college{0sGfKADHImwk1lH7qwCQLnbPyZd.dhTM4QDLzAjN0czW}
   ```
### Flag
```
pwn.college{0sGfKADHImwk1lH7qwCQLnbPyZd.dhTM4QDLzAjN0czW}
```

## Challenge 7: Grepping live output
In this challenge, I got to know how to use the pipe (|) operator in Linux to pass the output of one command directly as input to another command. Instead of redirecting output to a file first, we used the ` |` operator to send the output of `/challenge/run` directly to grep, which searched for the flag.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then I executed the following command
   ```
   /challenge/run | grep "pwn.college"
   ```
   where
   * `/challenge/run`: Generates a large output, including the flag.
   * `|` (pipe): Connects the output of /challenge/run to the input of grep.
   * `grep "pwn.college"`: Searches for the specific pattern pwn.college in the output to get the flag.

   Output:
   ```
   [INFO] WELCOME! This challenge makes the following asks of you:
   [INFO] - the challenge checks for a specific process at the other end of stdout : grep
   [INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

   [HYPE] ONWARDS TO GREATNESS!

   [INFO] This challenge will perform a bunch of checks.
   [INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

   [TEST] You should have redirected my stdout to another process. Checking...
   [TEST] Performing checks on that process!

   [INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
   [INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
   [INFO] To pass the checks, the executable must be grep.

   [PASS] You have passed the checks on the process on the other end of my stdout!
   [PASS] Success! You have satisfied all execution requirements.
   pwn.college{4ViYWHF3qlu01RL51m3NS_Ku0Rv.dlTM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{4ViYWHF3qlu01RL51m3NS_Ku0Rv.dlTM4QDLzAjN0czW}

```

## Challenge 8: Grepping errors
In this challenge, the task was to explore how to redirect errors (stderr) into another program for further processing using the 2>&1 operator. The objective was to capture error messages from the `/challenge/run` command and search through them for a specific pattern using `grep`.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. It was required to redirect both the standard output(stdout) and standard error(stderr) from the `/challenge/run` command.
   While the `| ` operator only pipes the stdout to another program, using 2>&1 allows us to redirect stderr to stdout and then pipe both streams into grep.
   The command I used for redirection is
   ```
   /challenge/run 2>&1 | grep "pwn.college"
   ```
   This redirected both stderr and stdout to `grep`, which then searched for the flag pattern "pwn.college" and showed the output :
   ```
   [INFO] WELCOME! This challenge makes the following asks of you:
   [INFO] - the challenge checks for a specific process at the other end of stderr : grep
   [INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

   [HYPE] ONWARDS TO GREATNESS!

   [INFO] This challenge will perform a bunch of checks.
   [INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

   [TEST] You should have redirected my stderr to another process. Checking...
   [TEST] Performing checks on that process!

   [INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
   [INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
   [INFO] To pass the checks, the executable must be grep.

   [PASS] You have passed the checks on the process on the other end of my stderr!
   [PASS] Success! You have satisfied all execution requirements.
   pwn.college{AtXpRvtbOxufi0S7gjkFb4xotDN.dVDM5QDLzAjN0czW}
   ```

   ### Flag
   ```
   pwn.college{AtXpRvtbOxufi0S7gjkFb4xotDN.dVDM5QDLzAjN0czW}
   ```

   ## Challenge 9: Duplicating piped data with tee
   



   

   









