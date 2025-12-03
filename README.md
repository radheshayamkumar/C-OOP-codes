## 4. Control Statements

### 4.1 Find Greater Number
*Write a program which finds the greater number from the given three numbers.*

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b, c;
    cout << "Enter three numbers: ";
    cin >> a >> b >> c;

    if (a >= b && a >= c) {
        cout << a << " is the greatest number.";
    } 
    else if (b >= a && b >= c) {
        cout << b << " is the greatest number.";
    } 
    else {
        cout << c << " is the greatest number.";
    }
    return 0;
}
````

### 4.2 Student Grade Calculation

*Write a program to decide the class of the student based on percentage.*

```cpp
#include <iostream>
using namespace std;

int main() {
    float percentage;
    cout << "Enter percentage: ";
    cin >> percentage;

    if (percentage >= 75) {
        cout << "Result: Distinction";
    } 
    else if (percentage >= 60) {
        cout << "Result: First Class";
    } 
    else if (percentage >= 50) {
        cout << "Result: Second Class";
    } 
    else if (percentage >= 35) {
        cout << "Result: Pass Class";
    } 
    else {
        cout << "Result: Fail";
    }
    return 0;
}
```

-----

## 5\. Function Overloading

*Write a program to implement function overloading.*

```cpp
#include <iostream>
using namespace std;

// Function for integer
void display(int i) {
    cout << "Integer value: " << i << endl;
}

// Function for double (Same name, different parameter)
void display(double f) {
    cout << "Double value: " << f << endl;
}

int main() {
    display(5);      
    display(5.5);    
    return 0;
}
```

-----

## 6\. Constructor and Destructor

*Write a program to demonstrate use of constructor and Destructor.*

```cpp
#include <iostream>
using namespace std;

class Demo {
public:
    // Constructor
    Demo() {
        cout << "Constructor Called: Object Created" << endl;
    }
    // Destructor
    ~Demo() {
        cout << "Destructor Called: Object Destroyed" << endl;
    }
};

int main() {
    cout << "Inside Main..." << endl;
    Demo d; 
    cout << "Exiting Main..." << endl;
    return 0;
}
```

-----

## 7\. Friend Function

*Write a program to demonstrate use of friend function.*

```cpp
#include <iostream>
using namespace std;

class Box {
private:
    int length;
public:
    Box() { length = 10; }
    
    // Friend function declaration
    friend void showLength(Box b);
};

void showLength(Box b) {
    // Accessing private member directly
    cout << "Length is: " << b.length << endl;
}

int main() {
    Box b;
    showLength(b);
    return 0;
}
```

-----

## 8\. Friend Class

*Write a program to demonstrate use of friend class.*

```cpp
#include <iostream>
using namespace std;

class A {
private:
    int x = 50;
    friend class B; // Class B is a friend of A
};

class B {
public:
    void display(A obj) {
        cout << "Value of x in Class A is: " << obj.x << endl;
    }
};

int main() {
    A objA;
    B objB;
    objB.display(objA);
    return 0;
}
```

-----

## 9\. Inheritance

### 9.1 Single Inheritance

*Parent -\> Child*

```cpp
#include <iostream>
using namespace std;

class Parent {
public:
    void msg1() { cout << "This is Parent class." << endl; }
};

class Child : public Parent {
public:
    void msg2() { cout << "This is Child class." << endl; }
};

int main() {
    Child c;
    c.msg1();
    c.msg2();
    return 0;
}
```

### 9.2 Multi-level Inheritance

*GrandParent -\> Parent -\> Child*

```cpp
#include <iostream>
using namespace std;

class GrandParent {
public:
    void msg1() { cout << "GrandParent Class" << endl; }
};

class Parent : public GrandParent {
public:
    void msg2() { cout << "Parent Class" << endl; }
};

class Child : public Parent {
public:
    void msg3() { cout << "Child Class" << endl; }
};

int main() {
    Child c;
    c.msg1(); 
    c.msg2(); 
    c.msg3(); 
    return 0;
}
```

### 9.3 Multiple Inheritance

*Father + Mother -\> Child*

```cpp
#include <iostream>
using namespace std;

class A {
public:
    void showA() { cout << "Class A function" << endl; }
};

class B {
public:
    void showB() { cout << "Class B function" << endl; }
};

// Child C inherits from both A and B
class C : public A, public B {
public:
    void showC() { cout << "Class C function" << endl; }
};

int main() {
    C obj;
    obj.showA();
    obj.showB();
    obj.showC();
    return 0;
}
```

### 9.4 Hierarchical Inheritance

*Animal -\> Dog, Animal -\> Cat*

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() { cout << "Animal is eating..." << endl; }
};

class Dog : public Animal {
public:
    void bark() { cout << "Dog is barking..." << endl; }
};

class Cat : public Animal {
public:
    void meow() { cout << "Cat is meowing..." << endl; }
};

int main() {
    Dog d;
    Cat c;
    d.eat(); d.bark();
    c.eat(); c.meow();
    return 0;
}
```

-----

## 10\. Operator Overloading

### 10.1 Operator Overloading (Member Function)

*Overloading unary minus (-)*

```cpp
#include <iostream>
using namespace std;

class Number {
    int n;
public:
    Number() { n = 10; }
    
    // Overloading '-' unary operator
    void operator - () {
        n = -n;
    }
    
    void display() { cout << "Number: " << n << endl; }
};

int main() {
    Number obj;
    -obj; 
    obj.display();
    return 0;
}
```

### 10.2 Operator Overloading (Friend Function)

*Overloading unary minus (-) using friend*

```cpp
#include <iostream>
using namespace std;

class Number {
    int n;
public:
    Number() { n = 20; }
    void display() { cout << "Number: " << n << endl; }
    
    friend void operator - (Number &obj);
};

void operator - (Number &obj) {
    obj.n = -obj.n;
}

int main() {
    Number obj;
    -obj; 
    obj.display();
    return 0;
}
```

-----

## 11\. Virtual Functions

*Demonstrate Runtime Polymorphism*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base Class Show" << endl;
    }
};

class Derived : public Base {
public:
    void show() {
        cout << "Derived Class Show" << endl;
    }
};

int main() {
    Base *bptr;
    Derived d;
    bptr = &d;
    
    // Calls Derived show() because of virtual keyword
    bptr->show(); 
    return 0;
}
```

-----

## 12 & 13. Exception Handling

*Throw divide by zero exception*

```cpp
#include <iostream>
using namespace std;

int main() {
    int numerator, denominator, result;
    cout << "Enter Numerator: ";
    cin >> numerator;
    cout << "Enter Denominator: ";
    cin >> denominator;

    try {
        if (denominator == 0) {
            throw denominator; // Throwing exception
        }
        result = numerator / denominator;
        cout << "Result: " << result << endl;
    }
    catch (int e) {
        cout << "Exception: Cannot divide by " << e << endl;
    }

    return 0;
}
```
