# command line environment and remote control

## Shell script:

0. string argument: `ls -l project1` \

1. flags: argument with single or double dash, as options to the program to change its default behavior. \
`ls -a` is equivalent to `ls --all` \
(the parsing of flags are done by programs, not the shell) 

2. arbitrary of arguments: Programs capable to accept the same type of argument an arbitrary amount of times, like create multiple folders： \
`mkdir proj3 proj4` 

3. globing and pattern: \
`touch proj1/{a,b,c}.py` is equivalent to `touch proj1/a.py proj1/b.py proj1/c.py` \
`touch *.{py, sh}` will expand to all possible single file 

4. streams: when execute pipeline in shell, all these programs are run in parallel. \
`cat numbers.txt | grep -P '^\d$' | sort | uniq` \
Most PGMs expects **standard input**. And PGMs produce either **standard output stream** or **standard error stream**. \
So to capture error we need different syntax.  `ls nonexistence 2> err.txt` will acquire the error MSG while `ls nonexistence > err.txt` can not \
`ls nonexistence 2> /dev/null` will ignore the error MSG 

5. environmental variables: Use syntax like `foo=bar` to define and use syntax like `echo $foo` to access. (`foo = bar ` with spaces is invalid.) \
could store the environment variables like `files=${ls}` then `echo $files` \
**Locality**: whenever create a variable, it only goes into current local session. If want to pass it to other PGM, need to pretend the cmd before passing it like: \
`DEBUG=1 bash -c 'echo $DEBUG` ( note that `DEBUG=1` then `bash -c 'echo $DEBUG'` will print nothing) \
Or use export cmd let the child process inherit the environment variable: \
`export DEBUG=1` then `bash -c 'echo $DEBUG'` \
to undo the environment variables: `unset DEBUG`

6. return code: almost all control flow is based on return code. \
`echo $?` to reveal the return code, 0 indicating a success. non 0 is a fail. 

7. signals: pressing ctrl+c will stop the PGM, this is signaling, a type of software interrupt. \
ctrl+c -> SIGINT, SIGQUIT is more aggressive to force exit PGM. Further there is SIGKILL. \
ctrl+z -> SIGTSTP, suspend the PGM. could recover the PGM by `fg` \
kill command to direct send signal: `kill -SIGNCONT` or `kill -SIGINT` with process number.

## On remote server: secure shell(SSH):

1. call ssh and authentication: \
`ssh user@110.100.100.111` and a prompt for password

2. Free from re-authentication -- SSH keys: \
a public key and a private key. Put the public key on remote server to verify if we have related private key. Keep private key always hidden. \

3. ssh capable of interactive sessions as well as execute commands\
`ssh jjgo@192.168.65.4 ls | wc -l` will execute "ls" on the server, then execute line count locally and print the output on our terminal.\
if want to do this on both sides: `ssh jjgo@192.168.65.4 'ls | wc -l'`

4. files copying: syntax like `scp` to transfer files to the server: `scp jjgo@192.168.65.4:home/jjgo`

5. terminal multiplexers: `tmux` is a PGM enable user to run many other pgms within the same environment. \
It will generate 'windows' like browser tabs to visualize different pgms. \
once we disconnected, the pgm on remote server will be lost by shell hangup signal SIGHUP.\
if reconnect by `tmux attach`. the pgm continues.

## Customizing shell:
