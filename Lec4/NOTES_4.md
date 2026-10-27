# Debugging and Profiling

## print debugging
crude but effective, need to start from scratch and incrementally narrow down the range.\
### logging
Logging is a more principled print debugging. --> unstructured logging and structured logging. \
Logging level: trace, debug, info, warn, error, critical. Usually a mechanism exists to output log only above certain level.\
Further some frameworks allow the logging level varies between different modules.\
A good practice is: after sticking a bunch of print statements, turn them into log statements. Then don't need to re-compile multiple times\
many app already built-in logging, use flag `-v` or ` --verbose` to track. 

## debugger
printing debugging is limited: may want to real-time check pgm behavior rather than endless recompile, or even don't know what to print.\
GDB or LLDB, that is **attached** to the running process and allow you to control the process execution, like pause pgm, introspect memory, resume pgm \
general purpose debugger v.s. language-specific debugger.

## reverse debug
RR in Linux, short for record replay, very similar to GDB.
