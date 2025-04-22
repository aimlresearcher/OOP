# 👨‍🏫 Instructor Introduction

**Name:** Syed Hamed Raza  
**Education:** MS in Computer Science from HUST, Wuhan, China  
**Current Roles:**  
- PhD Scholar at COMSATS University  
- Lecturer at University of Management and Technology (UMT), Lahore  

# 🎓 Week-01: Overview of Programming Fundamentals in C++

## 📘 Textbook:
1. *"Starting Out with C++ from Control Structures to Objects"*, **9th/10th
Edition by Tony Gaddis** 
2. **Deitel & Deitel**, *"C++ How to Program"*, **10th Edition** 

# 🎓 Overview of Programming Fundamentals in C++

## 🎯 Learning Objectives

By the end of this lecture, students should be able to:

- Understand the structure of a basic C++ program  
- Identify key programming concepts (variables, data types, operators)  
- Use input/output operations  
- Write and compile a simple C++ program  

## 🧠 1. Introduction to Programming and C++

### 🔹 What is Programming?
Programming is the process of designing and implementing instructions (code) that a computer can follow to perform a specific task.

### 🔹 Why C++?
- Developed by **Bjarne Stroustrup**  
- Combines the power of **C** with **object-oriented features**  
- Widely used in **systems programming**, **game development**, and **real-time systems**

### 🔹 Features of C++
- **High performance**  
- **Object-Oriented Programming**  
- **Rich standard library**  
- **Platform independent** (with compiler support)

## 🧱 2. Structure of a Simple C++ Program

```cpp
#include <iostream>        // Preprocessor directive
using namespace std;       // Use the standard namespace

int main()                 // Main function - program execution starts here
{
    cout << "Hello, World!" << endl;  // Output statement
    return 0;              // Exit code
}
```
## 📌 Key Components:

| Component    | Description                                |
|--------------|--------------------------------------------|
| `#include`   | Preprocessor directive to include libraries |
| `main()`     | Entry point of every C++ program            |
| `cout`       | Used for output                             |
| `<<`         | Stream insertion operator                   |
| `return 0;`  | Ends the program with success               |
---
## 📊 3. Data Types & Variables

### 🔹 Basic Data Types

| Type     | Description             | Example   |
|----------|-------------------------|-----------|
| `int`    | Integer numbers         | `10`      |
| `float`  | Decimal numbers         | `3.14`    |
| `double` | Large decimal numbers   | `3.14159` |
| `char`   | Single character        | `'A'`     |
| `bool`   | Boolean value           | `true`    |
### 🔹 Variable Declaration

```cpp
int age = 20;
float pi = 3.14;
char grade = 'A';
bool passed = true;
```
## 🧮 4. Operators in C++

| Type        | Symbols                  | Example   |
|-------------|--------------------------|-----------|
| Arithmetic  | `+  -  *  /  %`           | `a + b`   |
| Relational  | `==  !=  >  <  >=  <=`    | `a != b`  |
| Logical     | `&&`  &#8741;  `!`             | `a && b`  |
| Assignment  | `=  +=  -=  *=  /=  %=`   | `x += 2`  |

## ⌨️ 5. Input and Output

### 🔹 Output: `cout`

```cpp
cout << "Age: " << age << endl;
```
### 🔹 Input: `cin`
```cpp
cin >> age;
```
> 💡 **Make sure to** `#include <iostream>` **and use** `using namespace std;`
## 🧩 6. Sample Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int num1, num2, sum;
    cout << "Enter two numbers: ";
    cin >> num1 >> num2;
    sum = num1 + num2;
    cout << "Sum is: " << sum << endl;
    return 0;
}
```
