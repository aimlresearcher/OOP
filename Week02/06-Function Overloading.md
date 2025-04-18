# 🎓 Function Overloading in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand what **function overloading** is  
- Write **multiple versions** of the same function with different parameters  
- Differentiate **overloading** from **default arguments**  
- Avoid common **overloading pitfalls**

---

## 📌 1. What is Function Overloading?

**Function Overloading** means having **multiple functions** with the **same name**, but different:

- ✅ Number of parameters  
- ✅ Types of parameters  
- ✅ Order of parameters  

🧠 It allows you to use the **same function name** for different tasks, based on the **signature**.

---

## 🧠 2. Why Use Function Overloading?

- ✅ Improves **code readability**  
- ✅ Makes functions more **intuitive and usable**  
- ✅ Supports **polymorphism** (important in **OOP**)  
- ✅ Allows for **flexible API design**
## 🧱 3. Syntax of Function Overloading

Each overloaded function must have a **unique parameter list** (number, type, or order).

```cpp
return_type function_name(parameter_list) {
    // body
}
```
> ✅ You can define **multiple versions** of `function_name()` with **different parameter lists** (signature).
## 💡 4. Example: Basic Overloading

```cpp
#include <iostream>
using namespace std;

void print(int i) {
    cout << "Integer: " << i << endl;
}

void print(double d) {
    cout << "Double: " << d << endl;
}

void print(string s) {
    cout << "String: " << s << endl;
}

int main() {
    print(10);         // Calls print(int)
    print(3.14);       // Calls print(double)
    print("Hello");    // Calls print(string)
}
```
> ✅ All three `print()` functions are **valid** because they have **different parameter types**, enabling **function overloading**.

## 🔁 5. Example: Overloading with Parameter Count

```cpp
int add(int a, int b) {
    return a + b;
}

int add(int a, int b, int c) {
    return a + b + c;
}
```
## 🔄 6. Example: Overloading with Parameter Order

```cpp
void display(int a, char b) {
    cout << "int-char version" << endl;
}

void display(char a, int b) {
    cout << "char-int version" << endl;
}
```
> ⚠️ **Parameter types and/or order must differ** — overloading based on **return type alone is not allowed** in C++.
## 🚫 7. Invalid Overloading

❌ **Overloading by return type only is not allowed** in C++.

```cpp
int get();
double get();  // ❌ Error: same name and parameters
```
## 📚 8. Function Overloading vs Default Arguments

| Feature                | Function Overloading                            | Default Arguments                         |
|------------------------|--------------------------------------------------|-------------------------------------------|
| **Multiple definitions** | ✅ Yes                                         | ❌ No (only one definition)               |
| **Based on parameters** | ✅ Type, number, or order                        | ✅ Only trailing parameters                |
| **Compiler Decision**   | Based on **best match**                         | Based on **number of arguments provided** |
| **Flexibility**         | ✅ More flexible                                | ✅ Simpler, but limited                   |
