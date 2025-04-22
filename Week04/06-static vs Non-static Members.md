# 🎓 Comparison of Static and Non-Static Members in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Distinguish between **static** and **non-static** data members  
- Understand how static and non-static **member functions differ**  
- Explain **memory allocation** and **accessibility** rules for both types  
- Apply the correct type of member depending on the **design need**

---

## 📌 1. Overview

In C++, class members (variables or functions) can be either:

- **Static**: Shared across all objects of a class  
- **Non-static**: Unique for each object (instance-specific)

---

## 📋 2. Comparison Table

| Feature                | Static Members                                    | Non-Static Members                                 |
|------------------------|---------------------------------------------------|----------------------------------------------------|
| **Memory Allocation**   | Allocated once for the **entire class**           | Allocated **separately for each object**           |
| **Belongs To**          | Class itself                                     | Specific object/instance                           |
| **Accessed Using**      | `ClassName::member` or `object.member`           | Only through `object.member`                       |
| **Default Initialization** | Defined **outside the class**                 | Via constructor or assignment                      |
| **Storage Duration**    | Entire program (like a global variable)          | Lives as long as the object exists                 |
| **Scope**               | Class-wide                                       | Object-level                                       |
| **Function Restrictions** | Can access **only static** members              | Can access **both static and non-static** members  |
| **Use Case**            | Counters, shared config, class-wide settings     | Instance-specific data or behavior                 |
| **`this` pointer**      | ❌ Not available                                  | ✅ Available                                        |

---

## 🔧 3. Static Data Members: Example

```cpp
class Student {
    static int totalStudents;

public:
    Student() {
        totalStudents++;
    }

    static int getTotal() {
        return totalStudents;
    }
};

// Definition of static member
int Student::totalStudents = 0;
```
## ✅ Access

You can access a **static member function** using the class name:

```cpp
Student::getTotal();
```
## 🔧 4. Non-Static Data Members: Example

```cpp
class Student {
    string name;  // Non-static member

public:
    void setName(string n) { name = n; }
    void display() { cout << "Name: " << name; }
};
```
## ✅ Access

```cpp
Student s1, s2;
s1.setName("Ali");
s2.setName("Sara");
```
> 🧠 Each object has its **own copy** of the non-static member `name`.

This means changes made through one object **do not affect** the `name` in another object.

## 🔁 5. Static vs Non-Static Functions

| Feature                  | Static Function             | Non-Static Function           |
|--------------------------|-----------------------------|-------------------------------|
| Requires object to call? | ❌ No                        | ✅ Yes                         |
| Can access non-static?   | ❌ No                        | ✅ Yes                         |
| Can access static?       | ✅ Yes                       | ✅ Yes                         |
| Has `this` pointer?      | ❌ No                        | ✅ Yes                         |

---

## 💡 6. When to Use What?

### ✅ Use **Static Members** When:
- You need a **shared counter**, setting, or flag  
- You want a **class-wide property** that’s the same for all objects  
- You need to track or manage **global state** across instances

### ✅ Use **Non-Static Members** When:
- Each object needs its **own copy of data**  
- The **behavior or data is unique** to each instance  
- You want to maintain **encapsulation per object**
