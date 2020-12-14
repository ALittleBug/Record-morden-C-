* refer [知乎 link](https://www.zhihu.com/question/56132218)
  * gcc with -finstrument-functions [link](http://gcc.gnu.org/onlinedocs/gcc-4.4.4/gcc/Code-Gen-Options.html)
  
  ```
  -finstrument-functions
  Generate instrumentation calls for entry and exit to functions. Just after function entry and just before function exit, the following profiling functions will be called with    the address of the current function and its call site. 
  1. addr2line -f -e $EXE $ADDR
  2. __attribute__((constructor)) 
  ```
