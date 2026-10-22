*INSPIRATION of this lecture (by Jose): "unknown unknowns -- might just not know many smart programmers before you have already faced the frustrations you've met
and already solved these problems."*

**1. BASH (Bourne-Again Shell) in Linux -- Shell: command line interface** \
   `date` returns world-time viewing\
   `echo` returns printing string with space-separated arguments\
   `man` returns manual of argument, on wanted instruction like `man date` (`man bash` included more specifics)
   
**2. directory manipulate:** \
   `cd` for change directory. Use slash indicating the directory to jump to, like: `cd /bin`, followed by a change of prompt showing success or not\
   `cd /` jumps to the root
   
   relative paths: not start with slash as resolution in current directory, not from root. So a `cd bin` will search, just from current position, not root.
   
   `cd .` and `cd ..`: for current directory and parent directory wherever we are.\
   `cd ~` back to home directory. Thus we know `cd ~/..` will go to parent directory of home
   
**3. `$PATH` and `which`:** \
   `which` returns the directory of program as its argument. \
   `echo $PATH` returns an 'environmental-variable-like' list that may include the wanted program. System will walk through to perform the program when first match \
   `which -a` returns all possible director of wanted program (same name)

**4. files:** \
   `ls \bin` returns the list of contents in the directory as argument. Absenct argument `ls` will return a list of content of current dir.\
   `cat` returns the content of a file as argument, like: `cat README.md`\
   `sort` returns a sorted version of the file as argument. \
   `uniq` returns a drop-duplicated version of the file as argument. \
   `head` and `tail` viewing the first/last several lines within the file, could adjust line counts as: `head -n5 datafile` \
   `grep` is **files searcher** returns dir. supported by regex. `-r` for recursively search in the nested folders \
   `sed` is **line editor** with built-in language, basically for replace/search \
   `sed -i '/s/target/replaced/g' */*.md`, `-i` for inplace modify, `/g` for global, `*/*` means any dir., `.md` is glob. \
   `sed -i '/s/[^a].*-\d/replaced/g' */*.md` is a regex example. \
   `find` used for specific type search of files, like `find ~/downloads -type f -name "*.zip" -mtime +30`, returns the dir. \
   `rm` remove the file.
   
   Combine above instructions like this: `find ~/downloads -type f -size +100M -mtime +30 -exec rm{} \;` or `find . -name "*.md" -exec grep -l "TODO" {} \;`
   
   `awk` is **parser** also with built-in language. Will split the file by white-space and lines by default. \
   `awk '{print $2}' datafile` what in-between the quotation is AWK language. \
   `>` and `<` for write file and read file. writing: `date >thedate.txt` reading: `cat thedate.txt` or `cat <thedate.txt` \
   `date >>thedate.txt` will append content in file, by default it is override. 
   
**5. pipeline and pipe character** \
	`|` run the left PGM and take its output as input of right PGM. 

**6. simple conditions in BASH** \
	`if grep 2026 thedate.txt; then echo "it's 2026"; fi` branch PGM will executed only when the 'if' branches successfully exit. \
	`while` + `do` + `done`, sep. by semicolon \
	`for` + `in` + `do` + `done`, sep. by semicolon	\
	`test` or `[` for non command line conditions

**7. BASH lines and .sh executable**\
	runs from top to bottom, line by line like bash input sequentially. \
	**shebang** is hash bang that started at executable files: `#!/bin/sh`. This line tells shell to use this executable file as input and give it to the program under specific dir. [Shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) \
	This means `./mypgm.sh` as the same as `/bin/sh <mypgm.sh`. **shebang** makes this equivalence. \
	**shebang** can be extended to like: `#!/usr/bin/python`. Thus the lines in executable will be passed as input of python. **(NOT AVAILABLE FOR LANGUAGE NEEDS SEPARATE COMPILING)** \
	`chmod +x` to modify permission/accessibility

 *QUICKTRICK:* use ctrl+c to skip command or terminate the command \  
 *QUICKTRICK:* use TAB or double TAB for autocomplete\	
