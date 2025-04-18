# 👨‍🏫 Instructor Introduction

**Name:** Syed Hamed Raza  
**Education:** MS in Computer Science from HUST, Wuhan, China  
**Current Roles:**  
- PhD Scholar at COMSATS University  
- Lecturer at University of Management and Technology (UMT), Lahore  

# 🎓 Program Structure in C++
## 🎯 Learning Objectives

By the end of this lecture, students should be able to:

- Understand the basic structure of a C++ program  
- Use I/O statements correctly  
- Describe and use preprocessor directives  
- Identify and use appropriate data types in C++   

## 🧱 1. Program Construction in C++

A basic C++ program includes the following:

```cpp
#include <iostream>            // Preprocessor directive
using namespace std;           // Standard namespace

int main()                     // Main function
{
    cout << "Welcome to C++!"; // Output statement
    return 0;                  // Return value
}
```
### 🔹 Key Sections

| Section              | Role                                           |
|----------------------|------------------------------------------------|
| `#include <iostream>` | Includes input/output stream library           |
| `using namespace std;` | Avoids writing `std::` before `cin` and `cout` |
| `int main()`         | Starting point of the program                   |
| `{ }`                | Block of code for the main function             |
| `return 0;`          | Exits the program successfully                  |

## 🧾 2. Input/Output Statements

### 🔹 Output: `cout`

Used to display output to the console.

```cpp
cout << "Hello, World!";
```
### 🔹 Input: `cin`

Used to take input from the user.

```cpp
string name;
cin >> name;
```
### 🧠 Chained I/O Example
```cpp
int age;
string name;

cout << "Enter name and age: ";
cin >> name >> age;

cout << "Name: " << name << ", Age: " << age;
```
### 🔸 Notes

- `<<` is the **insertion operator** (used for output)
- `>>` is the **extraction operator** (used for input)
## 🔧 3. Preprocessor Directives

### 📌 What are they?
Commands that are executed **before compilation** begins. They help manage code dependencies and configurations.

### 🔹 Common Directives:

| Directive          | Purpose                         |
|--------------------|---------------------------------|
| `#include <...>`   | Includes standard libraries     |
| `#define`          | Defines constants/macros        |
| `#ifndef / #endif` | Conditional compilation          |

```cpp
#include <iostream>
#define PI 3.14159          // Constant macro
#define SQUARE(x) ((x)*(x)) // Function-like macro

using namespace std;

int main() {
    double radius;
    cout << "Enter the radius of the circle: ";
    cin >> radius;

    // Use PI to calculate area
    double area = PI * SQUARE(radius); // SQUARE(radius) is replaced at compile time
    cout << "Area of the circle: " << area << endl;

    return 0;
}
```
### 🔍 Explanation:

| Line                         | Purpose                                                         |
|------------------------------|-----------------------------------------------------------------|
| `#define PI 3.14159`         | Replaces all occurrences of `PI` with `3.14159` before compilation |
| `#define SQUARE(x) ((x)*(x))`| Macro to calculate square of a value                           |
| `cin >> radius`              | Takes input from user                                           |
| `PI * SQUARE(radius)`        | Expands to `3.14159 * ((radius)*(radius))`                     |
## ✅ What is `#ifndef` and `#endif` in C++?

These are preprocessor directives used to **prevent multiple inclusions** of the same header file — a common practice in large C++ projects.

---

### 🔹 `#ifndef` stands for:
**"If Not Defined"**

It checks whether a macro name has **NOT** been defined before. If not, the code between `#ifndef` and `#endif` will be included.

---

### 🔹 `#endif` stands for:
**"End If"**

It simply closes the `#ifndef`, `#ifdef`, or `#if` directive block.

---

### 💡 Why use `#ifndef`?
To **avoid duplicate inclusion** of the same file, especially header files, which can cause **redefinition errors**.

> Example usage in a header file:
```cpp
#ifndef MY_HEADER_H
#define MY_HEADER_H

// Header file content goes here

#endif
```
## 🧾 Example: Using `#ifndef` in a Header File

### 👉 Circle.h (Header File)

```cpp
#ifndef CIRCLE_H   // Check if CIRCLE_H is not defined
#define CIRCLE_H   // Define CIRCLE_H

class Circle {
private:
    double radius;
public:
    Circle(double r);
    double area();
};

#endif  // End of conditional inclusion
```
### 👉 Circle.cpp (Implementation File)

```cpp
#include "Circle.h"
#define PI 3.14159

Circle::Circle(double r) {
    radius = r;
}

double Circle::area() {
    return PI * radius * radius;
}
```
### 👉 main.cpp (Main Program)

```cpp
#include <iostream>
#include "Circle.h"   // Included only once due to #ifndef

using namespace std;

int main() {
    Circle c(5);
    cout << "Area: " << c.area() << endl;
    return 0;
}
```
### 💡 Why this is important:

Without `#ifndef`, if `Circle.h` were included multiple times (directly or indirectly), it could cause **multiple definition errors** at compile time.

---

### 🖥️ Output:

```cpp
Area: 78.5398
```
## 🧮 4. Data Types in C++

C++ provides several built-in data types categorized as:

---

### 🔹 Basic Data Types

These are the fundamental types provided by the language:

| Data Type | Size (Approx.) | Example                    | Description                              |
|-----------|----------------|----------------------------|------------------------------------------|
| `int`     | 4 bytes         | `int x = 10;`              | Stores integer (whole) numbers           |
| `float`   | 4 bytes         | `float pi = 3.14;`         | Stores single-precision decimal values   |
| `double`  | 8 bytes         | `double bigPi = 3.1415926;`| Stores double-precision decimal values   |
| `char`    | 1 byte          | `char grade = 'A';`        | Stores a single character                |
| `bool`    | 1 byte          | `bool pass = true;`        | Stores boolean values: `true` or `false` |

---

### 🔹 Derived Data Types

These are built using basic data types and allow more complex data handling:

- **Arrays**: Collection of elements of the same type stored in contiguous memory  
  - Example: `int numbers[5];`
- **Pointers**: Variables that store the memory address of another variable  
  - Example: `int* ptr = &x;`
- **Functions**: Reusable blocks of code that perform specific tasks  
  - Example: `int add(int a, int b);`

---

### 🔹 User-defined Data Types

These allow users to define their own complex types:

- **`struct`**: Groups related variables of different types  
  - Example:  
    ```cpp
    struct Student {
        string name;
        int age;
    };
    ```
- **`class`**: Blueprint for creating objects, includes data and functions  
  - Supports features like encapsulation and inheritance  
- **`union`**: Similar to `struct` but stores only one variable at a time to save memory  
  - Example:  
    ```cpp
    union Data {
        int i;
        float f;
    };
    ```
## 🧪 Practice Example

**Write a program to input the radius of a circle, then compute and display its area:**

```cpp
#include <iostream>
#define PI 3.14159
using namespace std;

int main() {
    float radius, area;
    cout << "Enter radius: ";
    cin >> radius;
    area = PI * radius * radius;
    cout << "Area = " << area;
    return 0;
}
```
