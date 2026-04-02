# Object-Oriented Programming (OOP) in C++ - Complete Study Notes

## 1. Classes and Objects Introduction
To understand C++, you need to understand the difference between a blueprint and the actual thing built from that blueprint.

* **Class:** A **blueprint** or a template. It doesn't physically exist in your computer's memory; it just defines what something *should* look like and what it *should* be able to do. It binds data and functions together.
* **Object:** A real, usable **instance** created from the blueprint. It takes up space in memory. 

**Real-World Example:**
* **Class:** The concept of a "Bank Account."
* **Object:** *Your* specific bank account with ₹5,000 in it.

---

## 2. Specifying a Class
You create a blueprint using the `class` keyword. You define its **Data Members** (variables) and **Member Functions** (actions). 
Access Specifiers control visibility:
* `private`: Hidden from the outside world (default).
* `public`: Accessible from anywhere.

```cpp
class BankAccount {
private:
    double balance; // Data Member
public:
    void setBalance(double amount); // Member Function
}; // Don't forget the semicolon!
```

---

## 3. Defining Member Functions
You can define *how* functions work in two places:

**A. Inside the Class Definition:** (Best for short functions)
```cpp
class BankAccount {
private:
    double balance;
public:
    void displayBalance() {
        cout << "Balance is: " << balance << endl; 
    }
};
```

**B. Outside the Class Definition:** (Best for keeping blueprints clean)
Requires the **Scope Resolution Operator** (`::`).
```cpp
void BankAccount::setBalance(double amount) {
    balance = amount;
}
```

---

## 4. C++ Program with a Class
To use the class, create an **Object** inside `main()` and use the **dot operator (`.`)** to access its public functions.

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance;
public:
    void setBalance(double amount) { balance = amount; }
    void displayBalance() { cout << "Current Balance: $" << balance << endl; }
};

int main() {
    BankAccount myAccount; // Create Object
    myAccount.setBalance(1500.50); // Dot operator
    myAccount.displayBalance();
    return 0;
}
```

---

## 5. Nesting of Member Functions
**Nesting** means one member function calls *another* member function of the **same** class. You do **not** need the dot operator for this.

```cpp
class Account {
public:
    double calculateInterest(double balance) { return balance * 0.05; }

    void printReport(double balance) {
        // Calling another function directly (Nesting)
        double interest = calculateInterest(balance); 
        cout << "Interest: " << interest << endl;
    }
};
```

---

## 6. Private Member Functions
Internal "helper" functions. They cannot be called directly from `main()`. They can only be triggered by other functions within that same class via nesting.

```cpp
class SecureAccount {
private:
    double balance = 5000;
    bool checkSufficientFunds(double amount) { // Private helper
        return amount <= balance;
    }

public:
    void withdraw(double amount) {
        if (checkSufficientFunds(amount)) { // Nesting call
            balance -= amount;
            cout << "Withdrawal successful." << endl;
        }
    }
};
```

---

## 7. Memory Allocation for Objects
* **Classes do not take up memory; only Objects do.**
* When an object is created, memory is allocated for its variables.
* To save space, functions are stored only **once** centrally, and all objects share those same instructions.

---

## 8. Static Data Members
A variable **shared** by all objects of that class. Created only once. If one object changes it, every object sees the change. Must be defined *outside* the class to allocate memory.

```cpp
class Bank {
public:
    static int totalCustomers; // Shared variable
    Bank() { totalCustomers++; }
};

// Memory allocation outside the class
int Bank::totalCustomers = 0; 
```

---

## 9. Static Member Functions
* Can **only** access other static variables or static functions.
* Can be called directly using the Class name, without needing to create an object.

```cpp
class Bank {
private:
    static int totalCustomers;
public:
    static void showTotal() { cout << "Customers: " << totalCustomers << endl; }
};
int Bank::totalCustomers = 0;

int main() {
    Bank::showTotal(); // Called without an object
    return 0;
}
```

---

## 10. Arrays within a Class
An array inside a class, used when a single object needs to hold a list of items (e.g., a student's grades).

```cpp
class Student {
private:
    int marks[3]; // Array inside class
public:
    void setMarks(int m1, int m2, int m3) {
        marks[0] = m1; marks[1] = m2; marks[2] = m3;
    }
};
```

---

## 11. Arrays of Objects
An array where every "slot" holds a complete object with its own data and functions.

```cpp
class Employee {
private:
    int id;
public:
    void setId(int empId) { id = empId; }
};

int main() {
    Employee company[3]; // Array of 3 Employee objects
    company[0].setId(101);
    company[1].setId(102);
    return 0;
}
```

---

## 12. Objects as Function Arguments
Handing over an object to a function so the function can read or modify its data.

```cpp
class Box {
public:
    int weight;
    // Takes another Box object as an argument
    void addWeights(Box b1, Box b2) {
        weight = b1.weight + b2.weight;
    }
};
```

---

## 13. Friendly Functions (Friend Functions)
An outside, non-member function that is granted a "VIP pass" to access a class's `private` data.

```cpp
class BankAccount {
private:
    int hiddenWealth = 1000000;
    // Declare the outside function as a friend
    friend void taxInspector(BankAccount account); 
};

// Outside function accessing private data
void taxInspector(BankAccount account) {
    cout << "Found: $" << account.hiddenWealth << endl;
}
```

---

## 14. Returning Objects
A function can create a temporary object, set its data, and return it. The return type must be the Class name.

```cpp
class Time {
public:
    int hours;
    
    // Returns a Time object
    Time addTime(Time t2) {
        Time temp; // Temporary object
        temp.hours = hours + t2.hours; 
        return temp; // Returning the new object
    }
};
```
