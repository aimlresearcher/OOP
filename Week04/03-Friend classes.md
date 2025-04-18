# 🎓 Lecture 25: Friend Classes in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Define what a **friend class** is and how it works  
- Understand how friend classes access **private and protected** members  
- Recognize **appropriate use cases** for friend classes  
- Evaluate the **impact on encapsulation and design**

---

## 📌 1. What Is a Friend Class?

A **friend class** is a class that is **granted access** to the **private and protected members** of another class.

> ✅ It’s like saying: “This class is **trusted enough** to see and modify my internal data.”

---

## 🔐 Why Do We Use Friend Classes?

- To allow **tight cooperation** between two **related classes**  
- Useful when classes need to **access each other’s internals frequently**  
- Helps implement designs like:
  - **Two-way relationships**
  - **Helper/utility classes**
  - **Operator overloading** (especially binary operators)

---

## 🧱 2. Syntax: Declaring a Friend Class

```cpp
class B;  // Forward declaration

class A {
private:
    int secretA = 100;

public:
    friend class B;  // B can access private members of A
};

class B {
public:
    void showA(A a) {
        cout << "A's secret: " << a.secretA << endl;  // Allowed
    }
};
```
> ⚠️ **Note:** Friendship is **not mutual** by default.  
If `A` is a friend of `B`, it **does not** mean `B` is also a friend of `A` —  
you must **explicitly declare friendship in both classes** if two-way access is needed.
## 🧠 3. Key Characteristics of Friend Classes

| Feature                                | Friend Class                       |
|----------------------------------------|------------------------------------|
| Access to private/protected members?   | ✅ Yes                              |
| Automatically grants mutual friendship?| ❌ No (must be explicitly declared) |
| Breaks encapsulation?                  | ✅ Potentially                      |
| Requires explicit declaration?         | ✅ Yes                              |
| Member-wise control?                   | ❌ No — friendship applies to entire class |

---

## 💡 4. Example: Two Classes Cooperating

```cpp
class Engine;

class Car {
private:
    int speed = 180;
    friend class Engine;  // Engine can access Car's private data
};

class Engine {
public:
    void tune(Car& c) {
        c.speed += 20;  // Accessing private member of Car
        cout << "Tuned speed: " << c.speed << endl;
    }
};
```
## 🔄 5. Friend Function vs Friend Class

| Feature              | Friend Function                     | Friend Class                          |
|----------------------|--------------------------------------|----------------------------------------|
| **Granularity**       | Grants access to **one function**    | Grants access to **entire class**      |
| **Access Scope**      | Access to **one class**              | Access to **all members** of another class |
| **Relationship**      | One-way                             | One-way                                |
| **Encapsulation Impact** | Less severe                     | More invasive                          |

---

## ⚠️ 6. Design Considerations

### ✅ Use Friend Classes When:
- Two classes are **logically connected** (e.g., `Engine` and `Car`)  
- You want to **avoid multiple getters/setters**  
- A **helper class** needs **direct access** to simplify implementation

---

### ❌ Avoid Friend Classes If:
- You're compromising **data privacy** without a valid reason  
- **Better alternatives** exist using encapsulation or interfaces  
- The classes aren't tightly related in terms of functionality

> 🔒 **OOP encourages limited sharing** — friendship is a **controlled violation** of encapsulation and should be used **sparingly**.
