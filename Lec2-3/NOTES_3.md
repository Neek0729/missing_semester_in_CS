# Development environment

## VIM
1. terminal-based development environment V.S. IDE(graphical) \
can turn some text editor like VIM or Emacs into IDEs. VIM coding useful when IDE not available (on remote server such as)
key bindings of VIM is available on many other IDE as well as bash/zsh. \

2. text-editing \
coding really not sequentially editing/modifying a stream of text. Need jumps between snippets of text. \
VIM buffers the text and offers a way to code basically only rely on keyboard. \
cool idea: *interface(VIM) itself is viewed as a programing language*. --> Primitives to operate text-editing \
J --> cursor down;  10J --> jump down by 10 lines \
K --> cursor up \
F --> find;  F% --> find next ( \
... 

3. Modal editor \
In Vim, 4 modes to switch. Default is NORMAL mode(NORMAL mode cannot modify buffer of text). \
i. pressing "i" switch to INSERT mode. Add text to the buffer of text. return to NORMAL by "esc". \
ii. pressing "r" switch to REPLACE mode. overwrite the text. \
iii. 3 visual modes: plain visual mode(chunks of text), visual line mode and visual block mode, by "v", "shift+v" and "ctrl+v" 

4. NORMAL mode - movement \
by arrow or by JIKL key bindings.
W --> cursor moves forward word by word. \
B --> back to the beginning of a word. \
0 --> back to the beginning of a line. \
e --> to the end of a word.\
$ --> jumps to the end of a line. \
H --> head of the screen; M --> middle of the screen; L --> bottom of the screen. \
ctrl+D --> scroll up;  ctrl+U --> scroll down \
gg -> jumps to the top of the line\
G --> jumps to the bottom of the file \
: 123 --> jumps to line 123 (: switch to COMMAND mode) \
% --> find matching character \
F(on one char) --> finds next same char; T(on one char) --> return to prev. \
/ --> search matching string.

5. NORMAL mode - selection\
In VISUAL mode, use movement cmd to slide cursor around and select \
V --> select the whole line, so if continue press J or ↓, will select the next line \
ctrl+V --> select the whole block

6. NORMAL mode - edition\
c --> change, force switch to INSERT mode. \
d --> delete; combine use: 'd' + 'w' --> delete current word. 'd' + 'j' --> delete next line.\
o --> create new line below(force into INSERT mode); O --> create new line above\
a --> append text. \
u --> undo; 5u --> undo five times. 

7. NORMAL mode - counts and modifier\
5W --> move 5 words forward. \
i --> inside; a --> around. \
so 'ci' can enable change within some range, like within parentheses, press 'ci('. A quick way to modify arguments of funct. \

8. COMMAND mode, ":" to run commands\
q! --> force quit. \
w --> to write file\
...

##  IDE semantic understanding based on language server
Support for language automatic formatting, code completion, error checking, jump to definition, etc.\
Not IDE built-in, but a protocol(LangauageServerProtocol) enable IDE interop. w/ language server. 

## AI powered dev.
1. copilot of github. **AI-autocompletion** for functions definition, docstring generate, etc.\
Need to review the code though. \
One good practice is to steer AI by writing comments to guide the implementation. \
But this autocompletion only based on wherever cursor is and applies narrowly on small range. \
In python, a more advanced way is to steer AI by docstring. Thus an entire code block may be generated.

2. inline chat: select by cursor on specific line or block text and give direct command to AI to guide it.\
After selection, call copilot by ctrl+i to prompt a chatbox to give command.\
Then AI will propose modification in a display mode like git diff.\
Can keep the changes after review.


