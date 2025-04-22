# 👨‍🏫 Instructor Introduction

**Name:** Syed Hamed Raza  
**Education:** MS in Computer Science from HUST, Wuhan, China  
**Current Roles:**  
- PhD Scholar at COMSATS University  
- Lecturer at University of Management and Technology (UMT), Lahore  

# 🎓 Functions in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the **concept and purpose** of functions  
- Define and **call functions** in C++  
- Differentiate between **user-defined**, **library**, and **recursive** functions  
- Use **return values** and **parameters**  
- Apply **function overloading** and **default arguments**

---

## 📌 1. What is a Function?

A **function** is a block of code that performs a **specific task** and can be **called multiple times** to reuse that logic.

---

## 🧠 2. Why Use Functions?

- ✅ Code **reusability**  
- ✅ Better **readability** and **structure**  
- ✅ Easier **debugging** and **maintenance**  
- ✅ Divides the program into **logical sections**
## 🧱 3. Function Syntax

```cpp
return_type function_name(parameter_list) {
    // body
    return value;  // if return_type is not void
}
```
### 🔹 4. Function Example

```cpp
#include <iostream>
using namespace std;

// Function to add two numbers
int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(5, 3);
    cout << "Sum: " << result;
    return 0;
}
```
## 🧭 5. Types of Functions

| Type                   | Description                                 |
|------------------------|---------------------------------------------|
| **Library Functions**  | Predefined in C++ (e.g., `cout`, `sqrt`)    |
| **User-Defined Functions** | Created by the programmer               |
| **Recursive Functions**| A function that **calls itself**            |

## 💡 6. Function with No Return and No Parameter

```cpp
void greet() {
    cout << "Hello, Student!";
}

int main() {
    greet();  // function call
}
```
## 🔄 7. Return Value Functions

```cpp
float square(float num) {
    return num * num;
}
```
> 📌 A function can only return **one value directly**, but you can use **pointers or references** to return **multiple values**.
## 🛠 8. Function Prototypes

Function prototypes help **declare functions before they are defined**, allowing for **modular and organized code**.

```cpp
int add(int, int);  // Function prototype

int main() {
    cout << add(3, 7);
}

int add(int a, int b) {
    return a + b;
}
```
## 🌀 9. Recursive Function

A **recursive function** is a function that **calls itself** until a **base condition** is met.

```cpp
int factorial(int n) {
    if (n <= 1)
        return 1;
    else
        return n * factorial(n - 1);
}
```
## 🔁 10. Function Overloading

Function **overloading** allows **multiple functions with the same name** but **different parameters**.

```cpp
int add(int a, int b) {
    return a + b;
}

float add(float a, float b) {
    return a + b;
}
```
> ✅ The compiler decides which version of the overloaded function to use based on the **argument types** provided in the function call.
## ⚙️ 11. Default Arguments

Default arguments allow you to **assign default values** to parameters in a function definition.

```cpp
int power(int base, int exp = 2) {
    int result = 1;
    for (int i = 0; i < exp; i++) result *= base;
    return result;
}

int main() {
    cout << power(3);      // 3^2 = 9
    cout << power(3, 3);   // 3^3 = 27
}
```
⚠️ 12. Common Mistakes to Avoid

Mistake	Issue
Not returning value from non-void	Compilation error
Mismatching parameters	Runtime error or wrong results
Missing function prototype	Compiler error (if called before defined)