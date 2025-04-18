# 🎓 Friend Functions in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the concept and **syntax of friend functions**  
- Recognize **when** a friend function is appropriate  
- Access **private/protected** members of a class using a friend  
- Evaluate the **trade-offs** of using `friend` in OOP design

---

## 📌 1. What Is a Friend Function?

A **friend function** is a **non-member** function that is granted access to the **private and protected members** of a class.

> ✅ It is **not a member**, but behaves as though it is when accessing class internals.

---

## 🔐 2. Why Use a Friend Function?

- To allow an **external function** to access **private data**  
- Useful for **operator overloading** or **non-member utility functions**  
- Helps in **cooperative access** between two or more tightly related classes

---

## 🧱 3. Syntax of a Friend Function

- Declared **inside the class** using the keyword `friend`  
- Defined **outside** the class like a normal function

```cpp
class Box {
private:
    int width;

public:
    friend void printWidth(Box b);  // Friend declaration
};
```
```cpp
void printWidth(Box b) {
    cout << "Width: " << b.width;  // Accessing private member
}
```
## 💡 4. Example: Friend Function in Action

```cpp
class Student {
private:
    string name;
    int marks;

public:
    Student(string n, int m) : name(n), marks(m) {}

    friend void display(const Student& s);  // Friend declaration
};

void display(const Student& s) {
    cout << "Name: " << s.name << ", Marks: " << s.marks << endl;
}
```
> ⚠️ `display()` is **not a member** of the `Student` class,  
> but it can still **access private data** (`name` and `marks`) because it’s declared as a **friend**.
## 🧠 5. Key Characteristics

| Feature                        | Friend Function                     |
|-------------------------------|-------------------------------------|
| Is it a member of the class?  | ❌ No                                |
| Can access private data?      | ✅ Yes                               |
| Uses `this` pointer?          | ❌ No (not part of the object)       |
| Called using object?          | ✅ Yes, object passed as argument    |
| Defined inside class?         | ❌ Only declared inside the class    |

---

## 🔄 6. Friend Function with Multiple Classes

Friend functions can be granted access to **multiple classes** if declared as a friend in **each class**.

```cpp
class A;
class B;

class A {
    int valueA = 5;
    friend void showBoth(A, B);
};

class B {
    int valueB = 10;
    friend void showBoth(A, B);
};

void showBoth(A a, B b) {
    cout << "A: " << a.valueA << ", B: " << b.valueB;
}
```
## 🔎 7. Pros and Cons of Friend Functions

### ✅ Advantages:
- Allows **tightly coupled** classes or functions to share internal data  
- Can **simplify code**, especially in **operator overloading**  
- Useful when **accessor functions** would be awkward or verbose  

---

### ❌ Disadvantages:
- **Breaks encapsulation** by exposing private data to non-members  
- **Tightens coupling**, making code harder to maintain and refactor  
- **Violates strict OOP principles** of data hiding and modularity  

> ⚠️ **Use friend functions only when necessary** — they are powerful but should be used **with caution**.
