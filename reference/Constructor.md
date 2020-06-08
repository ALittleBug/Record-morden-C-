* Find default copy constructor(shallow copy) [Useful basic C++ blog for some tips](http://www.fredosaurus.com/notes-cpp/index.html)
  * Whether the constructor can be called depends on whether a new object is generated
  * foo(MyClass &rM) foo (MyClass &&rM) foo(MyClass vM) 
  * [Bo Qin vedio about move semantic](https://www.youtube.com/watch?v=IOkgBrXCtfo)
* Default move constuctor
  * refer [link](https://stackoverflow.com/questions/11572669/move-with-vectorpush-back) [sample for vector using move/copy](https://www.educative.io/edpresso/what-is-a-move-constructor-in-cpp) 
  >15 The implicitly-defined copy/move constructor for a non-union class X performs a memberwise copy/move of its bases and members.
  * [how to check if default move constructor generated](https://stackoverflow.com/questions/33939687/how-can-i-check-if-a-move-constructor-is-being-generated-implicitly) [default move assignment](https://en.cppreference.com/w/cpp/language/move_assignment)
* memberwise vs bitwise shallow copy/deep copy
  * [member wise/ defalut move constructor](https://stackoverflow.com/questions/18290523/is-a-default-move-constructor-equivalent-to-a-member-wise-move-constructor) [copy types](https://stackoverflow.com/questions/42749439/what-is-the-difference-between-memberwise-copy-bitwise-copy-shallow-copy-and-d)
  * [link](https://blog.csdn.net/m0_37316917/article/details/61425215)

* C++ Return type is Class value, gcc will optimized and not generate a tempary vaviable
  * refer [link](https://blog.csdn.net/sxhelijian/article/details/50977946)
 ```cpp
 #include <iostream>
class MyClass {
private:
    int a;
    int *p;
  public:
   MyClass() {
    std::cout << "default constructor "<< std::endl;
   }
    MyClass(MyClass &&Rhs){
        std::cout << "move " << std::endl;
    }
    MyClass(MyClass &Rhs){
        std::cout << "cpy" << std::endl;
    }

    ~MyClass(){
        std::cout << "delete "<< std::endl;
    }

};

void foo(MyClass mC) {
    std::cout<< "mC "<< std::endl;
}
void foo(MyClass *pMC) {
    std::cout<< "pMc "<< std::endl;
};

MyClass create() {
    std::cout << "entrer" << std::endl;
    MyClass ret;
    std::cout << "exitr" << std::endl;
    return ret;
}

int main(){
    MyClass tem ;
    foo(tem);
    foo(std::move(tem));
    //foo(new MyClass);
   // std::cout << "beggin" << std::endl;
   /*
    foo(std::move(create()));
    std::cout << "lllll" << std::endl;
    foo(create());*/
    return 0;
}

 ```
 ```shell
 bcao@apt-sz08:/build/bcao/test_work_place/move-semantic$ g++11 test.cpp -fno-elide-constructors && ./a.out
default constructor
cpy
mC
delete
move
mC
delete
delete
bcao@apt-sz08:/build/bcao/test_work_place/move-semantic$ g++11 test.cpp && ./a.out                 
default constructor
cpy
mC
delete
move
mC
delete
delete

 ```
 
   * if returen value is class, then the move constructor will be called if there is, otherwise the copy constructor 
   
 ```cpp
 #include <iostream>
class MyClass {
private:
    int a;
    int *p;
  public:
   MyClass() {
    std::cout << "default constructor "<< std::endl;
   }
    MyClass(MyClass &&Rhs){
        std::cout << "move " << std::endl;
    }

    MyClass(MyClass &Rhs){
        std::cout << "cpy" << std::endl;
    }

    ~MyClass(){
        std::cout << "delete "<< std::endl;
    }

};

MyClass create() {
    std::cout << "entrer" << std::endl;
    MyClass ret;
    std::cout << "exitr" << std::endl;
    return ret;
}

int main(){
   create();
    return 0;
}

 ```
 
 ```shell
 ##:comment out the move constructor
 bcao@apt-sz08:/build/bcao/test_work_place/move-semantic$ g++11 test.cpp -fno-elide-constructors && ./a.out
 entrer
 default constructor
 exitr
 cpy
 delete
 delete
 bcao@apt-sz08:/build/bcao/test_work_place/move-semantic$ g++11 test.cpp -fno-elide-constructors && ./a.out
 entrer
 default constructor
 exitr
 move
 delete
 delete
 bcao@apt-sz08:/build/bcao/test_work_place/move-semantic$

 ```
