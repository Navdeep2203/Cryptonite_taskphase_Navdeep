# Ponddering PATH

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


