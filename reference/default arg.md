* default args 
  * refer [link](https://stackoverflow.com/questions/5740296/missing-default-argument-compiler-error)
  
  ```cpp
  void func ( string word = "hello", int b ) {

    // some jobs

  }

  in another function

  //calling 
  func ( "", 10 ) ;
  You can't have non-default parameters after your default parameters begin. Put another way, how would you 
  specify a value for b leaving word to the default of "hello" ?
  ```
