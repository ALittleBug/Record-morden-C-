* new int[0]
  * refer [link](https://stackoverflow.com/questions/1087042/c-new-int0-will-it-allocate-memory)
  
* new int[5]() vs new int[5] and new int vs new int()
  * refer [link](https://stackoverflow.com/questions/7546620/operator-new-initializes-memory-to-zero)
  ```
  There are two versions:

  wsk = new unsigned int;      // default initialized (ie nothing happens)
  wsk = new unsigned int();    // zero    initialized (ie set to 0)
  Also works for arrays:

  wsa = new unsigned int[5];   // default initialized (ie nothing happens)
  wsa = new unsigned int[5](); // zero    initialized (ie all elements set to 0)
  ```
