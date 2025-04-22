# 🎓 Object-Oriented Concepts in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Define and explain the **core concepts** of object-oriented programming (OOP)  
- Understand the **relationships** between classes, objects, and abstraction mechanisms  
- Describe how each concept contributes to **clean**, **reusable**, and **scalable** software

---

## 📌 1. What Are Object-Oriented Concepts?

Object-Oriented Concepts form the **foundation of OOP** and are essential for designing **modular**, **reusable**, and **real-world-representative** software systems.

| Concept          | Description                                           |
|------------------|-------------------------------------------------------|
| **Class**         | Blueprint for creating objects                       |
| **Object**        | Instance of a class                                  |
| **Encapsulation** | Bundling data and methods; ensures **data hiding**   |
| **Abstraction**   | Hiding internal complexity; exposing only essentials |
| **Inheritance**   | Deriving new classes from existing ones              |
| **Polymorphism**  | One interface, many forms                            |
| **Message Passing** | Communication between objects via methods         |
| **Dynamic Binding** | Runtime decision of which method to invoke         |

---

## 🧱 2. Class and Object

### 🔹 Class

A **user-defined type** that groups together **data (attributes)** and **functions (methods)**.

```cpp
class Student {
public:
    string name;
    void display() {
        cout << "Name: " << name;
    }
};
```
### 🔹 Object

An **object** is an **instance** of a class. It has its own copy of the class’s attributes and can invoke its methods.

```cpp
Student s1;
s1.name = "Ali";
s1.display();
```
## 🔒 3. Encapsulation

- Combines **data and methods** into one unit: the **class**  
- Keeps data **safe from outside interference**  
- Access controlled using **access specifiers**: `private`, `public`, `protected`

> 🔐 *"Data hiding is a key part of encapsulation."*

---

## 🎭 4. Abstraction

- Exposes only the **essential features** of an object  
- Hides the **internal implementation details**  
- Simplifies interaction with complex systems

> 🔸 *Example:* You can drive a car without knowing how the engine works.

### In C++:
- Achieved via **classes**  
- Enhanced further with **abstract classes** and **interfaces**

---

## 🧬 5. Inheritance

- Allows one class (**child/derived**) to **inherit** the attributes and behaviors of another (**parent/base**)  
- Promotes **code reuse**, and establishes a **hierarchical relationship**

```cpp
class Animal {
public:
    void eat();
};

class Dog : public Animal {
public:
    void bark();
};
```
## 🔄 6. Polymorphism

**Polymorphism** allows functions or methods to **behave differently** based on **input** or **context**.

---

### 🔹 Types of Polymorphism:

1. **Compile-time (Static)**  
   - Achieved through **function overloading** and **operator overloading**

2. **Run-time (Dynamic)**  
   - Achieved using **virtual functions** and **inheritance**

---

### 💡 Example: Function Overloading (Compile-time Polymorphism)

```cpp
void draw(int shape);
void draw(double shape);  // Function overloading
```
## 📬 7. Message Passing

- Objects **communicate with each other** by calling each other’s **methods**
- Promotes a **modular**, object-driven approach to software design

### 💡 Example:

```cpp
student1.sendMessage("Hello!");
```
## 🔁 8. Dynamic Binding (Late Binding)

- A **method call is resolved at runtime**, not at compile-time  
- Enables **dynamic polymorphism** through **virtual functions**

---

### 💡 Example:

```cpp
class Animal {
public:
    virtual void speak();  // Virtual function
};
```
## 🔍 9. Summary Table

| Concept           | Key Purpose                           |
|-------------------|----------------------------------------|
| **Class**          | Defines structure                     |
| **Object**         | Runtime instance                      |
| **Encapsulation**  | Data protection and modularity        |
| **Abstraction**    | Simplifies complexity                 |
| **Inheritance**    | Code reuse and hierarchy              |
| **Polymorphism**   | Flexibility and extensibility         |
| **Message Passing**| Communication between objects         |
| **Dynamic Binding**| Run-time decision making              |
