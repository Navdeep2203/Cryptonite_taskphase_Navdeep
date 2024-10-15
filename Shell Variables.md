# Shell Variables 

## Challlenge 1: Printing Variables
In this challenge the goal was to print the value stored in a shell variable named `FLAG`. To solve this, we were required to use basic shell commands, specifically echo, which prints out text or variable values.

### Method 
1. Firstly, I connected to the pwn.college server via the SSH using the following command:
   ```
   ssh -i /home/navdee2203/key hacker@dojo.pwn.college
   ```
2. To print the value of the `FLAG` variable, I used the following command:
   ```
   echo $FLAG
   ```
   where 
   * The `FLAG` variable contains the flag, and we need to print it out using a shell command and
   * The `echo` command is used because it can output both plain text and variable values by using the `$` symbol before the variable name.
  
     which gave the flag to proceed.
   ```
   pwn.college{4tei_YISQk9maSfwUua1RssDv2H.ddTN1QDLzAjN0czW}
   ```

   ### Flag
   ```
   pwn.college{4tei_YISQk9maSfwUua1RssDv2H.ddTN1QDLzAjN0czW}
   ```

## Challenge 2: Setting Variables
In this challenge the goal was to set a shell variable named `PWN` to the value `COLLEGE` and then retrieve the flag which required clear understanding of correct syntax for variable assignment in the shell.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then, to proceed with this challenge, I assigned the value COLLEGE to the PWN variable using the following command:
   ```
   PWN=COLLEGE
   ```
   After setting the variable correctly, the following output was displayed and the flag was given to proceed.
   ```
   You've set the PWN variable properly! As promised, here is the flag:
   pwn.college{sZdlhtrWRwia638fK1p6uSd05kh.dlTN1QDLzAjN0czW}
   ```
### Flag
```
pwn.college{sZdlhtrWRwia638fK1p6uSd05kh.dlTN1QDLzAjN0czW}
```

## Challenge 3: Multi Word Variables
In this challenge ,the goal  was to correctly set the `PWN` variable to the multi-word string `COLLEGE YEAH`. This required an understanding of how to handle spaces within variable values using quoting in the shell.

### Method
1.  Firstly, reconnected to the pwn.college server via the SSH.
2.  Then, to set the `PWN` variable to `COLLEGE YEAH`, the following command was used:
  ```
   PWN="COLLEGE YEAH"
```
because to set a variable to a value containing spaces, the entire value needs to be enclosed in quotes (either single or double quotes)which allows the shell to treat the value as a single entity.

Output:
```
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UrRj8yTMTc4DHz4isvFVs0jbheT.dBjN1QDLzAjN0czW}
```

### Flag
```
pwn.college{UrRj8yTMTc4DHz4isvFVs0jbheT.dBjN1QDLzAjN0czW}
```

## Challenge 4: Exporting Variables
In this challenge, the task was to set two variables,`PWN` and `COLLEGE`, with specific instructions regarding export behavior:

The `PWN` variable must be exported and set to the value `COLLEGE`.
The `COLLEGE` variable must be set to the value PWN but not exported.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then ,the first step was to set the `COLLEGE` variable to the value `PWN` without exporting it which ensures that it remains local to the current shell. So I ran the following command:
 ```
COLLEGE=PWN
```
which displayed the following message 
```
You've set the COLLEGE variable to the proper value!
```

3. Then ,the next step was to set and export the `PWN` variable with the value `COLLEGE` which allows the child process /challenge/run to inherit the PWN variable:
   ```
   export PWN=COLLEGE
   ```
   which displayed the following message
   ```
   You've set the PWN variable to the proper value!
   You've set the COLLEGE variable to the proper value!
   ```
5. After setting the variables correctly, I invoked the challenge command to complete the task:
   ```
   /challenge/run
   ```
   which gave the following output and the flag to proceed.
   ```
   CORRECT!
   You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
   job! Here is your flag:
   pwn.college{Uu90d5Klt_fpj5KMM0_ybYXXOO0.dJjN1QDLzAjN0czW}
   You've set the PWN variable to the proper value!
   You've set the COLLEGE variable to the proper value!
   ```

### Flag
```
   pwn.college{Uu90d5Klt_fpj5KMM0_ybYXXOO0.dJjN1QDLzAjN0czW}
```

## Challenge 5: Printing Exported Variables
In this challenge, the goal was to retrieve a flag from an environment variable using the `env` command, which lists all exported environment variables in the current shell session. After running the command, I was able to identify the FLAG variable, which contained the flag for this level.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then, I executed the command `env` in the shell.
   ```
   env
   ```
   which displayed the following output:
```
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=2a6b8ff75443534cfe0306a816e1527a76d4dda7840709b7747c8e141dd215a2
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
FLAG=pwn.college{USXdIwD3y9aA10tNufrJSMJw4w2.dhTN1QDLzAjN0czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
```
3. Then I scanned through the output to find the `FLAG` variable in which the flag for this level was there.

### Flag
```
pwn.college{USXdIwD3y9aA10tNufrJSMJw4w2.dhTN1QDLzAjN0czW}
```

## Challlenge 6: 
In this challenge, I learned about command substitution in the shell. The task was to read the output of the `/challenge/run` command directly into a variable called `PWN`, which would contain the flag.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then,  I used the command substitution feature of the shell to store the output of the `/challenge/run` command in the variable `PWN`:
   ```
   PWN=$(/challenge/run)
   ```
   which gave the following message
   ```
   Congratulations! You have read the flag into the PWN variable. Now print it out
   and submit it!
   ```
3. Then, I printed the value of the PWN variable to retrieve the flag:
   ```
   echo $PWN
   ```
   which printed the flag.

### Flag
```
pwn.college{IFqjEmqHU0bgriAsZ5-Y2CIzaTn.dVzN0UDLzAjN0czW}
```

## Challenge 7: Reading Input
In this challenge, I learned how to read user input using the `read` builtin command in the shell. The objective was to set the variable `PWN` to the value `COLLEGE`.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. Then, I executed the following command to read input and assign it to the variable `PWN`:
   ```
   read PWN
   ```
   which prompted me to input the value to the variable which I entered as `COLLEGE`.
   ```
   COLLEGE
   ```
   Upon successful execution, the system confirmed that the `PWN` variable was set properly and provided the flag:
   ```
   You've set the PWN variable properly! As promised, here is the flag:
   pwn.college{UtpS_KgpDP8UqcIY6PEcLoEGq7n.dhzN1QDLzAjN0czW}
   ```
### Flag
```
pwn.college{UtpS_KgpDP8UqcIY6PEcLoEGq7n.dhzN1QDLzAjN0czW}
```


## Challenge 8: Reading Files
In this challenge, the objective was to read the contents of a file directly into an environment variable using the read command with input redirection, instead of using a subshell with cat.

### Method
1. Firstly, reconnected to the pwn.college server via the SSH.
2. To read the contents of the `/challenge/read_me` file directly into the` PWN `environment variable, I utilized the read command along with input redirection.
   ```
   read PWN < /challenge/read_me
   ```
   which gave the following output the flag to proceed.
   ```
   You've set the PWN variable properly! As promised, here is the flag:
   pwn.college{EMiJVDen2SmQvFFh5paEuL4O7Dx.dBjM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{EMiJVDen2SmQvFFh5paEuL4O7Dx.dBjM4QDLzAjN0czW}
```

   

 

   








   
   

   


   
   
