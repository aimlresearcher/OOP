# 🎓 Constants and Constant Functions in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Define and use **constant variables** and **functions** in procedural-style C++  
- Understand the role of `const` in ensuring **immutability**  
- Apply the concept of **constant member functions** in OOP  
- Recognize the benefits of using `const` for **secure and stable code**

---

## 📌 1. Constant Variables in Procedural Paradigm

In **procedural programming** (non-OOP), a constant variable is declared using the `const` keyword.  
> 🧠 Its value **cannot be changed** after initialization.

### 🔹 Syntax:

```cpp
const int MAX = 100;
```
### 🔸 Example: Constant Variable

```cpp
#include <iostream>
using namespace std;

int main() {
    const float PI = 3.14159;
    cout << "PI = " << PI;
    // PI = 3.14; // ❌ Error: Cannot modify a const variable
    return 0;
}
```
## ✅ Benefits of Using `const`:

- 🔒 **Prevents accidental modification** of important values  
- 🧹 Makes the code **easier to maintain and debug**  
- 📏 Used to represent **fixed values** like tax rates, limits, constants in calculations

---

## 🧠 2. Constant Functions in Procedural Style

You can pass **parameters as constant** to ensure they are **not modified** inside the function.

### 🔹 Syntax:

```cpp
void show(const string msg);
```
### 🔸 Example: Constant Parameter in Function

```cpp
void greet(const string name) {
    cout << "Hello, " << name << endl;
    // name = "Ali"; // ❌ Error: Cannot modify a const parameter
}
```
> ✅ Useful when passing large objects by reference to **avoid unnecessary copying** and to **prevent accidental changes**.

---

## 🧱 3. Constant Member Functions in OOP

A **constant member function** is a class method that **does not modify** the object’s state (i.e., it doesn't change any data members).

### 🔹 Syntax:

```cpp
class MyClass {
    int value;
public:
    int getValue() const;  // Constant member function
};
```
### 🔸 Example: Constant Member Function

```cpp
class Student {
    string name;
    int rollNo;

public:
    Student(string n, int r) : name(n), rollNo(r) {}

    void display() const {
        cout << "Name: " << name << ", Roll No: " << rollNo << endl;
        // rollNo++; ❌ Error: Cannot modify member in const function
    }
};
```
## 📌 Rules for Constant Member Functions

| Rule                            | Description                                        |
|---------------------------------|----------------------------------------------------|
| **Can read data members**       | ✅ Yes                                              |
| **Can modify data members**     | ❌ No — modification is not allowed                |
| **Can call other const functions** | ✅ Yes                                          |
| **Cannot call non-const functions** | ❌ No — violates const-correctness             |

---

## 🔒 4. `const` Objects and `const` Pointers in OOP

### 🔹 `const` Object:

A `const` object can **only call `const` member functions**.

```cpp
const Student s("Ali", 123);
// s.setName("Hassan"); // ❌ Error: Only const member functions can be called
```
### 🔹 `const` Pointer to Object

A pointer to a **const object** means you **cannot modify** the object's members (only `const` functions can be called).

```cpp
const Student* ptr = new Student("Sara", 456);
ptr->display();     // ✅ Allowed
// ptr->setName("Zara"); ❌ Not allowed
```
## ⚙️ 5. Why Use `const` in OOP?

| Reason               | Benefit                                                   |
|----------------------|-----------------------------------------------------------|
| **Ensures safety**   | Prevents accidental modifications to data                 |
| **Improves readability** | Makes programmer intentions **clear and explicit**   |
| **Enables compatibility** | Required for working with **`const` objects** or **STL** |
