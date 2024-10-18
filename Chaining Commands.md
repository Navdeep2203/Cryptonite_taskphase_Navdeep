# Chaining Commands

## Challenge 1: Chaining with Semicolons
In this challenge , the goal  was to chain two commands using the `;` operator, which allows for the execution of multiple commands in sequence.

### Method
1. Firstly, connected to the pwn.college server via the SSH.
2. Then, I chained the two commands with semicolon in between:
   ```
   /challenge/pwn;/challenge/college
   ```
   After running the above command, both `/challenge/pwn` and `/challenge/college `executed successfully, and I received the flag.
   ```
   Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
   pwn.college{MSVZJn8BRd5OWHVKjNWHWIZwkoo.dVTN4QDLzAjN0czW}
   ```

### Flag
```
   pwn.college{MSVZJn8BRd5OWHVKjNWHWIZwkoo.dVTN4QDLzAjN0czW}
```

## Challenge 2: Your First Shell Script
In this  challenge, the task was to create a shell script to automate running two commands, `/challenge/pwn` and `/challenge/college`. I used VS Code to write, save, and execute the shell script.
### Method
1. I opened my VS Code workspace and created a new shell script file named `x.sh` using the VS Code Explorer.
2. In the `x.sh` file, I wrote the following commands:
   ```
   /challenge/pwn
   /challenge/college
   ```
3. After writing the commands, I saved the script in VS Code by pressing Ctrl + S.
4. I opened the integrated terminal in VS Code by selecting Terminal > New Terminal.
5. Then, I executed the script with the following command:
   ```
   bash x.sh
   ```
   The script ran both commands successfully, and I received the flag.
   ```
   Great job, you've written your first shell script! Here is the flag:
   pwn.college{U5QMFQq7VpcOwXtPWzEzkIM6KVn.dFzN4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{U5QMFQq7VpcOwXtPWzEzkIM6KVn.dFzN4QDLzAjN0czW}
```

## Challenge 3: Redirecting Script Output
In this challenge, I had to create a shell script that runs the `/challenge/pwn` and `/challenge/college` commands in sequence. The output from these commands needed to be piped into the `/challenge/solve` command, all in one step.

### Method
1. I created a shell script named `x.sh` in VS Code with the following content:
   ```
   /challenge/pwn
   /challenge/college
   ```
2. I opened the terminal in VS Code and ran the following command to execute the script and pipe its output into `/challenge/solve`:
   ```
   bash x.sh | /challenge/solve
   ```
   The output of the script was successfully passed to `/challenge/solve`, and I received the flag.
   ```
   Correct! Here is your flag:
   pwn.college{gf6PyICBNnEMFXxal0H0WG4Os4I.dhTM5QDLzAjN0czW}
   ```

### Flag
```
   pwn.college{gf6PyICBNnEMFXxal0H0WG4Os4I.dhTM5QDLzAjN0czW}
```

## Challenge 4: Executing Shell Scripts
In this challenge, the goal was to  create a shell script that invokes the `/challenge/solve` command and to execute it without manually invoking bash. By making the script executable, I was able to run it directly from the command line.

### Method
1. I created a file named `solve.sh` with the following content:
   ```
   /challenge/solve
   ```
2. Initially, when I tried to run the script using `./solve.sh`, I encountered a "Permission denied" error. To resolve this, I used the following command to change the file permissions and make it executable
   ```
   chmod +x solve.sh
   ```
3. After making the script executable, I ran it using:
   ```
   ./solve.sh
   ```
   The script executed successfully and invoked the `/challenge/solve` command, returning the expected output.
   ```
   Congratulations on your shell script execution! Your flag:
   pwn.college{w_j1tNFrIi1WF9SZd6lvqL3f5cc.dRzNyUDLzAjN0czW}
   ```

### Flag
```
pwn.college{w_j1tNFrIi1WF9SZd6lvqL3f5cc.dRzNyUDLzAjN0czW}
```


   







