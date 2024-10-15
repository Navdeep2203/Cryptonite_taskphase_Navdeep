# Shell Variables 

## Challlenge 1: Printing Variables
In this challenge the goal was to print the value stored in a shell variable named `FLAG`. To solve this, we were required to use basic shell commands, specifically echo, which prints out text or variable values.

### Method 
1. Firstly, I connected to the pwn.college server via the SSH using the following command:
   ```
   ssh -i /home/navdee2203/key hacker@dojo.pwn.college
   ```
2. To print the value of the `FLAG` variable, I used the following command:
   ```
   echo $FLAG
   ```
   where 
   * The `FLAG` variable contains the flag, and we need to print it out using a shell command and
   * The `echo` command is used because it can output both plain text and variable values by using the `$` symbol before the variable name.
  
     which gave the flag to proceed.
   ```
   pwn.college{4tei_YISQk9maSfwUua1RssDv2H.ddTN1QDLzAjN0czW}
   ```

   ### Flag
   ```
   pwn.college{4tei_YISQk9maSfwUua1RssDv2H.ddTN1QDLzAjN0czW}
   ```

## Challenge 2: Setting Variables
In this challenge the goal was to set a shell variable named `PWN` to the value `COLLEGE` and then retrieve the flag which required clear understanding of correct syntax for variable assignment in the shell.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then, to proceed with this challenge, I assigned the value COLLEGE to the PWN variable using the following command:
   ```
   PWN=COLLEGE
   ```
   After setting the variable correctly, the following output was displayed and the flag was given to proceed.
   ```
   You've set the PWN variable properly! As promised, here is the flag:
   pwn.college{sZdlhtrWRwia638fK1p6uSd05kh.dlTN1QDLzAjN0czW}
   ```
### Flag
```
pwn.college{sZdlhtrWRwia638fK1p6uSd05kh.dlTN1QDLzAjN0czW}
```

## Challenge 3: Multi Word Variables
In this challenge ,the goal  was to correctly set the `PWN` variable to the multi-word string `COLLEGE YEAH`. This required an understanding of how to handle spaces within variable values using quoting in the shell.

### Method
1.  Firstly, reconnected to the pwn.college server via the SSH.
2.  Then, to set the `PWN` variable to `COLLEGE YEAH`, the following command was used:
  ```
   PWN="COLLEGE YEAH"
```
because to set a variable to a value containing spaces, the entire value needs to be enclosed in quotes (either single or double quotes)which allows the shell to treat the value as a single entity.

Output:
```
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UrRj8yTMTc4DHz4isvFVs0jbheT.dBjN1QDLzAjN0czW}
```

### Flag
```
pwn.college{UrRj8yTMTc4DHz4isvFVs0jbheT.dBjN1QDLzAjN0czW}
```

## Challenge 4: Exporting Variables
In this challenge, the task was to set two variables,`PWN` and `COLLEGE`, with specific instructions regarding export behavior:

The `PWN` variable must be exported and set to the value `COLLEGE`.
The `COLLEGE` variable must be set to the value PWN but not exported.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then ,the first step was to set the `COLLEGE` variable to the value `PWN` without exporting it which ensures that it remains local to the current shell. So I ran the following command:
 ```
COLLEGE=PWN
```
which displayed the following message 
```
You've set the COLLEGE variable to the proper value!
```

3. Then ,the next step was to set and export the `PWN` variable with the value `COLLEGE` which allows the child process /challenge/run to inherit the PWN variable:
   ```
   export PWN=COLLEGE
   ```
   which displayed the following message
   ```
   You've set the PWN variable to the proper value!
   You've set the COLLEGE variable to the proper value!
   ```
5. After setting the variables correctly, I invoked the challenge command to complete the task:
   ```
   /challenge/run
   ```
   which gave the following output and the flag to proceed.
   ```
   CORRECT!
   You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
   job! Here is your flag:
   pwn.college{Uu90d5Klt_fpj5KMM0_ybYXXOO0.dJjN1QDLzAjN0czW}
   You've set the PWN variable to the proper value!
   You've set the COLLEGE variable to the proper value!
   ```

### Flag
```
   pwn.college{Uu90d5Klt_fpj5KMM0_ybYXXOO0.dJjN1QDLzAjN0czW}
```

## Challenge 5: 


   
   

   


   
   
