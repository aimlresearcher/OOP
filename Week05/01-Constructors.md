# 🎓 Constructors and Object Instantiation in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the **role and purpose** of constructors in OOP  
- Describe the process of **object instantiation**  
- Identify **different types** of constructors  
- Explain how constructors support **encapsulation** and **initialization**

---

## 📌 1. What Is a Constructor?

A **constructor** is a **special member function** of a class that:

- Has the **same name** as the class  
- Has **no return type** (not even `void`)  
- Is **automatically invoked** when an object is created

> 🔧 “A constructor prepares the object for use by **initializing its data members**.”

---

## 🧱 2. Object Instantiation

**Instantiating an object** means:

- Creating an **actual object in memory** from a class blueprint  
- This **triggers** the **constructor call**

---

### 🔸 Example:

```cpp
class Student {
public:
    Student() {
        cout << "Constructor called!" << endl;
    }
};

int main() {
    Student s1;  // Object instantiation → constructor automatically called
}
```
## 🧠 3. Characteristics of Constructors

| Feature                 | Description                                 |
|-------------------------|---------------------------------------------|
| **Name**                | Must be the **same as the class name**      |
| **Return type**         | ❌ **None** — not even `void`               |
| **Can be overloaded**   | ✅ Yes — multiple constructors allowed       |
| **Automatically invoked**| ✅ Called when an object is created         |
| **Can take arguments**  | ✅ Yes — for custom initialization          |
| **Can be default or user-defined** | ✅ Both are allowed              |

---

## 📦 4. Types of Constructors

### 🔹 A. Default Constructor

- Takes **no parameters**  
- **Automatically provided** by the compiler if **no constructor is defined**  
- You can also define your own default constructor

```cpp
class A {
public:
    A() {
        cout << "Default constructor" << endl;
    }
};
```
### 🔹 B. Parameterized Constructor

- Takes **arguments** to **initialize data members**  
- Useful for **customized object initialization**

```cpp
class Student {
private:
    string name;
    int rollNo;

public:
    Student(string n, int r) {
        name = n;
        rollNo = r;
    }
};
```
### 🔹 C. Constructor Overloading

- Allows you to define **multiple constructors** with **different parameter lists**
- Supports **flexibility** in object creation based on available data

```cpp
class Box {
public:
    Box() {
        cout << "Default" << endl;
    }

    Box(int l) {
        cout << "Length: " << l << endl;
    }

    Box(int l, int b) {
        cout << "Area: " << l * b << endl;
    }
};
```
## 🔄 5. Object Instantiation and Initialization

```cpp
class Person {
    string name;
    int age;

public:
    Person(string n, int a) {
        name = n;
        age = a;
    }

    void display() {
        cout << name << ", " << age << endl;
    }
};

int main() {
    Person p1("Ali", 20);  // Constructor is called with arguments
    p1.display();
}
```
## 🧩 6. Constructor vs Normal Function

| Feature          | Constructor                        | Normal Function                    |
|------------------|-------------------------------------|-------------------------------------|
| **Name**         | Same as class name                  | Any valid function name             |
| **Return type**  | ❌ None (no return value)            | ✅ Required (can return any type)   |
| **Automatic call**| ✅ Automatically called on object creation | ❌ Must be explicitly called    |
| **Purpose**      | Used to **initialize** an object     | Used to **perform a task or logic** |

> 🔍 Constructors ensure that an object is **ready to use immediately** after it's created.

