# File Globbing

## Challenge 1: Matching with *
This challenge focused on using globbing to navigate to the /challenge directory while adhering to a character limit. The goal was to successfully change the directory and run a command to obtain a flag.

### Method
1. Firstly, I connected to the pwn.college server via the SSH.
2. First I attempted to change to the /challenge directory using a glob pattern:
   ```
   cd /cha*
   ```
   but I received an error :
   ```
   You specified the path to 'cd' to in more than 4 characters. Disallowed!
   This challenge resets your working directory to /home/hacker unless you change
   directory properly...
   ```
3. Then I adjusted the command to use a 4-character glob pattern:
   ```
   cd /c*e
   ```
   which successfully changed the directory to `/challenge`.
4. Then I ran the challenge command
   ```
   /challenge/run
   ```
   which gave the following output.
   ```
   You ran me with the working directory of /challenge! Here is your flag:
   pwn.college{Y__FN7HDXZKb7u6GvGRDBN3rsEL.dFjM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{Y__FN7HDXZKb7u6GvGRDBN3rsEL.dFjM4QDLzAjN0czW}
```

## Challenge 2: Matching with ?
In this challenge it was required to use the `?`wildcard to change the directory to `/challenge`. The task was to navigate using single-character wildcards and subsequently execute a command to obtain a flag.


### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then, I attempted to change to the `/challenge` directory using the `?` wildcard.
   ```
   cd /?ha??enge
   ```
   which successfully changed the directory to `/challenge`.

3. After confirming the current working directory, I ran the challenge command:
   ```
   ./run
   ```
   which gave me the following output and the flag to proceed.
   ```
   You ran me with the working directory of /challenge! Here is your flag:
   pwn.college{8hrOgvjOGAxt0HN1kGba-7WJdy5.dJjM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{8hrOgvjOGAxt0HN1kGba-7WJdy5.dJjM4QDLzAjN0czW}
```

## Challenge 3 : Matching with []
In this challenge, the task was change the working directory to /challenge/files and run a command using bracket-globbing to match specific files.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Next, I changed the current working directory to `/challenge/files`.
   ```
   cd /challenge/files
   ```
3. Then I executed the command `/challenge/run` with the required bracket globbing.
   ```
   /challenge/run file_[absh]
   ```
   which gave me the following output and the flag to proceed.
   ```
   You got it! Here is your flag!
   pwn.college{YGHWI2Wx5gKgXiv0UA7akY_T5En.dNjM4QDLzAjN0czW}
   ```
### Flag
```
pwn.college{YGHWI2Wx5gKgXiv0UA7akY_T5En.dNjM4QDLzAjN0czW}
```

## Challenge 4: Matching paths with []
In this challenge, the task focused on using globbing patterns to construct absolute paths for files located in `/challenge/files`. The task was to expand the path to include specific files using the bracket-globbing technique.


### Method 
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then I used the following command to access the required files and run the `challenge ` command.
   ```
   /challenge/run /challenge/files/file_[absh]

   ```
   which gave the following output and the flag to proceed.
   ```
   You got it! Here is your flag!
   pwn.college{4PtTqo_tcrMjyXzMMSnEybpBTYZ.dRjM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{4PtTqo_tcrMjyXzMMSnEybpBTYZ.dRjM4QDLzAjN0czW}
```

## Challenge 5: Mixing globs
In this challenge , the task was to use glob patterns to match the files "`challenging`," "`educational`," and "`pwning`" located in the `/challenge/files` directory. The challenge required a single globbing pattern that was no more than six characters long.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. The files to match were
   * challenging
   * educational
   * pwning
  I recognized that I could use a square bracket glob to match the first character of each file name.
  I experimented with several patterns to find one that satisfied the challenge requirements such as
```
* /challenge/run [cep]
* /challenge/run [cep]*g
```
3. After several attempts, I successfully executed the command.
   ```
   /challenge/run [cep]*
   ```
   which matched all the required files and finally gave me the following output and the flag to proceed.
   ```
   You got it! Here is your flag!
   pwn.college{I97CnYKbZleeYxxAM4_Lyn6m18f.dVjM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{I97CnYKbZleeYxxAM4_Lyn6m18f.dVjM4QDLzAjN0czW}
```

## Challenge 6: Exclusionary Globbing
In this challenge, the task was to filter out files in the /challenge/files directory using exclusionary globbing. Specifically, we needed to exclude files that start with the letters "p," "w," or "n."

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then, I navigated to the `/challenge/files` directory using the `cd` command.
  ```
  cd /challenge/files
  ```
3.  Then, I executed the `/challenge/run` command with the appropriate glob pattern to exclude files that start with "p," "w," or "n."
   ```
   /challenge/run [!pwn]*
   ```
which gave me the following output and the flag to proceed.
```
You got it! Here is your flag!
pwn.college{8F4tOgXAlAjmAngubA-JJ8LwczH.dZjM4QDLzAjN0czW}
```
### Flag
```
pwn.college{8F4tOgXAlAjmAngubA-JJ8LwczH.dZjM4QDLzAjN0czW}
```

   





   
   
