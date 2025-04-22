# 🎓 Lecture 19: Use of Access Specifiers in C++ (`public`, `private`)

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the purpose of **access specifiers** in C++  
- Differentiate between **public** and **private** members of a class  
- Recognize how access specifiers **enforce encapsulation**  
- Predict **member visibility and access** in different contexts

---

## 📌 1. What Are Access Specifiers?

Access specifiers define the **accessibility or visibility** of data members and member functions of a class.

They control:

- Who can **access** class members  
- How **encapsulated and secure** the class is  

---

## 🧱 2. Types of Access Specifiers

| Specifier   | Accessible Within Class | Accessible Outside Class | Accessible in Derived Class |
|-------------|--------------------------|----------------------------|------------------------------|
| `private`   | ✅ Yes                   | ❌ No                      | ❌ No                         |
| `public`    | ✅ Yes                   | ✅ Yes                     | ✅ Yes                        |
| `protected` | ✅ Yes                   | ❌ No                      | ✅ Yes                        |

> 📌 For this lecture, we’ll focus on `private` and `public`, which are **commonly used** in basic class design.

---

## 🔐 3. `private` Access Specifier

- The **default access** level in a class  
- Members are **hidden from outside** the class  
- Promotes **data hiding** and **encapsulation**

### 🔸 Example:

```cpp
class Student {
private:
    int rollNo;
    string name;

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
    Student s;
    s.setData("Ali", 101);  // ✅ OK
    // s.rollNo = 101;      ❌ Error: rollNo is private
}
```
## 🔓 4. `public` Access Specifier

- Members declared as `public` are **accessible from anywhere** — both **inside** and **outside** the class  
- Commonly used for **functions** that provide an interface to the class

### 🔸 Example:

```cpp
class Calculator {
public:
    int add(int a, int b) {
        return a + b;
    }
};

int main() {
    Calculator c;
    cout << c.add(5, 3);  // ✅ Accessible
}
```
## ⚠️ 5. Why Not Make Everything Public?

While making everything `public` might seem convenient, it has serious drawbacks:

- ❌ **Breaks encapsulation**  
- ❌ Makes data **vulnerable to misuse or accidental change**  
- ❌ Increases **tight coupling**, reducing code flexibility  
- ❌ Leads to **poor modularity** and less maintainable code  

> 🔐 OOP encourages **information hiding** — internal details should be protected and only the necessary parts exposed.

---

## 🧠 6. When to Use What?

| Situation                                   | Specifier to Use |
|--------------------------------------------|------------------|
| Internal data members (e.g., `rollNo`, `GPA`) | `private`         |
| Helper functions that should not be exposed | `private`         |
| User-facing methods (`setData`, `display`) | `public`          |
| Getters and Setters                        | `public`          |

---

## 🔒 7. Encapsulation in Action

**Encapsulation** means:

- Keeping **data private**
- Allowing **controlled access** through `public` methods

### ✅ Benefits:
- Better **data integrity**
- Easier **debugging and maintenance**
- Cleaner and **well-defined APIs**
