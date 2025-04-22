# 🎓 Lecture 20: Scope of Class Members in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the meaning of **scope** in the context of class members  
- Identify **where and how** data members and member functions can be accessed  
- Explain the difference between **class scope**, **object scope**, and **function scope**  
- Appreciate how **access specifiers and scope** work together to **control access**

---

## 📌 1. What Is Scope?

In C++, **scope** refers to the **visibility** and **lifetime** of a variable or function —  
in other words, **where** it can be accessed from.

---

## 🧱 2. Types of Scope for Class Members

### 🔹 A. Class Scope

- Members declared inside a class have **class scope**  
- Their names are **known only inside the class** unless marked `public`

```cpp
class Student {
private:
    int rollNo;       // Class scope
public:
    void setRollNo(int r);  // Class scope
};
```
### 🔹 B. Object Scope

- Each **object** of a class has its **own copy** of **non-static** members  
- When you access members using an object, you're working in **object scope**

```cpp
Student s1, s2;
s1.setRollNo(1001);  // modifies s1's rollNo
s2.setRollNo(1002);  // modifies s2's rollNo
```
> 🔍 Even though `rollNo` is defined **once in the class**, each object holds a **separate instance** of it.

---

### 🔹 C. Function Scope (within Member Functions)

- Variables declared **inside a member function** are **local to that function**
- They exist **only during the function's execution**

```cpp
void display() {
    int x = 10;  // Function scope
}
```
> 🔒 Local variables declared inside functions **shadow** class variables if they share the same name.

---

### 🔹 D. Global Scope (Rare in Class-Based Design)

- Declared **outside all classes and functions**  
- Accessible from **any part** of the program, unless **shadowed** by a local variable

---

## 📦 3. Example: Scopes in Action

```cpp
#include <iostream>
using namespace std;

class Box {
private:
    int length;  // Class scope

public:
    void setLength(int length) {      // Function parameter (local scope)
        this->length = length;        // 'this->' accesses class member
    }

    void display() {
        int length = 5;               // Local variable (function scope)
        cout << "Local length: " << length << endl;
        cout << "Class length: " << this->length << endl;
    }
};
```
## 🧠 Output:

```cpp
Local length: 5
Class length: 20
```
> 🧠 The `this->` keyword is used to **distinguish class member variables** from function parameters  
or local variables with the **same name**.

---

## 🔄 4. Static Members and Scope

- Declared with the `static` keyword  
- Belong to the **class itself**, not to individual objects  
- Shared across **all instances** of the class  
- Have **class-level scope**, not object-level

```cpp
class Test {
    static int count;  // Shared class-level variable
};
```
> 🧠 The `this->` keyword is used to **distinguish class member variables** from function parameters  
or local variables with the **same name**.

---

## 🔄 4. Static Members and Scope

- Declared with the `static` keyword  
- Belong to the **class itself**, not to individual objects  
- Shared across **all instances** of the class  
- Have **class-level scope**, not object-level

```cpp
class Test {
    static int count;  // Shared class-level variable
};
```
## 🔐 5. Scope and Access Specifiers

| Scope           | Controlled by Access Specifier?                        |
|------------------|--------------------------------------------------------|
| **Class scope**   | ✅ Yes — defines visibility within and outside class  |
| **Object scope**  | ✅ Indirectly — via access rules defined in class     |
| **Function scope**| ❌ No — applies only within the function body         |
| **Global scope**  | ❌ Not related to class access control                |

> 🔍 **Access specifiers** control **visibility** across scopes, but not the **existence** of scope itself.
