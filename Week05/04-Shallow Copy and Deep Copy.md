# 🎓 Shallow Copy and Deep Copy in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Define and **differentiate** between shallow copy and deep copy  
- Understand how the **default copy constructor** performs a shallow copy  
- Recognize **problems caused by shallow copy** in dynamic memory management  
- Implement a **custom deep copy** using a user-defined copy constructor

---

## 📌 1. What Is Object Copying?

Object copying occurs in C++ during:

- ✅ Object initialization: `Class obj2 = obj1;`  
- ✅ Passing objects **by value**  
- ✅ Returning objects **by value**

The compiler invokes the **copy constructor** in these situations.

---

## 🧾 2. What Is a Shallow Copy?

A **shallow copy** performs a **bitwise (member-wise) copy** of the object.

### 🔹 Characteristics:

- Copies the **address**, not the content, of dynamically allocated memory  
- Both objects **point to the same memory**  
- Made by the **default compiler-generated** copy constructor

### ❌ Problem:

When one object **modifies or deletes** the shared memory,  
it **affects the other object**, leading to **dangling pointers, crashes, or undefined behavior**.

---

### 🔸 Example: Shallow Copy (Dangerous)

```cpp
class Sample {
    int* data;

public:
    Sample(int val) {
        data = new int(val);
    }

    void display() {
        cout << "Value: " << *data << endl;
    }

    ~Sample() {
        delete data;
        cout << "Destructor called" << endl;
    }
};

int main() {
    Sample s1(10);
    Sample s2 = s1;  // ❌ Shallow copy → both share the same memory
}
```
> ❗ **Both `s1` and `s2` point to the same memory**,  
> because the default copy constructor performs a **shallow copy**.  
> As a result, when both objects are destroyed, they **both attempt to delete the same memory**,  
> which causes a **double deletion error**, leading to a **crash or undefined behavior**.
## 🔁 3. What Is a Deep Copy?

A **deep copy** creates a **new memory allocation** and copies the **actual contents**  
of the dynamically allocated memory — not just the pointer.

---

### ✅ Benefits of Deep Copy:

- Each object has its **own independent memory**
- Prevents **unintended modifications** due to shared memory
- Avoids **memory corruption** and **double deletion errors**
- Ensures safe behavior in **dynamic memory management**

---

### 🔧 Example: Deep Copy (Safe Implementation)

```cpp
class Sample {
    int* data;

public:
    Sample(int val) {
        data = new int(val);
    }

    // Custom copy constructor for deep copy
    Sample(const Sample& s) {
        data = new int(*s.data);  // Allocate new memory and copy value
    }

    void display() {
        cout << "Value: " << *data << endl;
    }

    ~Sample() {
        delete data;  // Safe deallocation
    }
};
```
> ✅ Now `s1` and `s2` have **separate memory locations** and behave **independently**.  
> Modifying or deleting one object has **no effect** on the other — ensuring **safe, stable, and predictable behavior**.
## 🧠 4. Comparison Table: Shallow vs Deep Copy

| Feature              | **Shallow Copy**                           | **Deep Copy**                                |
|----------------------|---------------------------------------------|-----------------------------------------------|
| **Memory handling**  | Copies pointer only                         | Allocates new memory and copies content       |
| **Default/Manual**   | ✅ Done automatically by compiler           | ❌ Requires user-defined copy constructor      |
| **Object independence** | ❌ No — memory is shared                  | ✅ Yes — each object has separate memory       |
| **Risk**             | High — double deletion, dangling pointer    | Low — safe, independent memory handling       |
| **Used with pointers?** | ❌ Dangerous — memory sharing issues     | ✅ Recommended — avoids shared state           |

---

## 🔒 5. When Is Deep Copy Necessary?

Deep copy is **necessary** when your class uses **dynamic memory allocation**, such as with `new`.

You should implement a deep copy when working with:

- ✅ Dynamically allocated **strings** (e.g., `char*`)
- ✅ **Arrays** allocated at runtime
- ✅ **Linked lists** or tree structures
- ✅ **File handles** or external resource management
- ✅ Any time **two objects must not share the same memory**

> 🔐 Deep copy ensures that **each object owns its data**,  
> preventing bugs, crashes, and undefined behavior during object copying.
