# Untangling Users

## challenge 1: Becoming root with su
 In this challenge, I explored the su (switch user) command, which allows a user to elevate their privileges to that of the root user in Linux systems. While su is an older utility and less commonly used today due to modern alternatives like sudo, it remains an important tool to understand.

### Method
1. Firstly, connected to the pwn.college server via the SSH.
2. I attempted to use the su command without the root password to check for authentication failure:
   ```
   su
   Password:
   su: Authentication failure
   ```
3. For this challenge, I was provided with the root password: hack-the-planet. I entered the password to switch to the root user:
   ```
   su
   Password: [entered root password]
   root@users~becoming-root-with-su:/home/hacker#
   ```
4. Once I had root access, I retrieved the flag by executing the following command:
   ```
   cat /flag
   ```

### Flag
```
pwn.college{w3bItQZBvNZjzNMp5wmDEiv4T7I.dVTN0UDLzAjN0czW}
```

## Challenge 2: Other users with su
In this challenge, I learned to use the su (switch user) command to switch from the current user to another user account, specifically to the `zardus` user. 

### Method 
1. Firstly, reconnected to the pwn.college server via the SSH.
2. To begin, I used the `su` command followed by the username zardus to switch users. I was prompted for the password, which was provided as `dont-hack-me`. I entered the command:
   ```
   su zardus
   Password: [entered zardus password]
   ```
 After successfully entering the password, I was switched to the zardus user.

3. Once I was logged in as the zardus user, I executed the required command:
```
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
```
Upon running the command, I received a  message along with the flag:
```
Congratulations, you have become Zardus! Here is your flag:
pwn.college{oY0QwhZUvEtnyZonPmyh53XHBeX.dZTN0UDLzAjN0czW}
```

### Flag
```
pwn.college{oY0QwhZUvEtnyZonPmyh53XHBeX.dZTN0UDLzAjN0czW}
```

## Challenge 3: Cracking passwords
In this challenge, I worked on cracking the password hashes from a simulated leaked shadow file. The file was located at `/challenge/shadow-leak`, and it contained password hashes for users, including` zardus`. My objective was to crack the hash for `zardus`, use `su` to switch to the user, and run a specified command to retrieve the flag.

## Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. I initiated the challenge by using the `john` command, a popular password-cracking tool. I targeted the shadow file at` /challenge/shadow-leak`:
   ```
   john /challenge/shadow-leak
   ```
John the Ripper successfully loaded the password hash for the zardus user.
3.  After about 21 seconds of cracking, John revealed the password for zardus as aardvark.
```
aardvark         (zardus)
```

4. To verify and display all cracked passwords, I used the following command:
   ```
   john --show /challenge/shadow-leak
   ```
   Output
   ```
   hacker:NO PASSWORD:20000:0:99999:7:::
   zardus:aardvark:20013:0:99999:7:::
   ```

5. With the password `aardvark` in hand, I used the su command to switch to the `zardus` user:\
   ```
   su zardus
   ```
   I entered the cracked password and successfully became the `zardus` user.

6.  After switching to the `zardus` user, I executed the challenge command:
    ```
    /challenge/run
    ```
    Output:
    ```
    Congratulations, you have become Zardus! Here is your flag:
    pwn.college{8X1HwG1DxI8XqMeBERUoYdMpLUl.ddTN0UDLzAjN0czW}
    ```

### Flag
```
    pwn.college{8X1HwG1DxI8XqMeBERUoYdMpLUl.ddTN0UDLzAjN0czW}
```

## Challenge 4: Using sudo
In this challenge, I utilized the sudo command to elevate privileges and retrieve the flag. The challenge focused on how sudo allows specific commands to be executed as the root user, without needing to switch to the root account fully, which is a more flexible and secure approach compared to su.

### Method
1. First, I verified the current user by running the whoami command:
   ```
   whoami
   ```
   Output:
   ```
   hacker
   ```
   This confirmed that I was logged in as the user `hacker`.
2. To retrieve the flag, I used `sudo` to execute the `cat` command with elevated privileges. The `cat` command was used to read the contents of the flag file:
   ```
   sudo cat /flag
   ```
   which successfully gave the flag for this challenge.

### Flag
```
pwn.college{4NBHhMfXRz2uBUDB2QNqSOprAl6.dhTN0UDLzAjN0czW}
```



   
