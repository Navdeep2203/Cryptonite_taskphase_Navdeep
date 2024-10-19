# bandit

## Level 0

This level was associated to  logging into Bandit Level 0 using SSH.

### Method
1.  I opened my terminal application.
2. I used the following SSH command to connect to the Bandit server:
   ```
    I used the following SSH command to connect to the Bandit server:
   ```
3. After connecting, I was prompted to confirm the authenticity of the host. I typed yes to proceed.
   ```
   Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
   ```
4. When prompted, I entered the password for `bandit0`, which is `bandit0`.
   After logging in successfully, I saw the welcome message from OverTheWire and completed this level.


## Level 1
The goal of this level is to retrieve the password for the next level, which is stored in a file called `readme` located in the home directory. I will use this password to log into bandit1 using SSH.

### Method
1. I started by logging into Bandit Level 0 using the following command:
   ```
   ssh bandit0@bandit.labs.overthewire.org -p 2220
   ```
2. Once logged in, I checked the contents of the home directory using:
   ```
   ls
   ```
3. I found the `readme` file and used the `cat` command to display its contents:
   ```
   cat readme
   ```
   which displayed:
   ```
   Congratulations on your first steps into the bandit game!!
    Please make sure you have read the rules at https://overthewire.org/rules/
    If you are following a course, workshop, walkthrough or other educational activity,
    please inform the instructor about the rules as well and encourage them to
    contribute to the OverTheWire community so we can keep these games free!
    
    The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
   ```
4. With the retrieved password, I used the following command to log into Bandit Level 1:
   ```
   ssh bandit1@bandit.labs.overthewire.org -p 2220
   ```
   I entered the password obtained from the `readme` file when prompted and completed this level.

## Level 2
The goal of this level is to retrieve the password for the next level, which is stored in a file named - located in the home directory.

###  Method
1. I logged into Bandit Level 1 using the following command:
   ```
   ssh bandit1@bandit.labs.overthewire.org -p 2220
   ```
2.  Once logged in, I checked the contents of the home directory using:
    ```
    ls
    ```
    which showed
    ```
    -
    ```
3. To read the contents of the file, I used the following command, specifying it as a file:
      ```
      cat ./-
      ```
      which displayed the password for the next level
   ```
   263JGJPfgU6LtdEvgfWU1XP5yac29mFx
   ```

## Level 3




   



