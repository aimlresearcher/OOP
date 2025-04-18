# 🎓 Introduction to Classes and Objects  
*(Data Members and Member Functions)*

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand what **classes and objects** represent in OOP  
- Define **data members** and **member functions**  
- Differentiate between **instance** and **static** members  
- Recognize how **data and behavior** are encapsulated within a class

---

## 📌 1. What Is a Class?

A **class** is a **user-defined data type** that acts as a **blueprint** for creating objects.

It encapsulates:

- **Data Members** (attributes or fields)  
- **Member Functions** (methods or behaviors)  

> 🔍 A class does **not consume memory** until objects are **instantiated** from it.

---

## 🧱 2. Structure of a Class

```cpp
class ClassName {
    // Access specifier
    dataType dataMember1;
    dataType dataMember2;

public:
    returnType memberFunction1();
    returnType memberFunction2();
};
```
## 💡 Example: Basic Class Definition

```cpp
class Student {
    string name;
    int rollNo;

public:
    void setData(string n, int r);
    void displayData();
};
```
## 🧠 3. What Is an Object?

An **object** is a specific **instance of a class**.  
It contains its **own copy of data members** and can **invoke the class's member functions**.

---

### 🔹 Object Declaration:

```cpp
Student s1;
```
## 📌 Accessing Members

Use the **dot operator (`.`)** to access member functions and data of an object.

```cpp
s1.setData("Ali", 101);
s1.displayData();
```
## 🔍 4. Data Members (Variables Inside a Class)

### 🟢 Instance Data Members
- **Unique** for each object  
- Each object gets its **own copy**  
- Stored **separately in memory** for each object

---

### 🔵 Static Data Members
- **Shared** among all objects of the class  
- **Single copy** exists regardless of how many objects are created  
- Declared with the `static` keyword

```cpp
class Counter {
    static int count;  // Shared across all instances
};
```
## 🔧 5. Member Functions (Methods Inside a Class)

**Member functions** define the **behaviors or actions** an object can perform.

---

### 🔹 There are two types of definitions:

### ➤ Inside Class Definition (Inline by Default)

Functions defined inside the class body are treated as **inline** by default.

```cpp
class A {
public:
    void show() {
        cout << "Hello";
    }
};
```
### ➤ Outside Class Definition

Functions can also be defined **outside the class** using the **scope resolution operator `::`**.

```cpp
class A {
public:
    void show();  // Function declaration
};

void A::show() {  // Function definition
    cout << "Hello";
}
```
## 🔒 6. Access Specifiers

| Specifier   | Meaning                                                       |
|-------------|---------------------------------------------------------------|
| `private`   | Accessible **only within the class** (default for classes)    |
| `public`    | Accessible **from outside the class**                         |
| `protected` | Accessible in **derived classes** (covered later with inheritance) |

---

## 📌 7. Example: Full Class with Members

```cpp
class Student {
private:
    string name;
    int rollNo;

public:
    void setData(string n, int r) {
        name = n;
        rollNo = r;
    }

    void displayData() {
        cout << "Name: " << name << ", Roll No: " << rollNo << endl;
    }
};

int main() {
    Student s1;
    s1.setData("Hassan", 1001);
    s1.displayData();
    return 0;
}
```
## 📚 8. Key Benefits of Using Classes

- 🔒 **Encapsulation**: Keeps data safe and methods together in a single unit  
- 🧱 **Modularity**: Breaks code into **meaningful, manageable components**  
- 🔁 **Reusability**: Class definitions can be **reused** across multiple programs  
- 🔧 **Maintainability**: Makes it **easier to manage and update** large-scale software
