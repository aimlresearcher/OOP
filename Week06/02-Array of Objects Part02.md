# 🎓 Static Arrays, Dynamic Arrays, and Array of Objects in C++

## 🎯 Learning Objectives

- Understand the concept of **static vs dynamic arrays**
- Declare and use **arrays of objects**
- Recognize the **memory management implications** of dynamic arrays
- Compare the use of arrays for storing **values** and **objects**

---

## 📌 1. Static Arrays

A **static array** has a fixed size known at **compile time**.

### 🔹 Characteristics:

- Memory is allocated on the **stack**
- Simple and **efficient**
- ❌ Not resizable during runtime

---

### 🔧 Example:

```cpp
int marks[5] = {90, 80, 70, 85, 95};
```
## 📦 Static Array as a Data Member:

```cpp
class Student {
private:
    int marks[5];

public:
    void input() {
        for (int i = 0; i < 5; i++) {
            cin >> marks[i];
        }
    }
};
```
## 💻 2. Dynamic Arrays

A **dynamic array** has a size determined at **runtime**, using **dynamic memory allocation**.

### 🔹 Characteristics:

- Memory is allocated on the **heap**
- Size is **controlled during execution**
- Requires **manual memory management** using `new` and `delete`

### 🔧 Example: Dynamic Array as Class Member

```cpp
class Student {
private:
    int* marks;
    int size;

public:
    Student(int n) {
        size = n;
        marks = new int[size];
    }

    void input() {
        for (int i = 0; i < size; i++) {
            cin >> marks[i];
        }
    }

    ~Student() {
        delete[] marks;
    }
};
```
## 🔁 3. Comparison: Static vs Dynamic Arrays

| Feature               | **Static Array**             | **Dynamic Array**                          |
|-----------------------|-------------------------------|---------------------------------------------|
| **Memory Allocation** | Stack                         | Heap                                        |
| **Size Flexibility**  | Fixed at compile time         | Decided at runtime                          |
| **Performance**       | Slightly faster               | Slightly slower due to heap access          |
| **Risk of Memory Leak** | ❌ No                         | ✅ Yes — if `delete[]` is not used properly |
| **Suitable For**      | Known fixed-size data         | Variable-length user input data             |

---

## 🧱 4. Array of Objects

An **array of objects** stores multiple instances of a class in a single array.

### 🔧 Example:

```cpp
class Book {
    string title;

public:
    void setTitle(string t) {
        title = t;
    }

    void display() {
        cout << "Title: " << title << endl;
    }
};

int main() {
    Book library[3];

    library[0].setTitle("C++ Basics");
    library[1].setTitle("Data Structures");
    library[2].setTitle("OOP Concepts");

    for (int i = 0; i < 3; i++) {
        library[i].display();
    }
}
```
> ✅ Objects in an array are **created and stored contiguously in memory**,  
> just like **primitive values**, allowing efficient iteration and access.
## 💡 5. Dynamic Array of Objects

Used when the number of objects is **unknown at compile time**.

```cpp
int n;
cout << "Enter number of books: ";
cin >> n;

Book* library = new Book[n];  // Dynamic array of objects

// Input and display logic...

delete[] library;  // Prevent memory leak
```