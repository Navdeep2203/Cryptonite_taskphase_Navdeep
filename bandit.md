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


## Level 0 ->  Level 1
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

## Level 1 ->  Level 2
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

## Level 2 -> Level 3
The goal of this level is to retrieve the password for the next level, which is stored in a file named `spaces in this filename` located in the home directory.

### Method
1. I logged into Bandit Level 2 using the following command:
   ```
   ssh bandit2@bandit.labs.overthewire.org -p 2220
   ```
   and used the password from the previous level.
2. Once logged in, I listed the files in the home directory to locate the file:
   ```
   ls
   ```
   which showed
   ```
   spaces in the filename
   ```
3. To properly handle spaces in the filename,  I enclosed the filename in double quotes to handle the spaces:
   ```
   cat "spaces in this filename"
   ```
   After running the command, the contents of the file were displayed, revealing the password for the next level.
   ```
   MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
   ```

## Level 3 -> Level 4
The goal of this level is to retrieve the password for the next level, which is stored in a hidden file located in the inhere directory.

### Method
1. I logged into Bandit Level 3 using the following command:
   ```
   ssh bandit3@bandit.labs.overthewire.org -p 2220
   ```
   I used the password retrieved from the previous level.
2. I navigated to the inhere directory where the hidden file is located:
   ```
   cd inhere
   ```
3. To find hidden files in the inhere directory, I used the `ls` command with the `-a` argument, which lists all files including hidden ones:
   ```
   ls -a
   ```
   Output:
   ```
   .  ..  ...Hiding-From-You
   ```
   
I located the hidden file (`...Hiding-From-You`), which had a name starting with a dot (.), indicating that it’s a hidden file.

4.  I then displayed the contents of the hidden file and retrieve the password:
   ```
cat ...Hiding-From-You
```
Password revealed:
```
 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

## Level 4 -> Level 5
The goal of this level is to retrieve the password for the next level, which is stored in the only human-readable file in the inhere directory.

### Method 
1. I logged into Bandit Level 4 using the following command:
   ```
   ssh bandit4@bandit.labs.overthewire.org -p 2220
   ```
   Used the password revealed in the previous level.
2. I navigated to the `inhere` directory where the human-readable file is located:
   ```
   cd inhere
   ```
3.  In the inhere directory, there were multiple files, but only one was human-readable. To identify the human-readable file, I used the `file` command, which determines the type of each file:
   ```
   file ./*
```
Output: 
```
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```
Only `./-file07` was readable.

4.  I used the cat command to display its contents and retrieve the password:
   ```
   cat ./-file07
   ```
   which revealed the password for the next level.
Password:
```
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## Level 5 -> Level 6
The goal of this level is to retrieve the password for the next level, which is stored in a file under the `inhere` directory and meets the following criteria:

* Human-readable
* 1033 bytes in size
* Not executable


### Method
1. I logged into Bandit Level 5 using the following command:
   ```
   ssh bandit5@bandit.labs.overthewire.org -p 2220
   ```
   Used the password revealed in the previous level.

2. I moved into the `inhere` directory where the file is located:
   ```
   cd inhere
   ```
3. To locate the file that meets the specified criteria, I used the find command. This command is highly useful for finding files based on specific properties such as size, permissions, and more. The parameters I used were:
   ```
   find . -type f -size 1033c ! -executable
   ```
   where:
   * `type -f` finds regular files.
   *  `size 1033c` finds the files that are exactly 1033 bytes in size, and
   *  `! -executable`  ensures that the file is not executable.
  
     which gave the filename was
   ```
   ./maybehere07/.file2
   ```
4. I then read the contents of the file and revealed the password for the next level.
   ```
   cat ./maybehere07/.file2
   ```
   Password:
   ```
   HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
   ```

## Level 6 -> Level 7
The goal of this level was to find the password for Bandit Level 7. The password is stored somewhere on the server in a file with the following properties:

* Owned by user: bandit7
* Owned by group: bandit6
* 33 bytes in size

### Method
1. I logged into Bandit Level 6 using the following command:
   ```
   ssh bandit6@bandit.labs.overthewire.org -p 2220
   ```
   used the password revealed in the previous level.
2. Then I executed the find command to search for the file that matched the required properties:
   ```
   find / -type f -user bandit7 -group bandit6 -size 33c
   ```
   where
   `-type f` looks for regular files.
   `-user bandit7` ensures the file is owned by the user bandit7.
   `-group bandit6`ensures the file is owned by the group bandit6.
   `-size 33c` - The file must be exactly 33 bytes.
   which gave many filenames including the ones which were denied permissions.
   From there I figured out one file named as password
   ```
   /var/lib/dpkg/info/bandit7.password
   ```
3. Then I read the contents of the file and revealed the password for the next level.
   ```
   cat /var/lib/dpkg/info/bandit7.password'
   ```
   Password:
   ```
   morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
   ```

## Level 7 -> Level 8
The goal of this level was to find the password for Bandit Level 8. The password is stored in the file `data.txt` next to the word "millionth."

### Method
1. I logged into Bandit Level 7 using the following command:
   ```
   ssh bandit7@bandit.labs.overthewire.org -p 2220
   ```
2. Then I executed the `grep` command to search for the word "millionth":
   ```
    grep "millionth" data.txt
   ```
   which revealed the password for the next level:
   ```
   millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
   ```

## Level 8 -> Level 9
The goal of this level was to find the password for Bandit Level 9. The password is stored in the file `data.txt` and is the only line of text that occurs exactly once.

### Method
1. I logged into Bandit Level 8 using the following command:
   ```
   ssh bandit8@bandit.labs.overthewire.org -p 2220
   ```
2. Then I ,executed the following command to sort the file and find the unique line:
   ```
   sort data.txt | uniq -u
   ```
   where
   * `sort data.txt` sorts the entire file
   * `|` pipes the output of `sort data.txt` as the input of `uniq -u`
   * `uniq -u` filters out any lines that appear more than once.

   which gave the password for the next level,.
   ```
   4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
   ```

## Level 9 -> Level 10
The goal of this level was to find the password for Bandit Level 10, hidden in the file data.txt among non-human-readable characters. The password is preceded by several = characters.

### Method
1.  I logged into Bandit Level 9 using the following command:
   ```
   ssh bandit9@bandit.labs.overthewire.org -p 2220
   ```
2. Then I executed the following command to extract human-readable text and search for lines with = characters:
   ```
   strings data.txt | grep '==='
   ```
   where
   * `strings data.txt` - extracts human readable strings from `data.txt`
   *  `|` pipes the output of 1st command as the input of the 2nd command.
   *  `grep '==='` filters the output to show only the lines that contain multiple = characters.
  
   which showed several lines:
   ```
   }========== the
   3JprD========== passwordi
   ~fDV3========== is
   D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
   ```
   among which the fourth one was the password
   ```
   FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
   ```

##  Level 10 -> Level 11
The goal of this level was to find the password for Bandit Level 11, which was stored in a file named `data.txt` containing base64-encoded data.

### Method
1. I logged into Bandit Level 10 using the following command:
   ```
   ssh bandit10@bandit.labs.overthewire.org -p 2220
   ```
2. Then I, executed the following command to decode the base64-encoded data:
   ```
   base64 -d data.txt
   ```
where
* `base64 -d`: Decodes base64-encoded data and outputs the decoded content

  which showed the password for the next level
  ```
  The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
  ```

## Level 11 -> Level 12
The goal of this level was to find the password for Bandit Level 12, which was stored in a file named `data.txt` where all lowercase and uppercase letters were rotated by 13 positions (ROT13).

### Method
1.  I logged into Bandit Level 11 using the following command:
   ```
   ssh bandit11@bandit.labs.overthewire.org -p 2220
   ```
2. Then,I executed the following command to decode the ROT13-encoded text:
   ```
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
   ```
   This command translated all uppercase and lowercase letters using the ROT13 mapping:
   A-Z was mapped to N-ZA-M
   a-z was mapped to n-za-m

   The decoded result was the required password for the next level.
   ```
   The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
   ```

## Level 12 -> Level 13




   





   








   
   


   





   



