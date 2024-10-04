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

## Challenge 4: 
   
   

