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



