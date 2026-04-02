# C++ Programming: Detailed Technical Notes



## 1. Operators and Scope

### **Operators in C++**
Operators are specialized symbols that perform operations on operands (variables and values).
* **Arithmetic Operators:** Used for mathematical calculations ($+$, $-$, $*$, $/$, $\%$).
* **Relational Operators:** Used to compare two values ($==$, $!=$, $<$, $>$, $<=$, $>=$). They return a boolean value (`true` or `false`).
* **Logical Operators:** Used to combine multiple conditions ($&&$, $||$, $!$).

### **Scope Resolution Operator (`::`)**
The `::` operator is used to identify and specify the scope of an identifier (variable or function). Its most common use is to access a **global variable** when a local variable with the same name exists.

* **Example:**
    ```cpp
    int x = 100; // Global x

    int main() {
        int x = 10; // Local x
        std::cout << "Local x: " << x << std::endl;      // Prints 10
        std::cout << "Global x: " << ::x << std::endl;    // Prints 100
    }
    ```

---

## 2. Memory and Formatting

### **Memory Management Operators (`new` & `delete`)**
C++ allows **Dynamic Memory Allocation**, where you request memory from the system while the program is running (on the "Heap") rather than at compile-time.
* **`new`**: Allocates memory of a specific type and returns its address.
* **`delete`**: Releases the memory allocated by `new` to prevent **memory leaks**.



* **Example:**
    ```cpp
    int* ptr = new int; // Requests memory for an integer
    *ptr = 42;
    std::cout << *ptr;
    delete ptr;         // Frees the memory
    ```

### **Manipulators**
Manipulators are operators used to format the way data is displayed in the console. They are usually found in the `<iostream>` and `<iomanip>` libraries.
* **`endl`**: Moves the cursor to the next line and clears the buffer.
* **`setw(n)`**: Sets the width of the output field to $n$ characters.
* **`setprecision(n)`**: Sets the number of decimal places for floating-point numbers.

---

## 3. Control Structures and Expressions

### **Expressions**
An expression is a sequence of operators and operands that specifies a computation.
* **Example:** `result = (a + b) * (c / d);`

### **Control Structures**
These blocks control the execution flow based on logic:
1.  **Selection Structures**: `if-else` and `switch-case` (deciding which branch to take).
2.  **Iteration Structures (Loops)**: `for`, `while`, and `do-while` (repeating code).
3.  **Jump Statements**: `break` (exit loop), `continue` (skip to next iteration).

---

## 4. Function Mechanics

### **Functions in C++**
A function is a grouped set of statements that perform a specific task. They help in **modularizing** code, making it easier to read and debug.

### **Function Prototyping**
A prototype is a declaration that tells the compiler about a function's name, return type, and parameters before the function is actually called. This is necessary if the function is defined *after* the `main()` function.
* **Example:**
    ```cpp
    int add(int, int); // Prototype

    int main() {
        return add(5, 3);
    }

    int add(int a, int b) { return a + b; } // Definition
    ```

### **Inline Functions**
When a function is called, the CPU jumps to the function's memory address, executes it, and jumps back. For tiny functions, this "jumping" takes more time than the work itself. The `inline` keyword tells the compiler to replace the function call with the actual code to eliminate jump overhead.



---

## 5. Advanced Parameter and Return Methods

### **Call by Reference**
In "Call by Value," a copy of the variable is made. In **Call by Reference**, you pass the actual variable's address using the `&` symbol. This allows the function to modify the original variable directly.



* **Example:**
    ```cpp
    void makeDouble(int &n) {
        n = n * 2;
    }

    int main() {
        int val = 5;
        makeDouble(val); // val is now 10
    }
    ```

### **Return by Reference**
A function can return a reference to a variable that persists after the function returns (like a global or static variable). This allows a function call to appear on the **left side** of an assignment.
* **Example:**
    ```cpp
    int global_val = 0;
    int& getRef() { return global_val; }

    int main() {
        getRef() = 100; // global_val becomes 100
    }
    ```

### **Function Overloading**
This allows you to have multiple functions with the **same name** as long as their **parameter lists are different** (different types or different number of arguments). It is a form of compile-time polymorphism.
* **Example:**
    ```cpp
    int area(int side) { return side * side; }          // Square
    int area(int length, int breadth) { return length * breadth; } // Rectangle
    ```

## Summary Table

| Feature | Operator/Keyword | Primary Use |
| :--- | :--- | :--- |
| **Scope Resolution** | `::` | Access global variables or class members. |
| **Memory Allocation** | `new` / `delete` | Manage heap memory manually. |
| **Call by Reference** | `&` | Modify original arguments within a function. |
| **Overloading** | Same Name | Define multiple behaviors for one function name. |
| **Inline** | `inline` | Optimize performance for small, frequent functions. |
