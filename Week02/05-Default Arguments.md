# 🎓 Default Arguments in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand what **default arguments** are and how to use them  
- Apply default arguments in **function definitions** and **declarations**  
- Recognize the **rules and limitations** of default arguments  
- Differentiate between **default arguments** and **function overloading**

---

## 📌 1. What are Default Arguments?

**Default arguments** allow you to **assign default values** to function parameters,  
so the function can be called with **fewer arguments**.

---

## 🧠 2. Why Use Default Arguments?

- ✅ Reduce **redundancy**  
- ✅ Increase **flexibility**  
- ✅ Make function calls **simpler**  
- ✅ Avoid writing **multiple overloaded** versions of the same function
## 🧱 3. Syntax of Default Arguments

```cpp
return_type function_name(param1 = default1, param2 = default2) {
    // body
}
```
## 💡 4. Basic Example

```cpp
#include <iostream>
using namespace std;

void greet(string name = "Student") {
    cout << "Hello, " << name << "!" << endl;
}

int main() {
    greet();           // Output: Hello, Student!
    greet("Umer");     // Output: Hello, Umer!
}
```
## 📦 5. Example with Multiple Defaults

```cpp
int power(int base, int exponent = 2) {
    int result = 1;
    for (int i = 0; i < exponent; i++) {
        result *= base;
    }
    return result;
}

int main() {
    cout << power(5) << endl;     // 25 (5^2)
    cout << power(5, 3) << endl;  // 125 (5^3)
}
```
## 📌 6. Important Rules

✅ **Default arguments must be trailing** (from **right to left**) in the parameter list.

```cpp
// ✅ Valid
void func(int a, int b = 10, int c = 20);

// ❌ Invalid: default in the middle
void func(int a = 10, int b, int c = 20);
```
## ✅ Can be Defined In:

- **Function declaration** (✅ Preferred)
- **Function definition** (⚠️ Only in one place!)

---

## 🔄 7. Default Arguments vs Function Overloading

| Feature            | Default Arguments                            | Function Overloading                                |
|--------------------|-----------------------------------------------|------------------------------------------------------|
| **Purpose**         | Avoid writing multiple versions               | Provide multiple versions for different use cases   |
| **Syntax**          | Single function with default parameter(s)     | Multiple functions with different parameters        |
| **Flexibility**     | Less flexible                                 | More flexible                                       |
| **Readability**     | More concise                                  | Can be more explicit                                |

---

## 💡 Example Comparison

### ✅ Using Default Arguments:

```cpp
void display(string msg = "Hello", int times = 1) {
    for (int i = 0; i < times; i++) 
        cout << msg << endl;
}
```
### ✅ Using Overloading:

```cpp
void display() {
    cout << "Hello" << endl;
}

void display(string msg) {
    cout << msg << endl;
}

void display(string msg, int times) {
    for (int i = 0; i < times; i++) 
        cout << msg << endl;
}
## 🚫 8. Common Mistakes

| Mistake                                      | Issue                                               |
|----------------------------------------------|-----------------------------------------------------|
| Providing defaults in both declaration and definition | ❌ Compiler error — use default in only one place   |
| Placing default arguments in the middle       | ❌ Only **trailing** parameters can have defaults   |
| Overusing defaults with complex logic         | ⚠️ Can make functions **harder to read/debug**      |
