# Digesting Documentation

## Challenge 1: Learning from Documentation
 In this challenge, the task was to learn how to correctly pass arguments to a program by understanding its documentation. The program `/challenge/challenge` was to be run with the correct argument  in order to retrieve the flag. The challenge involved figuring out the correct argument based on provided documentation.

### Method
1. Firstly, I connected to the pwn.college server via the SSH.
   ```
   ssh -i /home/navdee2203/key hacker@dojo.pwn.college

   ```
2. The challenge provided documentation for the program `/challenge/challenge`, which indicated that the correct argument to use was `--giveflag`.
   So I ran the program using the following command with the specified argument.
   ```
   /challenge/challenge --giveflag
   ```
   which gave me the following output.
   ```
   Correct argument! Here is your flag:
   pwn.college{kzPUybdZGj2ZIvK1x5dCqhkM2r6.dRjM5QDLzAjN0czW}
   ```

### Flag
```
pwn.college{kzPUybdZGj2ZIvK1x5dCqhkM2r6.dRjM5QDLzAjN0czW}
```

## Challenge 2: Learning Complex Usage
In this challenge, the task was to learn about commands that accept arguments for their arguments, as demonstrated by the `--printfile` argument in the `/challenge/challenge` program.

### Method 
1. Reconnected to the pwn.college server via the SSH.
2. The documentation for the `/challenge/challenge` program explained that the command takes the `--printfile` argument, which itself requires an additional argument specifying the path of the file to print.
   So I  invoked the `/challenge/challenge` command with the appropriate argument pointing to the flag file.
   ```
   /challenge/challenge --printfile /flag
   ```
   which gave me the following output and the flag to proceed.
   ```
   Correct argument! Here is the /flag file:
   pwn.college{UX5t-3qMPVX5zZf7AVMZNBTfpk1.dVjM5QDLzAjN0czW}
   ```
### Flag
```
pwn.college{UX5t-3qMPVX5zZf7AVMZNBTfpk1.dVjM5QDLzAjN0czW}
```



   
   
