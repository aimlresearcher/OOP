# 🎓 Introduction to Single Inheritance – Public and Private Modes

## 🎯 Learning Objectives

- Understand the concept of **single inheritance**
- Differentiate between **public** and **private** inheritance
- Identify which members are inherited and how their **access specifiers change**
- Apply inheritance to represent **real-life hierarchies**

---

## 📌 1. What Is Inheritance?

**Inheritance** is an object-oriented programming concept where a new class  
(derived class) acquires the **properties and behaviors** of an existing class (base class).

### 🧠 “The derived class inherits the data and behaviors (members) of the base class.”

### 🔹 Why Use Inheritance?

- ✅ Reuse existing code
- ✅ Establish "is-a" relationships
- ✅ Promote extensibility and maintainability
- ✅ Simplify maintenance and updates

---

## 🧱 2. Single Inheritance (One-to-One)

In **single inheritance**, one **derived class** inherits from one **base class**.

```cpp
class Base {
    // base class members
};

class Derived : access_modifier Base {
    // derived class members
};
```
## 🧠 3. Real-Life Example

### 🔸 Base Class: `Person`
- `name`
- `age`
- `speak()`

### 🔸 Derived Class: `Student` inherits from `Person`
- `rollNo`
- `study()`

✅ `Student` **is a** `Person` → valid “is-a” relationship

---

## 🔓 4. Public Inheritance

```cpp
class Person {
public:
    string name;
    void speak() {
        cout << "Speaking..." << endl;
    }
};

class Student : public Person {
public:
    int rollNo;
};
```
## 🔹 Access Rules (Public Inheritance)

| Base Class Member Type | In Derived Class |
|------------------------|------------------|
| `public`               | `public`         |
| `protected`            | `protected`      |
| `private`              | ❌ Not inherited |

✅ In **public inheritance**, the **interface** of the base class remains **accessible** to users of the derived class.

---

## 🔒 5. Private Inheritance

```cpp
class Student : private Person {
public:
    int rollNo;

    void show() {
        speak();  // ✅ Allowed: inherited as private
    }
};
```
## 🔹 Access Rules (Public Inheritance)

| Base Class Member Type | In Derived Class |
|------------------------|------------------|
| `public`               | `public`         |
| `protected`            | `protected`      |
| `private`              | ❌ Not inherited |

✅ In **public inheritance**, the **interface** of the base class remains **accessible** to users of the derived class.

---

## 🔒 5. Private Inheritance

```cpp
class Student : private Person {
public:
    int rollNo;

    void show() {
        speak();  // ✅ Allowed: inherited as private
    }
};
```
## 🔹 Access Rules (Private Inheritance)

| Base Class Member Type | In Derived Class |
|------------------------|------------------|
| `public`               | `private`        |
| `protected`            | `private`        |
| `private`              | ❌ Not inherited  |

❌ Cannot access base class members through the object of the derived class  
(because they become private in private inheritance).

---

## 🔁 6. Comparison Table: Public vs Private Inheritance

| Feature                      | **Public Inheritance**     | **Private Inheritance**        |
|------------------------------|-----------------------------|---------------------------------|
| Base class `public` →        | Remains `public` in derived | Becomes `private` in derived    |
| Base class `protected` →     | Remains `protected`         | Becomes `private`               |
| Accessible from outside?     | ✅ Yes (through derived)     | ❌ No (restricted access)        |
| Use case                     | "is-a" relationships        | Implementation-only reuse       |
## 📝 Code Example: Public vs Private Inheritance

### ✅ Public Inheritance

```cpp
Student s;
s.name = "Ali";   // Accessible
s.speak();        // Accessible
```
### ❌ Private Inheritance

```cpp
Student s;
s.name = "Ali";     // ❌ Error: 'name' is private in Student
s.speak();          // ❌ Error: 'speak' is private in Student
```