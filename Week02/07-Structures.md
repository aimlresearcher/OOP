# 🎓 Structures in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand what **structures** are and why they are used  
- Define and declare **structure types** in C++  
- Create **structure variables** and access their members  
- Use **structures with functions and arrays**  
- Differentiate between **structures and classes**

---

## 📌 1. What is a Structure?

A **structure** in C++ is a **user-defined data type** that allows grouping of variables of **different data types** under one name.

---

### 🔹 Why Use Structures?

- ✅ Combine related data (e.g., name, age, GPA of a student)  
- ✅ Organize code and make it more **modular**  
- ✅ Used for **records**, **entities**, and modeling **real-world objects**
## 🧱 2. Syntax of a Structure

```cpp
struct StructureName {
    dataType member1;
    dataType member2;
    // ...
};
```
## 💡 3. Example: Defining and Using a Structure

```cpp
#include <iostream>
using namespace std;

struct Student {
    string name;
    int rollNo;
    float gpa;
};

int main() {
    Student s1;

    s1.name = "Ali";
    s1.rollNo = 101;
    s1.gpa = 3.75;

    cout << "Name: " << s1.name << endl;
    cout << "Roll No: " << s1.rollNo << endl;
    cout << "GPA: " << s1.gpa << endl;

    return 0;
}
```
## 🧾 4. Accessing Members

Use the **dot operator (`.`)** to access structure members:

```cpp
Student s1;
s1.name = "Sara";
cout << s1.name;
```
## 📚 5. Structure Initialization

You can **initialize a structure** at the time of declaration:

```cpp
Student s2 = {"Ahsan", 102, 3.85};
```
## 🧩 6. Array of Structures

```cpp
Student students[3];

// Input data
for (int i = 0; i < 3; i++) {
    cin >> students[i].name >> students[i].rollNo >> students[i].gpa;
}

// Output data
for (int i = 0; i < 3; i++) {
    cout << students[i].name << " " << students[i].rollNo << " " << students[i].gpa << endl;
}
```
## 🔁 7. Structures with Functions

### 🔹 Pass by Value

```cpp
void display(Student s) {
    cout << s.name;
}
```
### 🔹 Pass by Reference

```cpp
void updateGPA(Student &s) {
    s.gpa += 0.1;
}
```
## 🧠 8. Structure vs Class

| Feature         | `struct`                            | `class`                                   |
|------------------|--------------------------------------|--------------------------------------------|
| **Default access** | `public`                           | `private`                                  |
| **OOP Support**    | No (but can act like a class)       | Yes (supports all OOP principles)          |
| **Use Case**       | Grouping related **data**           | Full-fledged **object modeling**           |
## ⚠️ 9. Common Mistakes

| Mistake                             | Problem                                     |
|-------------------------------------|---------------------------------------------|
| Forgetting semicolon after `struct` | ❌ Compilation error                         |
| Accessing members without `.` operator | ❌ Undefined behavior                        |
| Mixing up value/reference passing   | ⚠️ May not update original values as expected |
