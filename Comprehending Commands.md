# Comprehending Commands 

## Challenge 1: cat:not the pet , but the command
In this challenge, the task focused on introducing the `cat` command in linux which is a command used to read, concatenate and dislay the contents of files. The goal was to use `cat` to read a file named flag, which had the flag require for the challenge.

### Method 
1. Firstly, I connected to the pwn.college server via the SSH key.
2. When the connection was established, I navigated to the home directory where the file `flag` was stored. I executed the following command to read the file:
   ```
   cat flag
   ```

   and the command successfully printed the contents of the flag file, which revealed the flag for this challenge.

### Flag
pwn.college{w204auDW1pfAZTDO7nCOfKgIRu2.dFzN1QDLzAjN0czW}

## Challenge 2: catting absolute paths 
In this challenge, the task introduced the conncepts of using absolute paths with the cat command. Instead of reading a file from the home directory, the task was to read the flag file from an absolute path : `/flag`.

### Method 
1. Again, I reconnected to the pwn.college server via the SSH.
2. In this challenge, the flag file was not located in the home directory but was readable through an absolute path: `/flag`.
   ```
   cat /flag
   ```
   The cat command successfully read the file hrough the absolute path and returned the flag.

### Flag
```
pwn.college{kKkDHnVf1hGEgOxYncRIpg0xAv4.dlTM5QDLzAjN0czW}
```

## Challenge 3: more catting practice
In this challenge, I was tasked to get the contents of a file containing a flag without changing the directories using the `cd` command. The file was hidden in a random directory in the file system and I had to access it by specifying its absolute path.

### Method 
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Now as the cd command was restricted to use i.e there was no option to navigate into directories manually to find the flag. So instead of navigating to the directory, I directly accessed the flag by providing its absolute path, using the `cat` command.
   ```
   cat /lib/emacsen-common/packages/flag

   ```
   The command successfully printed the contents of the flag file.

### Flag
```
pwn.college{MvxHK9AUknzLHqMrMY9_NdWZvkI.dBjM5QDLzAjN0czW}
```

## Challenge 4: grepping for a needle in haystack
In this challenge, the task was to search through a large file containing 100000 lines of text to find a hidden flag. 

The hint for this challenge was that every flag starts with `pwn.college`. So the goal was to use the `grep` command to search for this flag without manually going through the file line by line.

### Method
1. Firstly, I reconnected to the pwn. college server via the SSH.
2. To find the flag in  a file `/challenge/data.txt` with a thousand lines of text, I ran the `grep` command to search for the specific string `pwn.college`.
   ```
   grep pwn.college /challenge/data.txt
   ```
3. The command ran successfully and searched through the file and returned the flag starting with pwn.college.
   ```
   pwn.college{E6m9pJ20QDZ2W8Cv3g4pr4W2Lwl.ddTM4QDLzAjN0czW}
   ```
### Flag 
```
pwn.college{E6m9pJ20QDZ2W8Cv3g4pr4W2Lwl.ddTM4QDLzAjN0czW}
```

## Challenge 5: 
In this challenge, the task was to list the files using the `ls` command to locate a renamed file inside the `/challenge` directory. The file was renamed randomly, and I had to find  that, which would reveal the flag when executed.

### Method 
1. Reconnected to the pwn.college server via the SSH.
2. I used the `ls` command to list the contents of the `/challenge` directory to find the randomly named file.
   ```
   ls /challenge
   ```
   which gave me the output
   ```
   812-renamed-run-21877  DESCRIPTION.md
   ```
3. So after finding the renamed file , I ran it to get the flag.
   ```
   /challenge/812-renamed-run-21877
   ```
   which gave me the output
   ```
   Yahaha, you found me! Here is your flag:
   pwn.college{82k7oc2V-kmV4kOvVT3kDnmdpA-.dhjM4QDLzAjN0czW}

   ```
### Flag 
```
pwn.college{82k7oc2V-kmV4kOvVT3kDnmdpA-.dhjM4QDLzAjN0czW}

```

## Challenge 6: touching files
In this challenge, the task was to create two files using the `touch` command(`/tmp/pwn` and `/tmp/college`) and then execute a provided program (`/challenge/run`) to get the flag.

### Method 
1. Again, reconnected to the pwn.college server via the SSH.
2. Then I used `cd` command to navigate to the `/tmp` directory.
   ```
   cd /tmp
   ```
3. Then I created two files named pwn and college in `/tmp` directory using the `touch` command .
   ```
   touch pwn
   touch college
   ```
4. Then I ran the program given in the challenge to get the flag.
   ```
   /challenge/run
   ```
   which gave me the output
   ```
   Success! Here is your flag:
   pwn.college{gfTbfHrsDd3s0SzYbxSo4VH7Tbg.dBzM4QDLzAjN0czW}

   ```
### Flag
```
pwn.college{gfTbfHrsDd3s0SzYbxSo4VH7Tbg.dBzM4QDLzAjN0czW}

```

## Challenge 7: removing files
In this challenge, the task was to practice and learn how to remove files using the `rm `command. A file named `delete_me` was created in the home directory, and it was necessary to delete this file and verify its removal by running the command `/challenge/check`.

### Method 
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then I ran the `rm` command with the argument `delete_me` to remove the file from the home directory.
   ```
   rm delete_me
   ```
3. Then I ran the command given to check if the file was deleted and obtained the flag.
   ```
   challenge/check
   ```
   which gave me the output.
   ```
   Excellent removal. Here is your reward:
   pwn.college{Uxmw8SWigo5RFvPFFy1p1BWaIGD.dZTOwUDLzAjN0czW}
   ```

### Flag 
```
pwn.college{Uxmw8SWigo5RFvPFFy1p1BWaIGD.dZTOwUDLzAjN0czW}
```

## Challenge 8: hidden files

In this challlenge, the task was to find a hidden file in the root directory(`/`) that contains the flag. Hidden files in linux are those that begin with a dot(`.`) and are not displayed when the directory contents are listed. To view hidden files, the `ls` command is used with the `-a` flag.

### Method 
1. Firstly, reestablish a connection with pwn.college server via the SSH.
2. Then I used the `cd` command with the argument `/` which changes the current working directory to the root directory(`/`).

```
/cd
```
3. Then I used the `ls` command with the flag `-a` which lists all the files in the current directory, including hidden files(those starting with a dot).
```
ls -a
```
which gave me the output as
```
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-24303886531269  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
```
where I found the hidden flag file (`.flag-24303886531269`).

4. Then I displayed the contents of the hidden file using the `cat` command which gave me the flag to proceed .
```
cat /.flag-24303886531269
```

### Flag 
```
pwn.college{UoH_SHX_zttxlxAl-X7jsGK5d4r.dBTN4QDLzAjN0czW}
```

## Challenge 9 : An Epic Filesystem Quest
In this challenge, the task was to implement the knowledge of basic Linux commands(`ls`,`cd` and `cat`) to navigate a filesystem and to find a hidden flag.

The clues were provided in many files throughout the entire filesystem, guuiding the user to the next location in each of the clues. Some clues were hidden in files that required special handling, such as reading hidden files or entering directories to unlock further clues.

### Method
1. Firstly, I reestablished a connection to the pwn.college server via the SSH.
```
ssh -i /home/navdee2203/key hacker@dojo.pwn.college
```
2. Then I navigated to the root directory.
   ```
   cd /
   ```
3. Then I listed all the files in the root directory using the `ls` command.
   ```
   ls
   ```
   which gave me the output as
   ```
   NOTE  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  
   tmp  var
   bin   challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
   ```
   which had the file named `NOTE`.

4. Then I displayed the contents of the `NOTE` file, which provided the next clue.
   ```
   cat /NOTE
   ```


   
   

   


   

