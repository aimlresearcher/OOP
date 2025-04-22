# 🎓 Lecture 13: Unions in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the **concept and purpose** of unions  
- Define and **use unions** in C++  
- Compare **unions with structures**  
- Recognize appropriate **use cases** for unions

---

## 📌 1. What is a Union?

A **union** is a user-defined data type, similar to a structure, but with a key difference:

> In a **union**, all members **share the same memory location**, and only **one member can hold a value at a time**.

---

## 🧠 2. Why Use Unions?

- ✅ To **save memory**, especially in **embedded systems**  
- ✅ When you need a variable to **store different types** at different times  
- ✅ For **efficient storage** when only one of the variables is used at a time  
## 🧱 3. Syntax of a Union

```cpp
union UnionName {
    dataType member1;
    dataType member2;
    // ...
};
```
> ⚠️ Just like `struct`, **don’t forget the semicolon (`;`)** after a `union` definition — it's required by the syntax.

## 💡 4. Example: Basic Union Usage

```cpp
#include <iostream>
using namespace std;

union Data {
    int i;
    float f;
    char c;
};

int main() {
    Data d;
    
    d.i = 42;
    cout << "Integer: " << d.i << endl;

    d.f = 3.14;
    cout << "Float: " << d.f << endl;

    d.c = 'A';
    cout << "Char: " << d.c << endl;

    // Accessing previous values (not reliable)
    cout << "Integer after writing char: " << d.i << endl;

    return 0;
}
```
## 🧠 Output:

```cpp
Integer: 42
Float: 3.14
Char: A
Integer after writing char: (Garbage or changed)
```
> ⚠️ Because all members **share the same memory**, changing one member will **overwrite** the values of the others.
## 🔍 5. Memory Allocation in Unions

In a union, memory is **shared among all members**, and only the **largest member’s size** is allocated.

```cpp
union Example {
    int x;       // 4 bytes
    char y;      // 1 byte
    double z;    // 8 bytes
};
// Total size: 8 bytes (maximum of all members)
```
## 🔄 6. Union vs Structure

| Feature         | `union`                                  | `struct`                                  |
|-----------------|--------------------------------------------|--------------------------------------------|
| **Memory**       | Shared by all members                     | Separate for each member                   |
| **Access**       | Only one member holds a value at a time   | All members can hold values together       |
| **Size**         | Equal to the size of the **largest member** | Sum of the sizes of **all members**       |
| **Use Case**     | Memory-efficient alternatives             | General-purpose data grouping              |

---

## 📦 7. Practical Use Case

Unions are often used with enums or flags to manage type-safe variables in scenarios like:

- 🔧 Sensor data (e.g., temperature, pressure, status)
- 📜 Token values in parsers
- 🔀 Variant data types in low-level programming

---

## ⚠️ 8. Common Mistakes

| Mistake                                     | Explanation                                                  |
|---------------------------------------------|--------------------------------------------------------------|
| Expecting multiple members to hold values   | ❌ Only one member is **reliably valid** at a time            |
| Forgetting semicolon                        | ❌ Results in **syntax error** after union declaration         |
| Using unions for class-like behavior        | ⚠️ Unions **do not support** member functions (except constructors in C++11 and later) |
