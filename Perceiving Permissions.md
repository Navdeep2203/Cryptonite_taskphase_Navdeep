# Perceiving Permissions

## Challenge 1: Changing File Ownership
In this challenge, the task was to understand file ownership and permissions in Linux by changing the ownership of the `/flag` file from the root user to the hacker user. This allowed access to a file that was previously restricted, showcasing the importance of file permissions in system security.

### Method
1. Firstly, connected to the pwn.college server via SSH.
2. Then, I began by checking the permissions of the `/flag` file to confirm its ownership and access rights.
   ```
   ls -l /flag
   ```
   which displayed:
   ```
   -r-------- 1 root root 58 Oct 16 13:44 /flag
   ```
   indicating that the file was owned by root and had no read permissions for the hacker user.

3. I attempted to read the contents of the `/flag` file:
   ```
   cat /flag
   ```
   which denied permission:
   ```
   cat: /flag: Permission denied
   ```
4. To gain access, I used the `chown` command to change the owner of the `/flag` file to `hacker`:
   ```
   chown hacker /flag
   ```
5. After changing the ownership, I checked the permissions again:
   ```
   -r-------- 1 hacker root 58 Oct 16 13:44 /flag
   ```
   This confirmed that the ownership had been successfully changed to hacker.

6. Finally, I was able to read the contents of the `/flag` file:
   ```
   cat /flag
   ```
   Output:
   ```
   pwn.college{0Dj0Oz9cbP2HMOFpsGWVGfEX2b5.dFTM2QDLzAjN0czW}
   ```

### Flag
```
pwn.college{0Dj0Oz9cbP2HMOFpsGWVGfEX2b5.dFTM2QDLzAjN0czW}
```

## Challenge 2: Groups and Files 
In this challenge ,the goal was to change the group ownership of a restricted flag file to enable access to its contents. This challenge focused on understanding and manipulating file permissions and group ownership in a Linux environment. 

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then, I verified my current user and group memberships using the `id` command:
   ```
   id
   ```
   which gave the output as;
   ```
   uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
   ```
   indicating that the current user is hacker, and this user belongs to the hacker group.
3. Next, I checked the permissions for the `/flag` file using the `ls -l` command:
   ```
   ls -l /flag
   ```
   Output:
   ```
   -r--r----- 1 root root 58 Oct 16 13:53 /flag
   ```
   showing that the file is owned by the root user and the root group. The permissions indicate that the owner (root) has read access, while the group and others have no access to this file.

4. Since I did not have permission to read the `/flag` file, I needed to change its group ownership to `hacker`. I executed the `chgrp` command as follows:
   ```
   chgrp hacker /flag
   ```
5. After changing the group ownership, I confirmed the new group ownership by running the `ls -l` command again:
   ```
   ls -l /flag
   ```
   Output:
   ```
   -r--r----- 1 root hacker 58 Oct 16 13:53 /flag
   ```
6. With the group ownership changed, I was now able to read the contents of the flag file. I executed the following command:
   ```
   cat /flag
   ```
   Output:
   ```
   pwn.college{Mp_cSgrehMUmKyq9HgrK6xkuiBi.dFzNyUDLzAjN0czW}
   ```

### Flag
```
pwn.college{Mp_cSgrehMUmKyq9HgrK6xkuiBi.dFzNyUDLzAjN0czW}
```

## Challenge 3: Fun with Group Names
In this challenge, the goal was to identify the randomized group that the user belongs to and change the group ownership of the `/flag` file to that group, allowing access to read the flag.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then,  I executed the `id` command to determine my current user ID (UID), group ID (GID), and the groups I belong to.
   ```
   id
   ```
   Output:
   ```
   uid=1000(hacker) gid=1000(grp21636) groups=1000(grp21636)
   ```
   This confirmed that I am a member of the `grp21636` group.

3. Next, I checked the permissions of the `/flag` file to understand the ownership and access permissions.
   ```
   -r--r----- 1 root root 58 Oct 16 14:02 /flag
   ```
   showing that the file is owned by the root user and group, and the hacker user does not have permission to read it.

4. Then, I used the `chgrp` command to change the group ownership of the `/flag` file to `grp21636`, which is the group I belong to.
   ```
   chgrp grp21636 /flag
   ```
5. After changing the group ownership, I verified that the change was successful.
   ```
   ls -l /flag
   ```
   Output:
   ```
   -r--r----- 1 root grp21636 58 Oct 16 14:02 /flag
   ```
6. With the new group ownership in place, I attempted to read the contents of the flag file.
   ```
   cat /flag
   ```
   Output:
   ```
   pwn.college{oSqNl_MjZW2fTAAgptnRXU0sfr5.dJzNyUDLzAjN0czW}
   ```

### Flag
```
pwn.college{oSqNl_MjZW2fTAAgptnRXU0sfr5.dJzNyUDLzAjN0czW}
```

## Challenge 4: Changing Permissions
In this challenge, the task was to modify the the permissions of the `/flag`file to make it readable, even though it is owned by the root user. The challenge required  to change the file's permissions using the chmod` command to successfully read its contents.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2.  I began by listing the permissions of the `/flag` file to understand its current access rights:
   ```
   ls -l /flag
```
Output:
```
-r-------- 1 root root 58 Oct 17 16:52 /flag
```
only the root user had read access, while neither the group nor other users had any access.

3. I attempted to add read permission for the user (root) by running the following command:
   ```
   chmod u+r /flag
   ```
   After this, I checked the permissions again:
   ```
   ls -l /flag
   ```
   Output:
   ```
   -r-------- 1 root root 58 Oct 17 16:52 /flag
   ```
   However, the permissions remained unchanged.
4. I then tried adding read permission for all users using a+r:
   ```
   chmod a+r /flag
   ```
   After this I checked the permissions again:
   ```
   ls -l /flag
   ```
   Output:
   ```
   -r--r--r-- 1 root root 58 Oct 17 16:52 /flag
   ```
   Now, all users had read access to the file.

5. Finally, I was able to read the contents of the `/flag` file and get the flag for this challenge.
   ```
   cat /flag
   ```

### Flag
```
pwn.college{AExuM9I1sGeqfAI2CBID6r31lNE.dNzNyUDLzAjN0czW}
```

## Challenge 5: Executable Files
In this challenge, the goal was to get a flag from a file located at `/challenge/run`. However, the file initially lacked execute permissions, preventing it from being run. My task was to modify the permissions to allow execution and retrieve the flag.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. I started by listing the permissions of the file `/challenge/run` using the `ls -l` command:
   ```
   ls -l /challenge/run
   ```
   Output:
   ```
   -r--r--r-- 1 hacker hacker 32 Jul  4 06:37 /challenge/run
   ```
   which meant that the file had only read permissions (r--r--r--) for the owner, group, and others. No one had the execute permission, which was required to run 
   the file.
3. To make the file executable by the user, I applied the `chmod` command to add execute permission (u+x):
   ```
   chmod u+x /challenge/run
   ```
4. After adding the execute permission, I verified that the permissions had been updated successfully:
   ```
   ls -l /challenge/run
   ```
   Output:
   ```
   -r-xr--r-- 1 hacker hacker 32 Jul  4 06:37 /challenge/run
   ```
   The user (hacker) now had execute permission (r-x), while the group and others still had only read access (r--).

5. With the correct permissions in place, I was able to run the program and retrieve the flag:
   ```
   /challenge/run
   ```
   Output:
   ```
   hacker@permissions~executable-files:~$ /challenge/run
   Successful execution! Here is your flag:
   pwn.college{8e-8FnAtxhagSaDadqQjb0vXC7c.dJTM2QDLzAjN0czW}
   ```

### Flag
```
 pwn.college{8e-8FnAtxhagSaDadqQjb0vXC7c.dJTM2QDLzAjN0czW}
```

## Challenge 6: Permission Tweaking Practice
In this challenge, the task was to change the permissions of the `/challenge/pwn` file multiple times according to specific instructions. The goal was to successfully adjust the permissions eight times in a row, allowing me to eventually make the `/flag` file readable for myself.

### Method 
1. Firstly, reconnected to the  pwn.college server via the SSH.
2. I started by launching the challenge using the following command:
   ```
   /challenge/run
   ```
   which showed me the first round of changing permissions.
   ```
   Current permissions of "/challenge/pwn": rw-r--r--
   * the user does have read permissions
   * the user does have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": ---r--r--
   - the user doesn't have read permissions
   - the user doesn't have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   ```

3. So accordingly, I set the required permissions for the user to not have read and write permissions:
   ```
   chmod u-rw /challenge/pwn
   ```
   which displayed the next round for changing permissions.
   ```
   Current permissions of "/challenge/pwn": ---r--r--
   - the user doesn't have read permissions
   - the user doesn't have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": r-xr--r--
   * the user does have read permissions
   - the user doesn't have write permissions
   * the user does have execute permissions
   * the group does have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   ```
4. So accordingly I changed the permissions of the user to have  read and execute permissions.
   ```
   chmod u+rx /challenge/pwn
   ```
   which displayed the next round of changing permissions.
   ```
   You set the correct permissions!
   Round 2 (of 8)!
   
   Current permissions of "/challenge/pwn": r-xr--r--
   * the user does have read permissions
   - the user doesn't have write permissions
   * the user does have execute permissions
   * the group does have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": r-x---r--
   * the user does have read permissions
   - the user doesn't have write permissions
   * the user does have execute permissions
   - the group doesn't have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   ```
5. So now I changed the permissions of the group to not have read permission.
   ```
   chmod g-r /challenge/pwn
   ```
   which displayed the next round of changing permissions.
   ```
   You set the correct permissions!
   Round 3 (of 8)!
   
   Current permissions of "/challenge/pwn": r-x---r--
   * the user does have read permissions
   - the user doesn't have write permissions
   * the user does have execute permissions
   - the group doesn't have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": ---------
   - the user doesn't have read permissions
   - the user doesn't have write permissions
   - the user doesn't have execute permissions
   - the group doesn't have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   ```
6. So now I changed the permissions of all to not read and execute permissions.
   ```
   chmod a-rx /challenge/pwn
   ```
   which displayed the next round of changing permissions.
   ```
   You set the correct permissions!
   Round 4 (of 8)!
   
   Current permissions of "/challenge/pwn": ---------
   - the user doesn't have read permissions
   - the user doesn't have write permissions
   - the user doesn't have execute permissions
   - the group doesn't have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   - the world doesn't have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": -------w-
   - the user doesn't have read permissions
   - the user doesn't have write permissions
   - the user doesn't have execute permissions
   - the group doesn't have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   ```
7. So now I changed the permissions of the world to have write permissions.
   ```
   chmod o+w /challenge/pwn
   ```
   which diisplayed the next set of permissions.
   ```
   You set the correct permissions!
   Round 5 (of 8)!
   
   Current permissions of "/challenge/pwn": -------w-
   - the user doesn't have read permissions
   - the user doesn't have write permissions
   - the user doesn't have execute permissions
   - the group doesn't have read permissions
   - the group doesn't have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": rw-rw--w-
   * the user does have read permissions
   * the user does have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   * the group does have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   ```
8. So now I changed the permissions of the user and group to read and write permissions.
   ```
    chmod u+rw,g+rw /challenge/pwn
   ```
   which displayed the next set of permissions.
   ```
   You set the correct permissions!
   Round 6 (of 8)!
   
   Current permissions of "/challenge/pwn": rw-rw--w-
   * the user does have read permissions
   * the user does have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   * the group does have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": rw-rw-rw-
   * the user does have read permissions
   * the user does have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   * the group does have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   ```
9. So now I changed the permissions of the world to have the read permission.
    ```
    chmod o+r /challenge/pwn
    ```
    which displayed the next set of permissions.
   ```
   You set the correct permissions!
   Round 7 (of 8)!
   
   Current permissions of "/challenge/pwn": rw-rw-rw-
   * the user does have read permissions
   * the user does have write permissions
   - the user doesn't have execute permissions
   * the group does have read permissions
   * the group does have write permissions
   - the group doesn't have execute permissions
   * the world does have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   
   Needed permissions of "/challenge/pwn": rw--w--w-
   * the user does have read permissions
   * the user does have write permissions
   - the user doesn't have execute permissions
   - the group doesn't have read permissions
   * the group does have write permissions
   - the group doesn't have execute permissions
   - the world doesn't have read permissions
   * the world does have write permissions
   - the world doesn't have execute permissions
   ```
10. So now I changed the permissions of the group and world to have read permission.
    ```
     chmod g-r,o-r /challenge/pwn
    ```
    which displayed:
    ```
    You set the correct permissions!
      You've solved all 8 rounds! I have changed the ownership
      of the /flag file so that you can 'chmod' it. You won't be able to read
      it until you make it readable with chmod!
      
      Current permissions of "/flag": ---------
      - the user doesn't have read permissions
      - the user doesn't have write permissions
      - the user doesn't have execute permissions
      - the group doesn't have read permissions
      - the group doesn't have write permissions
      - the group doesn't have execute permissions
      - the world doesn't have read permissions
      - the world doesn't have write permissions
      - the world doesn't have execute permissions
    ```
11. So accordingly I changed the permissions of the flag file for the user to have readd permissions.
    ```
    chmod u+r /flag
    ```
12. Then after that I was able to read the content of the flag file and get the flag.
    ```
    cat /flag
    ```
    Output:
    ```
    pwn.college{EUlWoePVson3oqdKlbN1Xfz5_TB.dBTM2QDLzAjN0czW}
    ```

### Flag
```
pwn.college{EUlWoePVson3oqdKlbN1Xfz5_TB.dBTM2QDLzAjN0czW}
```

##  Challenge 7: Permissions Setting Practice
In this challenge, 


    
   
      



   





   


  


   
   
   
