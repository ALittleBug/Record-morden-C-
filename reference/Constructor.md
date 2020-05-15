* Find default copy constructor(shallow copy) [Useful basic C++ blog for some tips](http://www.fredosaurus.com/notes-cpp/index.html)
  * Whether the constructor can be called depends on whether a new object is generated
  * foo(MyClass &rM) foo (MyClass &&rM) foo(MyClass vM) 
  * [Bo Qin vedio about move semantic](https://www.youtube.com/watch?v=IOkgBrXCtfo)
  
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
