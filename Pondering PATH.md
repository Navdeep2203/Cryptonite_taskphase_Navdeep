# Pondering PATH

## Challenge 1: 
In this challenge, the task was to prevent the `/challenge/run` program from finding and executing the `rm` command, which would delete the flag file. By manipulating the PATH variable, I was able to achieve this.

### Method
1. Firstly, I connected to the pwn.college server via the SSH.
2. Initially, I checked the current value of the `PATH` variable to understand where the shell searches for commands.
   ```
   echo $PATH
   ```
3. I set the `PATH` variable to an empty string to prevent the shell from locating any commands:
   ```
   PATH=""
   ```
4. Then, I ran the `/challenge/run` program:
   ```
   /challenge/run
   ```
   The `/challenge/run` program attempted to execute rm but failed due to the blank `PATH`, allowing me to keep the flag.
   ```
   /run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    hacker@path~the-path-variable:~$ PATH=""
    hacker@path~the-path-variable:~$ /challenge/run
    Trying to remove /flag...
    /challenge/run: line 4: rm: No such file or directory
    The flag is still there! I might as well give it to you!
    pwn.college{0VEkimNBfGPbvhmtvieReWNhPyD.dZzNwUDLzAjN0czW}
   ```

### Flag
```
pwn.college{0VEkimNBfGPbvhmtvieReWNhPyD.dZzNwUDLzAjN0czW}
```

## Challenge 2: Setting PATH
In this challenge, I needed to modify the PATH variable to include the `/challenge/more_commands/` directory so that the `/challenge/run` program could successfully locate and execute the win command.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. I started by checking the current value of the PATH variable:
   ```
   echo $PATH
   ```
   which showed
   ```
3. I updated the `PATH` variable to point to the directory containing the `win` command:
   ```
   PATH=/challenge/more_commands/
   ```
4. I then ran the `/challenge/run` program:
   ```
   /challenge/run
   ```
   The program successfully located the `win `command in the specified directory and executed it, indicating that I completed the challenge.
   ```
   Invoking 'win'....
   Congratulations! You properly set the flag and 'win' has launched!
   pwn.college{4ercGtt5VUr5CEPer-oyTP2XBGM.dVzNyUDLzAjN0czW}
   ```

### Flag
```
pwn.college{4ercGtt5VUr5CEPer-oyTP2XBGM.dVzNyUDLzAjN0czW}
```

## Challenge 3: Adding Commands
In this challenge, the task was to create a custom shell script named `win` that would allow the `/challenge/run` command to retrieve a flag from the system. The win command had to be executable and placed in a directory that was included in the `PATH` environment variable.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then, I created a new file named win:
   ```
   touch win
   ```
3.  I wrote the command to retrieve the flag using `cat` into the `win` script:
   ```
   echo "cat /flag" > /home/hacker/win
```
4. I changed the permissions of the win script to make it executable:
   ```
   chmod a+x /home/hacker/win
   ```
5.  To enable `/challenge/run` to find the win command, I added the directory containing win to the PATH:
   ```
   PATH=$PATH:/home/hacker
```
6.  Finally, I executed the `/challenge/run` command to invoke the win script and retrieve the flag:
   ```
   /challenge/run
   ```
   Output: 
   ```
   Invoking 'win'....
pwn.college{EHUHWaPAuQan3MIS432lTleWxfJ.dZzNyUDLzAjN0czW}
```

### Flag
```
pwn.college{EHUHWaPAuQan3MIS432lTleWxfJ.dZzNyUDLzAjN0czW}
```

## Challenge 4: Hijacking Commands
In this challenge, the goal was to hijack the `rm `command to prevent it from deleting the flag and instead execute a different command to display the flag.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. I began by creating a new file named `rm` in my home directory.
   ```
   touch rm
   ```
3.  I then added a command to this file that would display the flag instead of deleting it.
   ```
   echo "cat /flag" > /home/hacker/rm
```
4. After writing the command, I made the `rm` file executable.
   ```
   chmod a+x /home/hacker/rm
   ```
5. To ensure my custom `rm `command would be used instead of the system one, I updated the PATH environment variable to prioritize my home directory.
   ```
   export PATH=/home/hacker:$PATH
   ```
6.  I checked that the correct` rm` command was being called.
   ```
   which rm
```
Output:
```
/home/hacker/rm
```

7.  Finally, I executed the challenge, which attempted to remove the flag but instead gave me the flag.

   ```
   /challenge/run
   ```
Output: 
```
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{Acq8Ss8veAmDW_w_QH2fUk9lRHp.ddzNyUDLzAjN0czW}
```

### Flag
```
pwn.college{Acq8Ss8veAmDW_w_QH2fUk9lRHp.ddzNyUDLzAjN0czW}
```






   




