# Processes andd Jobs

## Challenge 1: Listing Processes
In this challenge the task was to identify and relaunch a running process in a restricted environment to retrieve a flag. The `/challenge/run` file was renamed and launched as a background process, and we had to use the `ps` command to find and execute it.

### Method
1. Firstly connected to the pwn.college server via the SSH.
2.  I started by listing all running processes using the `ps -ef` command:
```
ps -ef
```
which displayed the following processes:
```
Connected!
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:28 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 12:28 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 12:28 ?        00:00:00 /challenge/19454-run-20351
root          72      68  0 12:28 ?        00:00:00 sleep 6h
hacker        73       0  0 12:28 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 12:28 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/19454-run-20351
Yahaha, you found me! Here is your flag:
pwn.college{keJaqSbUH4oT84D7r2P1wRFsy3R.dhzM4QDLzAjN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
3. From the output, I identified the process linked to the renamed challenge file:
   ```
   root          68       1  0 12:28 ?        00:00:00 /challenge/19454-run-20351
   ```
4. To retrieve the flag, I executed the identified process:]
   ```
   /challenge/19454-run-20351
   ```
   which displayed the flag for this challenge.

### Flag
```
pwn.college{keJaqSbUH4oT84D7r2P1wRFsy3R.dhzM4QDLzAjN0czW}
```

## Challenge 2: Killing Processes
In this challenge the task was to terminate a process named `/challenge/dont_run` that was blocking another process from running. The `ps` command was used to identify the process, and the `kill` command was used to terminate it.

### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. Then, I used the `ps -ef` command to display all running processes, including their Process IDs (PIDs).
```
ps -ef
```
which displayed the following processes
```
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:35 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 12:35 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 12:35 ?        00:00:00 su -c /challenge/.launcher hacker
hacker        73      71  0 12:35 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 12:35 ?        00:00:00 sleep 6h
hacker        75       0  0 12:35 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        92      75  0 12:36 pts/0    00:00:00 ps -ef
```
3.The process named `/challenge/dont_run` was identified with the following output:
```
hacker        73      71  0 12:35 ?        00:00:00 /challenge/dont_run
```
4. Then I used the `kill` command with the PID of the process:
   ```
   kill 73
   ```
5. After killing the process, I ran `ps -ef` command again to confirm that the process was no longer running:
   ```
   ps -ef
   ```
   which now displayed the following processes.
   ```
   UID          PID    PPID  C STIME TTY          TIME CMD
   root           1       0  0 12:35 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
   root           7       1  0 12:35 ?        00:00:00 /run/dojo/bin/sleep 6h
   hacker        74       1  0 12:35 ?        00:00:00 sleep 6h
   hacker        75       0  0 12:35 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
   hacker        93      75  0 12:36 pts/0    00:00:00 ps -ef
   ```
6. With the blocking process terminated, I ran the main challenge:
   ```
   /challenge/run
   ```
   which now gave the flag for this challenge.
   ```
   Great job! Here is your payment:
   pwn.college{wg8mHX2g8TwW1-3xZv3HUxyGDuL.dJDN4QDLzAjN0czW}
   ```'

### Flag
```
pwn.college{wg8mHX2g8TwW1-3xZv3HUxyGDuL.dJDN4QDLzAjN0czW}
```

## Challenge 3: Interrupting Processes
In this challenge, the task was to use the Ctrl-C keyboard shortcut to interrupt a running process in the terminal. This demonstrates how to manually send an interrupt signal to terminate a process that's waiting for input or running indefinitely.

### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. I started the process by executing the following command:
   ```
   /challenge/run
   ```
   which displayed the following message
   ```
   I could give you the flag... but I won't, until this process exits. Remember,
   you can force me to exit with Ctrl-C. Try it now!
   ```
3. To forcefully terminate the process, I pressed Ctrl-C, which sent an interrupt signal to the terminal, stopping the process
   ```
   ^C
   ```
   which gave the flag for this challenge
   ```
   Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
   pwn.college{EH6hz1ZclRFY6wz4hNCDJpYkC5v.dNDN4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{EH6hz1ZclRFY6wz4hNCDJpYkC5v.dNDN4QDLzAjN0czW}
```

## Challenge 4: Suspending Processes
In this challenge, the goal was to suspend a running process using Ctrl-Z and then launch another instance of the same process while the first one was suspended, demonstrating the ability to suspend and run multiple copies of a process in the same terminal.\

### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. I started by executing the following command to start the /challenge/run process:
   ```
   /challenge/run
   ```
   which gave the following message and output
```
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 12:50 pts/0    00:00:00 bash /challenge/run
root          84      82  0 12:50 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
```
3. To suspend the process, I pressed Ctrl-Z, which paused the current running process and sent it to the background.
   ```
   ^Z
   ```
   The terminal displayed:
   ```
   [1]+  Stopped                 /challenge/run
   ```

4. After suspending the first instance, I launched the process again:
   ```
   /challenge/run
   ```
   This time, the running process identified another instance of itself suspended in the background and the following output was displayed along with the flag for this challenge
```
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 12:50 pts/0    00:00:00 bash /challenge/run
root          89      65  0 12:50 pts/0    00:00:00 bash /challenge/run
root          91      89  0 12:50 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{oZ7BamnQk_4mQ3TmKQ5beDUwBm9.dVDN4QDLzAjN0czW}I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 12:50 pts/0    00:00:00 bash /challenge/run
root          89      65  0 12:50 pts/0    00:00:00 bash /challenge/run
root          91      89  0 12:50 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{oZ7BamnQk_4mQ3TmKQ5beDUwBm9.dVDN4QDLzAjN0czW}
```

### Flag
```
pwn.college{oZ7BamnQk_4mQ3TmKQ5beDUwBm9.dVDN4QDLzAjN0czW}
```

## Challenge 5: Resuming Processes
In this challenge, the task was to suspend a process using Ctrl-Z and then resume it with the `fg` command to bring it back to the foreground.


### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. I started by executing the `/challenge/run` command:
```
/challenge/run
```
The process requested to be suspended and resumed for successful completion.
```
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
```
3.  Using Ctrl-Z, I suspended the process:
```
[1]+  Stopped                 /challenge/run

```
4. After suspending the process, I resumed it with the `fg` command:
```
fg
```
which displayed the following output and gave the flag for this challenge.
```
/challenge/run
I'm back! Here's your flag:
pwn.college{Uc3PeMfC0Djo-OAibxMz8HxuacJ.dZDN4QDLzAjN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

### Flag
```
pwn.college{Uc3PeMfC0Djo-OAibxMz8HxuacJ.dZDN4QDLzAjN0czW}
```

## Challenge 6: Backgrounding processes
In this challenge the task was to suspend a process using Ctrl-Z, background it using the bg command, and then launch a second instance of the same process while the first continues running in the background.

### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. I started by executing the `/challenge/run` command:
   ```
   /challenge/run
   ```
   which displayed the following:
```
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
```
   
4. Then ,I suspended the process using Ctrl-Z:
   ```
   [1]+  Stopped                 /challenge/run
   ```
5. After suspension, I resumed the process in the background using the `bg` command:
   ```
   bg
   ```
   which gave the following message.
```
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
```
6. With the first instance running in the background, I launched a second instance of `/challenge/run`:
   ```
   /challenge/run
   ```
   which displayed the following and the flag for this challenge.
```
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{E5d-W6Qe35I86UorD22QwPnB-e7.ddDN4QDLzAjN0czW}
```

### Flag
```
pwn.college{E5d-W6Qe35I86UorD22QwPnB-e7.ddDN4QDLzAjN0czW}
```

## Challenge 7: Foregrounding Processes
In this challenge the task was to background a process and then bring it back to the foreground using the `fg` command.

### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. I started by executing the `/challenge/run` command:
   ```
   /challenge/run
   ```
   which displayed the following:
```
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
```
3. I suspended the running process using Ctrl-Z:
   ```
   [1]+  Stopped                 /challenge/run
   ```
4. After suspension, I sent it to the background with the `bg` command which displayed the following message.
```
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
```
5. To bring the backgrounded process back to the foreground, I used:
   ```
   fg
   ```
   which displayed the following message and prompted me to press Enter to get the flag and after pressing Enter,the flag for this challenge was revealed.
```
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{E-kCjpoYMMPTqKV0ZKGbnDASMbt.dhDN4QDLzAjN0czW}
```

### Flag
```
pwn.college{E-kCjpoYMMPTqKV0ZKGbnDASMbt.dhDN4QDLzAjN0czW}
```

## Challenge 8: Starting Backgrounded Processes
In this challenge, the goal was to start the `/challenge/run` process in the background and retrieve the flag.

### Method
1. Firstly, reconnected to pwn.college server via the SSH.
2. I started by executing the `/challenge/run` command:
   ```
   /challenge/run 
   ```
   which gave the following messaage.
   ```
   You've started me in the foreground! You must start me in the background (by
   appending '&' to the command) to get the flag!
   ```
3. Then, I ran the `/challenge/run` command with & at the end to start it in the background:
```
/challenge/run &
```
which gave the following message and the flag for this challenge
```
[1] 91



Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

hacker@processes~starting-backgrounded-processes:~$ Anyways! Here is your flag!
pwn.college{sfXAbmOSAftjkSKE2yOeqbWtGW5.dlDN4QDLzAjN0czW}

[1]+  Done                    /challenge/run
```

### Flag
```
pwn.college{sfXAbmOSAftjkSKE2yOeqbWtGW5.dlDN4QDLzAjN0czW}
```

## Challenge 9: Process Exit Codes
In this challenge ,the goal is to run the `/challenge/get-code` command, capture its exit code, and then use that exit code as an argument for the `/challenge/submit-code` command.

### Method
1.  Firstly, reconnected to pwn.college server via the SSH.
2.  Then I executed the /challenge/get-code command to retrieve the exit code:
    ```
    /challenge/get-code
    ```
3. Immediately after running the command, check the exit code by using the` $?` variable:
   ```
   echo $?
   ```
   The command displayed the exit code reurned by the command.
   ```
   74
   ```
4. Now, taking the exit code I just retrieved and usimg it as an argument for the /challenge/submit-code command I got the flag for this challenge.
   ```
   /challenge/submit-code 74
   ```
   Output:
   ```
   CORRECT! Here is your flag:
   pwn.college{wy3HndgmqJCBWtY14_U9AxQZTbA.dljN4UDLzAjN0czW}
   ```

###  Flag
```
pwn.college{wy3HndgmqJCBWtY14_U9AxQZTbA.dljN4UDLzAjN0czW}
```

   
   

   



   


   
   
   


