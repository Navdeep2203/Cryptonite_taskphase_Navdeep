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



## Challenge 2 : Program and Absolute Paths 

In this challenge, the task was to run a program named **run** which located in the **/challenge** directory, by using its absolute path. 

In Linux system, every file and a directory has a speciific path. Here the root directory is represented as **/** and within there's a **challenge** directory where the **run** program is stored, whose absolute path is ** /challenge/run**.


### Method 

1. Firstly, I again reconnected to the pwn.college server via the ssh key.
2. After connecting, I was required to access the ```run``` program which was located in the ```/challenge``` directory. The absolute path of the program was ```/challenge/run```.
3. To run the program, I entered the follwing command in the terminal:
   ```
   /challenge/run
   ```
   which executed the program successfully and returned the flag.

### Flag 
```
pwn.college{gDrkZj3ch7MrJWeTc7ukUFE_N2e.dVDN1QDLzAjN0czW}
```
