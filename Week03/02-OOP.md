# 🎓 Lecture 15: Object-Oriented Programming (OOP) in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the **fundamental principles** of Object-Oriented Programming (OOP)  
- Recognize the role of **objects and classes**  
- Identify the **core features** (pillars) of OOP  
- Appreciate how OOP helps design **better, scalable software**

---

## 📌 1. What is Object-Oriented Programming (OOP)?

**Object-Oriented Programming (OOP)** is a programming paradigm that structures software around **objects**, which are **instances of classes**.

> 🧠 “OOP organizes code by bundling data and behavior into a single logical unit called an **object**.”

---

## 🧠 2. Key Concepts in OOP

### 🔹 Class
A **blueprint** for creating objects. It defines:
- **Data** (attributes/variables)  
- **Methods** (functions/behavior)  

### 🔹 Object
An **instance** of a class.  
It holds actual values and can perform actions via the class’s methods.

---

## 🧱 3. Four Pillars of OOP

### 1️⃣ Encapsulation

- Binds **data** and the **functions** that manipulate it into one unit  
- Hides internal implementation details (**data hiding**)  
- Achieved using **access specifiers**: `private`, `public`, `protected`

```cpp
class Account {
private:
    double balance;

public:
    void deposit(double amount);
};
```
### 2️⃣ Abstraction

- Hides **complex implementation** and shows only the **essential features**  
- Simplifies system design by exposing only **what is necessary**

> 🚗 *Think of a car — you only need to know how to drive, not how the engine works.*

- Achieved through **classes**, **interfaces**, or **abstract classes**

---

### 3️⃣ Inheritance

- Mechanism that allows one class (**child/derived**) to **inherit** properties and behaviors from another class (**parent/base**)  
- Promotes **code reuse**, maintainability, and hierarchy representation

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
### 4️⃣ Polymorphism

- The ability of the **same function or method** to behave **differently** depending on the object or context  
- Enables flexibility and **extensibility** in software design

### 🔹 Achieved Through:

- **Function Overloading** → *Compile-time polymorphism*
- **Virtual Functions** → *Run-time polymorphism (dynamic binding)*

---

```cpp
void draw(Circle c);
void draw(Rectangle r);  // Function Overloading
```
## 🔄 4. Advantages of OOP

| Advantage         | Description                                           |
|-------------------|-------------------------------------------------------|
| **Reusability**   | Use existing classes in new ways via **inheritance**  |
| **Modularity**    | Code is broken into **logical, manageable units**     |
| **Maintainability** | Easier to **debug and modify** code                |
| **Security**      | **Encapsulation** protects sensitive data             |
| **Real-world modeling** | Closer mapping to real-world **entities**       |

---

## ⚠️ 5. Common Misunderstandings

| Misconception                        | Clarification                                               |
|--------------------------------------|-------------------------------------------------------------|
| "OOP is just about classes and objects" | OOP is about **design philosophy**, not just syntax         |
| "Inheritance is always good"         | Use **only when a logical hierarchy exists**                |
| "Polymorphism is optional"           | It’s **essential** for achieving **dynamic behavior**       |

---

## 📦 6. Real-Life Examples Modeled with OOP

| Entity         | Class        | Attributes                    | Methods                   |
|----------------|--------------|-------------------------------|---------------------------|
| **Student**     | `Student`     | `Name`, `RollNo`, `GPA`        | `Enroll()`, `Print()`      |
| **Car**         | `Car`         | `Model`, `Speed`, `FuelType`   | `Start()`, `Drive()`       |
| **Bank Account**| `Account`     | `Balance`, `AccountNumber`     | `Deposit()`, `Withdraw()`  |
