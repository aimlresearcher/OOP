# 🎓 Lecture 28: Importance of Destructor and Constructor Overloading in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the **role of a destructor** in C++ classes  
- Recognize when **destructors are automatically called**  
- Define and apply **constructor overloading**  
- Appreciate how both features support **clean, safe**, and **flexible OOP design**

---

## 📌 1. What Is a Destructor?

A **destructor** is a **special member function** automatically called when:

- An object **goes out of scope**, or  
- It is **explicitly deleted**

---

### 🔹 Syntax:

```cpp
~ClassName();  // Tilde (~) before class name
```
### 🔸 Characteristics of Destructors

- ❌ **No return type** (not even `void`)
- ❌ **No parameters**
- ❌ **Cannot be overloaded** — only **one destructor per class** is allowed

---

### ✅ Importance of Destructors

| Reason                  | Description                                                 |
|-------------------------|-------------------------------------------------------------|
| **Memory management**   | Releases dynamically allocated memory using `delete`        |
| **File/resource management** | Closes open files, network connections, etc.         |
| **Automatic cleanup**   | Automatically called when object goes out of scope          |
| **Avoid memory leaks**  | Ensures all unused memory is properly reclaimed             |
| **Completes object lifecycle** | Last function called before object is destroyed     |

---

### 💡 Example:

```cpp
class Sample {
    int* data;

public:
    Sample() {
        data = new int[10];  // Allocating memory
    }

    ~Sample() {
        delete[] data;       // Releasing memory
        cout << "Destructor called" << endl;
    }
};

int main() {
    Sample obj;  // Constructor and destructor automatically handled
}
```
> 🔍 Without the destructor, the dynamically allocated memory (`new int[10]`) is **not released**,  
> leading to a **memory leak** — the memory stays allocated even after the object is destroyed.
## 🔁 2. Constructor Overloading

**Constructor overloading** allows defining **multiple constructors** in a class,  
each with a **different parameter list**, to create objects in various ways.

---

### 🔹 Why Overload Constructors?

| Use Case                      | Benefit                              |
|-------------------------------|--------------------------------------|
| Create object in multiple ways | ✅ Flexibility in object creation     |
| Default + custom initialization | ✅ Versatility for different needs  |
| Support optional data         | ✅ Cleaner and more readable code     |
| Enables polymorphic object creation | ✅ Supports OOP design patterns |

---

### 🔧 Example: Constructor Overloading

```cpp
class Rectangle {
    int length, width;

public:
    Rectangle() {
        length = width = 0;
    }

    Rectangle(int l) {
        length = width = l;
    }

    Rectangle(int l, int w) {
        length = l;
        width = w;
    }

    void display() {
        cout << "Area: " << length * width << endl;
    }
};
```
### ✅ Usage:

```cpp
Rectangle r1;        // Default → Area: 0
Rectangle r2(5);     // Square → Area: 25
Rectangle r3(4, 6);  // Rectangle → Area: 24
```
## 🔄 3. Constructor Overloading vs Default Arguments

| Feature               | Constructor Overloading               | Default Arguments                    |
|-----------------------|----------------------------------------|---------------------------------------|
| **Multiple definitions** | ✅ Yes — multiple constructor versions | ❌ No — only one constructor allowed   |
| **Syntax flexibility**   | ✅ Better for complex logic             | ✅ Suitable for simple cases           |
| **Readability**          | Can become lengthy with many versions | Cleaner when fewer options are needed |

> 🧠 Use **constructor overloading** when object creation requires **different logic**,  
> and **default arguments** when the difference is only in optional parameter values.

---

## 📚 Summary Table: Destructor vs Constructor Overloading

| Feature                 | **Destructor**                              | **Constructor Overloading**              |
|-------------------------|----------------------------------------------|-------------------------------------------|
| **Purpose**             | Cleanup before object deletion               | Initialize objects in multiple ways       |
| **Return type**         | ❌ None                                       | ❌ None                                    |
| **Parameters**          | ❌ Not allowed                                | ✅ Allowed and can vary                   |
| **Overloading**         | ❌ Only one allowed                           | ✅ Many allowed                            |
| **Called automatically**| ✅ When object is destroyed                   | ✅ When object is created                  |

> 🔁 Both play vital roles in the **object lifecycle**, ensuring safe and flexible object-oriented design.
