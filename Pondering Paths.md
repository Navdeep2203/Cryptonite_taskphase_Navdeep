# Pondering Paths Module

## Challenge 1 : The Root
In this challenge I was tasked to run a program located in the root directory of the filesystem using its absolute path and get the flag to proceed further.

In Linux, the filesystem starts with a root directory which is represented by **/**. 

So I was required to run a program named **pwn** which was placed directly under the root directly. 

To execute it I had to use the absolute path, which was **/pwn** here.

###  Method
1. I started the challenge by connecting to pwn.college server via the SSH, which I did with the command below :
   ```
   ssh -i /home/navdee2203/key hacker@dojo.pwn.college

   ```
2. When connected I was shown the following prompt :
   ```
   hacker@paths~the-root:~$

   ```
3. In order to run the program, I typed the absolute path of the program:
   ```
   /pwn
   ```
   which then returned me the flag to proceed.

### Flag

```
pwn.college{AD6bdo2i6EzcSY3em9oUvlu2E5O.dhzN5QDLzAjN0czW}

```



## Challenge 2: Program and Absolute Paths 

In this challenge, the task was to run a program named **run** which is located in the **/challenge** directory, by using its absolute path. 

In the Linux system, every file and directory has a specific path. Here the root directory is represented as **/** and within there's a **challenge** directory where the **run** program is stored, whose absolute path is ** /challenge/run**.


### Method 

1. Firstly, I again reconnected to the pwn—college server via the SSH key.
2. After connecting, I was required to access the ```run``` program located in the ```/challenge``` directory. The absolute path of the program was ```/challenge/run```.
3. To run the program, I entered the following command in the terminal:
   ```
   /challenge/run
   ```
   which executed the program successfully and returned the flag.

### Flag 
```
pwn.college{gDrkZj3ch7MrJWeTc7ukUFE_N2e.dVDN1QDLzAjN0czW}
```

## Challenge 3: Position thy self
In this challenge, the task was to run a program named **run**, located in the ```/challenge``` directory, using its absolute path from a specific directory and getting the flag to proceed further.

It was required to navigate to a specific directory ```/var/lib/apt/lists/``` and execute the program from there to get the flag.

### Method
1. Firstly, I again reconnected to the pwn.college server using the SSH.
2. So, initially I tried running the program from my current directory with the command
   ```
   /challenge/run/

   ```
   But I received an error message
   ```
   Incorrect...  
   You are not currently in the /var/lib/apt/lists directory.
   Please use the `cd` utility to change directory appropriately.

   ```
3. Then I used the cd command and navigated to the current directory which popped up in the error message.
   ```
   cd /var/lib/apt/lists

   ```
4. After reaching the current directory, I successfully ran the program:
   ```
   /challenge/run
   ```
   which gave me the following output and the flag to proceed.
   ```
   Correct!!!
   /challenge/run is an absolute path, invoked from the right directory!
   ```

### Flag
```
 pwn.college{YEELLqfLO8m1Goz2XL8WKssN2Dz.dZDN1QDLzAjN0czW}
```


## Challenge 4 : Position elsewhere 
In this challenge, the task was the same as  Challenge 3 instead the program was to be navigated from a specific directory(/sys) and run the program from there to get the flag.

### Method 
1. Firstly, again reconnected to pwn.college server using the SSH.
2. Initially I tried running the program from an incorrect directory.
   ```
   /challenge/run
   ```
   which then gave me the error message
   ```
   Incorrect...
   You are not currently in the /sys directory.
   Please use the `cd` utility to change directory appropriately.
   ```
3. So then I navigated to the correct directory using the cd command.
   ```
   cd /sys
   ```
4. Once I was in the correct directory, I ran the program again
   ```
   /challenge/run
   ```
   which gave me the output and the flag to proceed.
   ```
   Correct!!!
   /challenge/run is an absolute path, invoked from the right directory!
   ```
   ### Flag
   ```
   pwn.college{guizXLGRe5J1ts3TZCmnGwSbK5M.ddDN1QDLzAjN0czW}

   ```

## Challenge 5: Position yet elsewhere

In this challenge the task was again the same as challenge 3, instead the program was to be navigated from a specific directory(/temp) and run the program from there to get the flag.

### Method
1. Firstly, again reconnected to pwn.college server via the SSH key.
2. Initially, I tried running the program from an incorrect directory
   ```
   challenge/run
   ```
   It gave the following message
   ```
   Incorrect...
   You are not currently in the /tmp directory.
   Please use the `cd` utility to change directory appropriately.
   ```
3. So I navigated to the correct directory ( /tmp ) using the `cd` command.
   ```
   cd /tmp
   ```
4. After changing to the correct directory, I successfully ran the program.
   ```
   /challenge/run
   ```
   which gave me the following output
   ```
   Correct!!!
   /challenge/run is an absolute path, invoked from the right directory!
   ```
### Flag
```
pwn.college{gvbolT1UhfG9W4WcU7u5scMIte0.dhDN1QDLzAjN0czW}
```

## Challenge 6 : implicit relative paths, from /
In this challenge, the task was to run a program located at `challenge/run` using a relative path while having the cwd (current working directory) set to the root directory(`/`). This task was to understand the difference between absolute paths and relative paths.

### Method
1. Firstly I again reconnected to the pwn.college server via the SSh.
2. To use the relative path, I changed my correct working directory ( cwd) to the root directory(`/`) using the `cd` command:
```
cd /
```
3. From the root directory , then I ran the program using the relative path:
   ```
   challenge/run
   ```
   The program ran successfully and returned the flag to proceed further.
   ```
   Correct!!!
   challenge/run is a relative path, invoked from the right directory!
   ```
### Flag
```
   pwn.college{Ars4NoBHMyw_8Yr6bTuTesl8_5F.dlDN1QDLzAjN0czW}
```

## Challenge 7 : Explicit relative paths from /
In this challenge , the task was to use explicit relative paths to run the program located at `/challenge/run`. This task emphasized the use of the `.` symbol to refer to the current directory and explore its implications in path navigation.

### Method
1. Again, I reconnected to the pwn.college server via the SSH.
2. To use the relative path, I changed my correct working directory ( cwd) to the root directory(`/`) using the `cd` command:
```
cd /
```

3. Then I ran the program using the explicit relative path
```
./challenge/run
```
which gave me the following output and the flag to proceed. 
```
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
```

### Flag
```
pwn.college{QlbNBpaPpoUXrdYcali8k-GSw7k.dBTN1QDLzAjN0czW}

```

## Challenge 8 : implicit relative path 
In this challenge, the task was to execute a program named `run` located in the `/challenge ` directory using relative path.  The challenge helped to understand  Linux's behavior when it comes to executing programs in the current directory, particularly why naked paths (like run) won't work and how to resolve this issue by using the `./` notation. 

### Method 
1. Again, I reconnected to pwn.college server via the SSH.
2. After connecting I navigated to the `/challenge` directory using the `cd` command.
   `
   cd /challenge
   `
3. Then I executed the program by specifying the relative path  using `./`.
   ```
   ./run
   ```
   The program ran successfully, and I got the output and the flag to proceed further.
   ```
   Correct!!!
   ./run is a relative path, invoked from the right directory!
   ```
### Flag
```
pwn.college{0asfAPZFcoE2YEQWkPcEV0elI5_.dFTN1QDLzAjN0czW}
```


## Challenge 9: home sweet home 
In this challenge, the goal was to use the home directory to write a file containing the flag by executing the program located at `/challenge/run`. This challenge emphasized understanding the use of absolute paths, specifically within the context of the home directory and the constraints regarding the argument provided to the command.

### Method
1. Firstly, I connected to the pwn.college server via the SSH.
2. After connecting, I executed the program to write the flag to a file within my home directory.
   ```
   /challenge/run ~/f
   ```
   where the argument provided was `~/f` which expands to `/home/hacker/f`

   I got the output as :
   ```
   Writing the file to /home/hacker/f!
   ... and reading it back to you:
   pwn.college{AVoGnTXdmMJZWeGsX1bAKpV6UMm.dNzM4QDLzAjN0czW}
   ```
   and got the flag.

### Flag
```
pwn.college{AVoGnTXdmMJZWeGsX1bAKpV6UMm.dNzM4QDLzAjN0czW}
```


