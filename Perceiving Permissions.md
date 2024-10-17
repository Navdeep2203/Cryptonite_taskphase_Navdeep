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
In this challenge, 


   


  


   
   
   
