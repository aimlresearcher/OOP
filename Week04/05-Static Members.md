# 🎓 Static Variables and Functions in Procedural and Object-Oriented Programming

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the concept of `static` in both **procedural** and **object-oriented** paradigms  
- Describe how **static variables** behave inside functions and globally  
- Define and use **static data members and member functions** in classes  
- Recognize differences in **lifetime**, **scope**, and **sharing** of static elements

---

## 🧾 Part A: Static in Procedural Programming

### 📌 1. Static Local Variables

A **static local variable** inside a function retains its value **between function calls**.

---

### 🔹 Syntax:

```cpp
void counter() {
    static int count = 0;  // Initialized only once
    count++;
    cout << "Count: " << count << endl;
}
```
### 🔄 Behavior of Static Local Variables:

- ✅ Memory is **allocated only once**, even if the function is called multiple times  
- ✅ The variable **persists** even after the function exits  
- ✅ It is **local to the function**, but its **lifetime is extended** to the entire program run

---

## 🧠 2. Static Global Variables

- Declared at **file scope** (outside any function)  
- Have **internal linkage**, meaning they are **visible only within the same file**  
- Commonly used in **multi-file programs** to **hide implementation details**

---

### 🔹 Example:

```cpp
static int fileLevelVar = 10;
```
## ⚙️ 3. Static Functions (Procedural)

- A function declared with `static` at **global scope** is **visible only within the file** it's declared in  
- Useful for **encapsulation** in multi-file (modular) projects  
- Prevents **name collisions** across different source files

---

### 🔹 Example:

```cpp
static void helper() {
    // Only visible in this file
}
```
## 🧾 Part B: Static Members in Object-Oriented Programming (OOP)

### 📦 4. Static Data Members (Class-Level Variables)

- Declared using the `static` keyword **inside the class**  
- Belong to the **class itself**, not to individual objects  
- **Shared** across all instances of the class  
- Only **one copy** exists in memory

---

### 🔹 Declaration:

```cpp
class Test {
    static int count;  // Declaration inside class
};
```
### 🔸 Definition (Outside the Class)

After declaring a static data member inside the class, you must define it **outside the class** (usually in a `.cpp` file).

```cpp
int Test::count = 0;  // Definition and optional initialization
```
## 💡 Characteristics of Static Data Members

- Belong to the **class**, not to any specific object  
- ✅ Accessible using the **class name**: `Test::count`  
- ⚠️ Can also be accessed via objects, but it's **not recommended** (use class name for clarity)

---

## 🔧 5. Static Member Functions

- Declared with the `static` keyword  
- Can access **only static data members**  
- ❌ Cannot access non-static members  
- ❌ Cannot use the `this` pointer (they don’t belong to any object)

---

### 🔹 Example:

```cpp
class Counter {
private:
    static int count;

public:
    static void increment() {
        count++;
        cout << "Count: " << count << endl;
    }
};

// Definition of static data member
int Counter::count = 0;
```
### 🔑 Usage

```cpp
Counter::increment();  // No object needed!
```
## 🔄 6. Comparison: Static in Procedural vs OOP

| Feature             | Procedural                          | OOP (Class-Based)                                |
|---------------------|--------------------------------------|--------------------------------------------------|
| **Variable Lifetime** | Persists across function calls       | Shared among all class objects                   |
| **Access Scope**     | Limited to function or file          | Class-wide scope (accessible via class name)     |
| **Data Sharing**     | Not shared unless declared global    | Automatically shared across all instances        |
| **Function Access**  | Hidden in file (`static` function)   | Bound to class, not to object (no `this` pointer) |

> 📘 Static has different roles in procedural and object-oriented paradigms — in OOP, it promotes **shared state and behavior** at the class level.
