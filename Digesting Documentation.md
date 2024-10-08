# Digesting Documentation

## Challenge 1: Learning from Documentation
 In this challenge, the task was to learn how to correctly pass arguments to a program by understanding its documentation. The program `/challenge/challenge` was to be run with the correct argument  in order to retrieve the flag. The challenge involved figuring out the correct argument based on provided documentation.

### Method
1. Firstly, I connected to the pwn.college server via the SSH.
   ```
   ssh -i /home/navdee2203/key hacker@dojo.pwn.college

   ```
2. The challenge provided documentation for the program `/challenge/challenge`, which indicated that the correct argument to use was `--giveflag`.
   So I ran the program using the following command with the specified argument.
   ```
   /challenge/challenge --giveflag
   ```
   which gave me the following output.
   ```
   Correct argument! Here is your flag:
   pwn.college{kzPUybdZGj2ZIvK1x5dCqhkM2r6.dRjM5QDLzAjN0czW}
   ```

### Flag
```
pwn.college{kzPUybdZGj2ZIvK1x5dCqhkM2r6.dRjM5QDLzAjN0czW}
```

## Challenge 2: Learning Complex Usage
In this challenge, the task was to learn about commands that accept arguments for their arguments, as demonstrated by the `--printfile` argument in the `/challenge/challenge` program.

### Method 
1. Reconnected to the pwn.college server via the SSH.
2. The documentation for the `/challenge/challenge` program explained that the command takes the `--printfile` argument, which itself requires an additional argument specifying the path of the file to print.
   So I  invoked the `/challenge/challenge` command with the appropriate argument pointing to the flag file.
   ```
   /challenge/challenge --printfile /flag
   ```
   which gave me the following output and the flag to proceed.
   ```
   Correct argument! Here is the /flag file:
   pwn.college{UX5t-3qMPVX5zZf7AVMZNBTfpk1.dVjM5QDLzAjN0czW}
   ```
### Flag
```
pwn.college{UX5t-3qMPVX5zZf7AVMZNBTfpk1.dVjM5QDLzAjN0czW}
```

## Challenge 3: Reading Manuals
In this challenge, the task was to explore the use of the man command to read documentation for various Linux commands. The goal was to retrieve the flag from the /challenge/challenge program by first consulting its manual page and discovering the correct argument to pass.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. Then I ran the `man` command which displays the manual page for a given command.
   ```
   man challenge
   ```
   which displayed the manual page for the command `/challenge/challenge/`.
   ```
   CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)

   NAME
       /challenge/challenge - print the flag!

   SYNOPSIS
       challenge OPTION

   DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --gycehw NUM
              print the flag if NUM is 031

   AUTHOR
       Written by Zardus.

   REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

   SEE ALSO
       man(1) bash-builtins(7)

   ```
3. The manual provided several options, including:

   `--fortune`: Read a fortune.
   `--version`: Output version information.
   `--gycehw NUM`: Print the flag if NUM is 031.
4. According to the manual, the `--gycehw` option required a numeric argument, specifically 031, to reveal the flag. So I ran the command:
   ```
   /challenge/challenge --gycehw 031

   ```
   which returned the flag.
   ```
   Correct usage! Your flag: pwn.college{0Qg3ZycU1KLeEhGwvIoqEAl5c7G.dRTM4QDLzAjN0czW}
   ```

### Flag 
```
pwn.college{0Qg3ZycU1KLeEhGwvIoqEAl5c7G.dRTM4QDLzAjN0czW}
```

## Challenge 4: Searching Manuals
In this challenge, I learned how to navigate man pages efficiently by scrolling, searching, and using specific key commands. The task was to use these techniques to find the option in the /challenge/challenge man page that would print the flag.

### Method
1.  Firstly, I reconnected to the pwn.college server via the SSH.
2.  Firstly I opened the manual page for the command `challenge`.
   ```
   man challenge
   ```
3.   The challenge introduced key commands for scrolling (`arrow keys`,` PgUp`,` PgDn`) and searching (`/` for forward searches,` ?` for backward searches).
   After opening the man page for the /challenge/challenge program , I  used the search functionality (`/`) to look for keywords like "flag" or "option" in the documentation.
4. After searching, I discovered the correct argument, ``--wxvp``, to pass to the program for retrieving the flag.
5. Then, I ran the `challenge` command with the argument `--wxvp`.
   ```
   /challenge/challenge --wxvp

   ```
   which gave me the following the flag.

### Flag
```
pwn.college{4O5wqblNgiXFiLQ2c08oPAv0BNB.dVTM4QDLzAjN0czW}
```

## Challenge 5: Searching For Manuals
In this challenge there was a hidden challenge where the man page for the command was randomized, making it tricky to discover the correct usage. The objective is to find the hidden man page that describes how to use the /challenge/challenge command to obtain the flag.

### Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. I started by reading the man page for `man` to understand how to search through man pages effectively.
   ```
   man man
   ```
3.  Then I used  the `man -k` command to search for keywords related to the challenge. The following command shows how to search for anything related to "challenge which I got to know by reading the man page for `man`.
   ```
   man -k challenge
   ```
4. After identifying the randomized name of the challenge's man page, I used the `man` command to view its contents.
   ```
   man zrqgfvwald
   ```
   which gave the following details.
   ```
   CHALLENGE(1)                                            Challenge Commands                                           CHALLENGE(1)

   NAME
       /challenge/challenge - print the flag!

   SYNOPSIS
       challenge OPTION

   DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit
   ```
5. With the knowledge obtained from the man page, I executed the `challenge` command using the correct argument to retrieve the flag:
   ```
   /challenge/challenge --zrqgfv 187
   ```
which gave me the flag to proceed. 
```
Correct usage! Your flag: pwn.college{AzrAE1q8KNgRTfO7KLvwN9aVOl4.dZTM4QDLzAjN0czW}
```

### Flag
```
pwn.college{AzrAE1q8KNgRTfO7KLvwN9aVOl4.dZTM4QDLzAjN0czW}
```

## Challenge 6: Helpful Programs
In this challenge, the goal was to explore a program’s documentation using the --help option and utilize the printed information to retrieve a flag.

## Method
1. Firstly, I reconnected to the pwn.college server via the SSH.
2.  I began by executing the `help` command to understand the available options for the program:
   ```
   /challenge/challenge --help
   ```
  which gave the following output:
  ```
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
```
3. Next, I used the `--print-value` option to obtain the specific value needed to retrieve the flag:
   ```
   /challenge/challenge --print-value
   ```
   which gave the secret value
   ```
   The secret value is: 401
   ```
4. Finally, I utilized the `--give-the-flag` option with the value retrieved:
   ```
   /challenge/challenge --give-the-flag 401
   ```
   which gave me the following output and the flag to proceed.
   ```
   Correct usage! Your flag: pwn.college{AxAPTjEulMC-ImNyyMs_VMFJiSq.ddjM4QDLzAjN0czW}
   ```

### Flag
```
pwn.college{AxAPTjEulMC-ImNyyMs_VMFJiSq.ddjM4QDLzAjN0czW}
```

## Challenge 7: Help for Builtins

In this challenge, the task was to explore built-in commands in the shell and specifically to retrieve a flag using the help command for the built-in `challenge`.

### Method 
1. Firstly, I reconnected to the pwn.college server via the SSH.
2. I began by using the help command to access the built-in commands available in the shell:
   ```
   help
   ```
   which gave the following output
   ```
   GNU bash, version 5.2.32(1)-release (x86_64-pc-linux-gnu)
   These shell commands are defined internally.  Type `help' to see this list.
   Type `help name' to find out more about the function `name'.
   Use `info bash' to find out more about the shell in general.
   Use `man -k' or `info' to find out more about commands not in this list.

   A star (*) next to a name means that the command is disabled.

   job_spec [&]                                                      history [-c] [-d offset] [n] or history -anrw [filename] or hi>
   (( expression ))                                                  if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ].>
   . filename [arguments]                                            jobs [-lnprs] [jobspec ...] or jobs -x command [args]
   :                                                                 kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or >
   [ arg... ]                                                        let arg [arg ...]
   [[ expression ]]                                                  local [option] name[=value] ...
   alias [-p] [name[=value] ... ]                                    logout [n]
   bg [job_spec ...]                                                 mapfile [-d delim] [-n count] [-O origin] [-s count] [-t] [-u >
   bind [-lpsvPSVX] [-m keymap] [-f filename] [-q name] [-u name] >  popd [-n] [+N | -N]
   break [n]                                                         printf [-v var] format [arguments]
   builtin [shell-builtin [arg ...]]                                 pushd [-n] [+N | -N | dir]
   caller [expr]                                                     pwd [-LP]
   case WORD in [PATTERN [| PATTERN]...) COMMANDS ;;]... esac        read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-N nc>
   cd [-L|[-P [-e]] [-@]] [dir]                                      readarray [-d delim] [-n count] [-O origin] [-s count] [-t] [->
   challenge [--fortune] [--version] [--secret SECRET]               readonly [-aAf] [name[=value] ...] or readonly -p
   command [-pVv] command [arg ...]                                  return [n]
   compgen [-abcdefgjksuv] [-o option] [-A action] [-G globpat] [->  select NAME [in WORDS ... ;] do COMMANDS; done
   complete [-abcdefgjksuv] [-pr] [-DEI] [-o option] [-A action] [>  set [-abefhkmnptuvxBCEHPT] [-o option-name] [--] [-] [arg ...]
   compopt [-o|+o option] [-DEI] [name ...]                          shift [n]
   continue [n]                                                      shopt [-pqsu] [-o] [optname ...]
   coproc [NAME] command [redirections]                              source filename [arguments]
   declare [-aAfFgiIlnrtux] [name[=value] ...] or declare -p [-aAf>  suspend [-f]
   dirs [-clpv] [+N] [-N]                                            test [expr]
   disown [-h] [-ar] [jobspec ... | pid ...]                         time [-p] pipeline
   echo [-neE] [arg ...]                                             times
   enable [-a] [-dnps] [-f filename] [name ...]                      trap [-lp] [[arg] signal_spec ...]
   eval [arg ...]                                                    true
   exec [-cl] [-a name] [command [argument ...]] [redirection ...>   type [-afptP] name [name ...]
   exit [n]                                                          typeset [-aAfFgiIlnrtux] name[=value] ... or typeset -p [-aAfF>
   export [-fn] [name[=value] ...] or export -p                      ulimit [-SHabcdefiklmnpqrstuvxPRT] [limit]
   false                                                             umask [-p] [-S] [mode]
   fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command>  unalias [-a] name [name ...]
   fg [job_spec]                                                     unset [-f] [-v] [-n] [name ...]
   for NAME [in WORDS ... ] ; do COMMANDS; done                      until COMMANDS; do COMMANDS-2; done
   for (( exp1; exp2; exp3 )); do COMMANDS; done                     variables - Names and meanings of some shell variables
   function name { COMMANDS ; } or name () { COMMANDS ; }            wait [-fn] [-p var] [id ...]
   getopts optstring name [arg ...]                                  while COMMANDS; do COMMANDS-2; done
   hash [-lr] [-p pathname] [-dt] [name ...]                         { COMMANDS ; }
   help [-dms] [pattern ...]
   ```
3.  Next, I specifically looked for help on the challenge built-in command:
   ```
   help challenge
   ```
which gave the following output
```
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value is "Qd7NyRop".
```
4. After getting the knowledge of the correct secret value, I executed the command to retrieve the flag:
   ```
   challenge --secret Qd7NyRop
   ```
   which gave the following output the flag to proceed.
   ```
   Correct! Here is your flag!
   pwn.college{Qd7NyRophnBDWBUZ4xuw6cd9PzJ.dRTM5QDLzAjN0czW}

   ```
### Flag
```
pwn.college{Qd7NyRophnBDWBUZ4xuw6cd9PzJ.dRTM5QDLzAjN0czW}
```


   
   






   






   
   
