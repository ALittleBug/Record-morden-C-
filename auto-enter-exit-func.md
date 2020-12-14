* refer [知乎 link](https://www.zhihu.com/question/56132218)
  * gcc with -finstrument-functions [link](http://gcc.gnu.org/onlinedocs/gcc-4.4.4/gcc/Code-Gen-Options.html)
  
  ```
  1. addr2line -f -e $EXE $ADDR
  2. __attribute__((constructor)) 
  ```
