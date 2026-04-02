# C++ Programming: Comprehensive Technical Notes

This document provides a detailed breakdown of fundamental and advanced C++ concepts, organized for clarity and technical accuracy.

---

## 1. Operators & Memory Management

### **Basic Operators**
Operators are functional symbols used to manipulate data.
* **Arithmetic:** `+`, `-`, `*`, `/`, `%` (Modulus).
* **Relational:** `==`, `!=`, `<`, `>`, `<=`, `>=`.
* **Logical:** `&&` (AND), `||` (OR), `!` (NOT).

### **Scope Resolution Operator (`::`)**
In C++, variables are defined within "scopes" (like inside a function or globally). If a local variable has the same name as a global variable, the local one takes precedence. The `::` operator allows you to bypass the local scope and access the global version.
* **Example:**
    ```cpp
    int value = 100; // Global

    int main() {
        int value = 10; // Local
        cout << "Local: " << value;     // Outputs 10
        cout << "Global: " << ::value;   // Outputs 100
    }
    ```

### **Memory Management Operators**
C++ gives you direct control over the computer's memory using the "Heap."
* **`new`:** Allocates a block of memory during program execution (Dynamic Allocation).
* **`delete`:** Releases that memory back to the system to prevent **Memory Leaks**.

* **Example:**
    ```cpp
    int* p = new int; // Allocate space for an integer
    *p = 25;
    delete p;        // Free memory
    ```

### **Manipulators**
Manipulators are used to format the output stream (how text looks in the console).
* **`endl`:** Flushes the output buffer and moves to a new line.
* **`setw(n)`:** Found in `<iomanip>`, it sets the field width for the next output.
* **`setprecision(n)`:** Controls the number of decimal places for floating-point numbers.

---

## 2. Program Structure

### **Expressions**
An expression is any valid combination of operators, constants, and variables that evaluates to a single value.
* **Example:** $z = (x + y) * 5$;

### **Control Structures**
These determine the execution flow of the program based on conditions.
* **Selection:** `if`, `else if`, `else`, and `switch`.
* **Iteration (Loops):** `for`, `while`, and `do-while`.
* **Jump Statements:** `break` (exit loop), `continue` (skip iteration), and `goto`.

---

## 3. Function Fundamentals

### **Functions in C++**
A function is a modular, reusable block of code. Every C++ program must have at least one function: `main()`.

### **Function Prototyping**
A prototype is a declaration that tells the compiler the function's "signature" (name, return type, and parameters) before the actual definition. This allows you to call functions defined at the bottom of your file.
* **Syntax:** `return_type function_name(argument_list);`

### **Inline Functions**
Calling a function normally involves "overhead" (saving registers, jumping to a memory address). For tiny functions, this overhead is wasteful. The `inline` keyword tells the compiler to replace the function call with the actual code of the function.

* **Example:**
    ```cpp
    inline int square(int x) { return x * x; }
    ```

---

## 4. Advanced Parameter Handling

### **Call by Reference**
Instead of creating a copy of the variable (Call by Value), you pass a **reference** (alias) to the original variable using the `&` symbol. Any change inside the function updates the original data.
* **Example:**
    ```cpp
    void swap(int &a, int &b) {
        int temp = a;
        a = b;
        b = temp;
    }
    ```

### **Return by Reference**
A function can return a reference to a variable that persists after the function ends (like a global or static variable). This allows the function call to act as an "L-value" (something that can be assigned a value).
* **Example:**
    ```cpp
    int global_n;
    int& getRef() { return global_n; }

    int main() {
        getRef() = 50; // global_n becomes 50
    }
    ```

### **Function Overloading**
This is a feature of Object-Oriented Programming where multiple functions can have the **same name** but **different parameters** (different types or different counts). The compiler automatically chooses the correct one based on the arguments provided.

* **Example:**
    ```cpp
    void print(int i) { cout << "Integer: " << i; }
    void print(string s) { cout << "String: " << s; }
    ```

---

## Summary Table

| Feature | Operator/Keyword | Primary Use |
| :--- | :--- | :--- |
| **Scope Resolution** | `::` | Access global variables or class members. |
| **Memory Allocation** | `new` / `delete` | Manage heap memory manually. |
| **Call by Reference** | `&` | Modify original arguments within a function. |
| **Overloading** | Same Name | Define multiple behaviors for one function name. |
| **Inline** | `inline` | Optimize performance for small, frequent functions. |
