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
- If empty class the size of the class will be 1.
- if variables inside class are int(4 bit) + char(1 bit) then the size of class will NOT BE 5 it will be 8 DUE TO PADDING

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
![image](https://github.com/pratt0007/TIL/assets/100209212/6a62aee1-f8c2-4839-8b87-a1c29aecba16)

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

## Friend Class - 
- A friend class can access private and protected members of other classes in which it is declared as a friend.
- It is sometimes useful to allow a particular class to access private and protected members of other classes.
- syntax -> friend class class_name;    // declared in the base class
```cpp
using namespace std;
 
class GFG {
private:
    int private_variable;
 
protected:
    int protected_variable;
 
public:
    GFG()
    {
        private_variable = 10;
        protected_variable = 99;
    }
 
    // friend class declaration
    friend class F;
};
 
class F {
public:
    void display(GFG& t)
    {
        cout << "The value of Private Variable = "
             << t.private_variable << endl;
        cout << "The value of Protected Variable = "
             << t.protected_variable;
    }
};

```
## Friend Function
- Like a friend class, a friend function can be granted special access to private and protected members of a class in C++. 
- They are the non-member functions that can access and manipulate the private and protected members of the class for they are declared as friends.


## The 4 Pillars Of OOPS
### 1. ENCAPSULATION
- Encapsulation in C++ is defined as the wrapping up of data and information in a single unit.
- In Object Oriented Programming, Encapsulation is defined as binding together the data and the functions that manipulate them.
- Two Important  property of Encapsulation
  	- 1.Data Protection: Encapsulation protects the internal state of an object by keeping its data members private.
  	-  Access to and modification of these data members is restricted to the class’s public methods, ensuring controlled and secure data manipulation
  	- 2. Information Hiding: Encapsulation hides the internal implementation details of a class from external code.
- Encapsulation also leads to data abstraction. Using encapsulation also hides the data, as in the above example, the data of the sections like sales, finance, or accounts are hidden from any other section.
![image](https://github.com/pratt0007/TIL/assets/100209212/a919f234-ea06-42de-ae23-9beabc4d36c8)

#### Data Abstraction 
- Encapsulation also leads to data abstraction.
- Using encapsulation also hides the data, as in the above example, the data of the sections like sales, finance, or accounts are hidden from any other section.
- It reduces the complexity of the program by hiding the implementation complexities of programs.

## POLYMORPHISM
- The word “polymorphism” means having many forms.
- In simple words, we can define polymorphism as the ability of a message to be displayed in more than one form.
![image](https://github.com/pratt0007/TIL/assets/100209212/64af92ba-b914-46b8-a522-afa4c58e016b)
### 1. Compile-Time Polymorphism
- 1. Compile-Time Polymorphism
	- When there are multiple functions with the same name but different parameters, then the functions are said to be overloaded, hence this is known as Function Overloading.
 	- Functions can be overloaded by changing the number of arguments or/and changing the type of arguments.
```cpp
class Geeks {
public:
    // Function with 1 int parameter
    void func(int x)
    {
        cout << "value of x is " << x << endl;
    }
 
    // Function with same name but
    // 1 double parameter
    void func(double x)
    {
        cout << "value of x is " << x << endl;
    }
 
    // Function with same name and
    // 2 int parameters
    void func(int x, int y)
    {
        cout << "value of x and y is " << x << ", " << y
             << endl;
    }
};
```
- 2. Operator Overloading
	- C++ has the ability to provide the operators with a special meaning for a data type, this ability is known as operator overloading.
```cpp
class Complex {
private:
    int real, imag;
 
public:
    Complex(int r = 0, int i = 0)
    {
        real = r;
        imag = i;
    }
 
    // This is automatically called
    // when '+' is used with between
    // two Complex objects
    Complex operator+(Complex const& obj)
    {
        Complex res;
        res.real = real + obj.real;
        res.imag = imag + obj.imag;
        return res;
    }
    void print() { cout << real << " + i" << imag << endl; }
};
```
### 2. Runtime Polymorphism
- This type of polymorphism is achieved by Function Overriding.
- Late binding and dynamic polymorphism are other names for runtime polymorphism.
- The function call is resolved at runtime in runtime polymorphism.
-

```cpp
class Animal {
public:
    string color = "Black";
};
 
// inheriting Animal class.
class Dog : public Animal {
public:
    string color = "Grey";
};
 
// Driver code
int main(void)
{
    Animal d = Dog(); // accessing the field by reference
                      // variable which refers to derived
    cout << d.color;
}
```
output = BLACK
![image](https://github.com/pratt0007/TIL/assets/100209212/b6ad38d3-ae04-4ef1-99dc-b45fe891c99d)

#### Virtual Functions
- It is a member function that is declared in the base class using the keyword virtual and is re-defined (Overridden) in the derived class.
- The main thing to note about the program is that the derived class’s function is called using a base class pointer.
- Virtual functions allow us to create a list of base class pointers and call methods of any of the derived classes without even knowing the kind of derived class object.
![image](https://github.com/pratt0007/TIL/assets/100209212/09a3249a-1820-4096-bcc3-a5615e217e37)


## INHERITANCE
- The capability of a class to derive properties and characteristics from another class is called Inheritance.
- Inheritance is a feature or a process in which, new classes are created from the existing classes.
- The new class created is called “derived class” or “child class” and the existing class is known as the “base class” or “parent class”.
- Modes of Inheritance: There are 3 modes of inheritance.
#### 3 Modes   
- Public Mode: If we derive a subclass from a public base class. Then the public member of the base class will become public in the derived class and protected members of the base class will become protected in the derived class.
- Protected Mode: If we derive a subclass from a Protected base class. Then both public members and protected members of the base class will become protected in the derived class.
- Private Mode: If we derive a subclass from a Private base class. Then both public members and protected members of the base class will become Private in the derived class.
- Note: The private members in the base class cannot be directly accessed in the derived class, while protected members can be directly accessed.

![image](https://github.com/pratt0007/TIL/assets/100209212/e78f9612-8b3b-44b0-8a12-295c6119dbd4)


