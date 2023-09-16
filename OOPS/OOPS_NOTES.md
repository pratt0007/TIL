# OOPS 
- As the name suggests uses objects in programming.
- Object-oriented programming aims to implement real-world entities like inheritance, hiding, polymorphism, etc. in programming.
- The main aim of OOP is to bind together the data and the functions that operate on them so that no other part of the code can access this data except that function.
- The main difference between C++ and C languange is that C++ is object oriented lang.
![image](https://github.com/pratt0007/TIL/assets/100209212/0932f045-33c5-4a42-91e0-78cf9979c302)
## CLASS
- The building block of C++ that leads to Object-Oriented programming is a Class.
- It is a user-defined data type, which holds its own data members and member functions, which can be accessed and used by creating an instance of that class(OBJECT)
- A class is like a blueprint for an object.

 ## OBJECT
 - Object is an instance of class.
 - When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated.
 - Objects take up space in memory and have an associated address like a record in pascal or structure or union. 
```cpp
// C++ Program to show the syntax/working of Objects as a
// part of Object Oriented PProgramming
#include <iostream>
using namespace std;

class person {
	char name[20];
	int id;

public:
	void getdetails() {}
};

int main()
{

	person p1; // p1 is a object
	return 0;
}

```

### Member Function-
There are 2 ways to define a member function:
- Inside class definition
- Outside class definition
- To define a member function outside the class definition we have to use the scope resolution:: operator along with the class name and function name.
```cpp
class Geeks
{
    public:
    string geekname;
    int id;
      
    // printname is not defined inside class definition
    void printname();
      
    // printid is defined inside class definition
    void printid()
    {
        cout <<"Geek id is: "<<id;
    }
};
  
// Definition of printname using scope resolution operator ::
void Geeks::printname()
{
    cout <<"Geekname is: "<<geekname; 
}
```

## Constructor
- Constructors are special class members which are called by the compiler every time an object of that class is instantiated.
-  Constructors have the same name as the class and may be defined inside or outside the class definition.
-  There are 3 types of constructors:
    - Default Constructors
    - Parameterized Constructors
    - Copy Constructors
- A Copy Constructor creates a new object, which is an exact copy of the existing object. The compiler provides a default Copy Constructor to all the classes.
- SYNTAX = class-name (class-name &){}
- THIS keyword -> is used to refer the current instance of class.
```CPP
class Geeks
{
    public:
    int id;
      
    //Default Constructor
    Geeks()
    {
        cout << "Default Constructor called" << endl; 
        id=-1;
    }
      
    //Parameterized Constructor
    Geeks(int x)
    {
        cout <<"Parameterized Constructor called "<< endl;
        id=x;
    }
};
```
## Distructor
- Destructor is another special member function that is called by the compiler when the scope of the object ends.
```cpp
class Geeks {
    // Access specifier
public:
    // Data  Members
    string geekname;
    // Member Functions()
    void printname() { cout << "Geekname is:" << geekname; }
};
```

## Access Modifiers
- Access modifiers are used to implement an important aspect of Object-Oriented Programming known as Data Hiding.
- There are 3 types of access modifiers available in C++:
    - Public
    - Private (if not defined by default is private)
    - Protected
#### 1. Public
- All the class members declared under the public specifier will be available to everyone.
-  The data members and member functions declared as public can be accessed by other classes and functions too.
-  The public members of a class can be accessed from anywhere in the program using the direct member access operator (.) with the object of that class. 
#### 2. Private
- The class members declared as private can be accessed only by the member functions inside the class.
-  They are not allowed to be accessed directly by any object or function outside the class.
-  Only the member functions or the friend functions are allowed to access the private data members of the class.
-  Private data can be accessed using Getter Setter method also.
#### 3. Protected 
- The protected access modifier is similar to the private access modifier in the sense that it can’t be accessed outside of its class unless with the help of a friend class.
-  The difference is that the class members declared as Protected can be accessed by any subclass (derived class) of that class as well. 

