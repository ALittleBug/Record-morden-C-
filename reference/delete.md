* [delete vs delete[] ](https://stackoverflow.com/questions/2347823/how-does-delete-differentiate-between-built-in-data-types-and-user-defined-ones)
* [for using smart pointer](https://stackoverflow.com/questions/2425728/delete-vs-delete-operators-in-c)
 
 ```
    If you're using smart pointers you still need to know the difference in the sense that you still need to know not to write 
    e.g. std::unique_ptr<int>(new int[3]), because it will call regular delete on the array which is undefined behaviour.
    Instead you need to use std::unique_ptr<int[]>
  ```
