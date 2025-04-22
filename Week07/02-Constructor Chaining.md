# 🎓 Constructor and Destructor Chaining in Inheritance

## 🎯 Learning Objectives

- Understand the **order of constructor and destructor calls** in inheritance
- Use **constructor initialization lists** to call base class constructors
- Explain the importance of **constructor/destructor chaining** in object lifecycle

---

## 📌 1. What Is Constructor/Destructor Chaining?

When a **derived class object is created**:

- ✅ The **base class constructor** is called **first**
- ✅ Then the **derived class constructor** is called

When the object is **destroyed**:

- ✅ The **derived class destructor** is called **first**
- ✅ Then the **base class destructor** is called

🧠 This sequence is known as **constructor/destructor chaining**.

---

## 🔄 2. Constructor Chaining: Order of Execution

### 🔹 Example:

```cpp
class Base {
public:
    Base() { cout << "Base constructor\n"; }
    ~Base() { cout << "Base destructor\n"; }
};

class Derived : public Base {
public:
    Derived() { cout << "Derived constructor\n"; }
    ~Derived() { cout << "Derived destructor\n"; }
};

int main() {
    Derived d;
    return 0;
}
```
### 🔸 Output:

```kotlin
Base constructor
Derived constructor
Derived destructor
Base destructor
```
✅ Constructor Chain: `Base → Derived`  
✅ Destructor Chain: `Derived → Base`

---

## 🧠 3. Why Constructor Chaining Matters

- Ensures **base part** of the derived object is initialized **first**
- Helps maintain **clean class hierarchies**
- Prevents use of **uninitialized base members**
- Ensures proper **resource cleanup** during destruction

---

## 🔧 4. Parameterized Base Constructors and Initialization List

If the **base class lacks a default constructor**, the derived class must call it explicitly using an **initializer list**.

### 🔹 Example:

```cpp
class Base {
public:
    Base(int x) {
        cout << "Base constructor with x = " << x << endl;
    }
};

class Derived : public Base {
public:
    Derived(int x) : Base(x) {
        cout << "Derived constructor\n";
    }
};
```
> 🔍 Use the **constructor initializer list** to pass arguments to the base class constructor  
> when the base class does **not have a default constructor**.
## 📦 5. Chaining in Multilevel Inheritance

```cpp
class A {
public:
    A() { cout << "A constructor\n"; }
    ~A() { cout << "A destructor\n"; }
};

class B : public A {
public:
    B() { cout << "B constructor\n"; }
    ~B() { cout << "B destructor\n"; }
};

class C : public B {
public:
    C() { cout << "C constructor\n"; }
    ~C() { cout << "C destructor\n"; }
};
```
### 🔸 Output:

```cpp
A constructor
B constructor
C constructor
C destructor
B destructor
A destructor
```
> ✅ **Constructors** execute **top-down** (Base → Derived)  
> ✅ **Destructors** execute **bottom-up** (Derived → Base)
## ❗ Common Mistakes

| Mistake                             | Problem                                             |
|-------------------------------------|-----------------------------------------------------|
| Not using initializer list          | ❌ Fails to call base constructor with required arguments |
| Assuming destructors run before constructors | ❌ Incorrect — destructors run in **reverse** order  |
| Omitting virtual destructors in base class | ❌ Causes memory leaks in polymorphism scenarios     |
