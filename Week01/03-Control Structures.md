# 👨‍🏫 Instructor Introduction

**Name:** Syed Hamed Raza  
**Education:** MS in Computer Science from HUST, Wuhan, China  
**Current Roles:**  
- PhD Scholar at COMSATS University  
- Lecturer at University of Management and Technology (UMT), Lahore  


# 🎓 Control/Iterative Statements and Arrays

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand and apply conditional statements (`if`, `else`, `switch`)
- Use iterative loops (`while`, `for`, `do-while`)
- Declare, initialize, and manipulate arrays

---

## 🧭 1. Control Statements (Selection)

### 🔹 `if` Statement

Used to execute a block of code only if a specified condition is true.

```cpp
int number = 10;
if (number > 0) {
    cout << "Positive number";
}
```
### 🔹 `if-else` Statement

Executes one block of code if the condition is true, and another if it's false.

```cpp
if (age < 18) {
    cout << "Not eligible.";
} else {
    cout << "Eligible.";
}
```
### 🔹 `else-if` Ladder

Used when you have multiple conditions to evaluate in sequence.

```cpp
if (marks >= 90) {
    cout << "Grade A";
} else if (marks >= 80) {
    cout << "Grade B";
} else {
    cout << "Needs Improvement";
}
```
### 🔹 `switch` Statement

Used to select one of many code blocks to be executed based on a variable's value.

```cpp
int choice;
cin >> choice;

switch (choice) {
    case 1: 
        cout << "Start"; 
        break;
    case 2: 
        cout << "Stop"; 
        break;
    default: 
        cout << "Invalid";
}
```
> 💡 **Note:** Use `break` to exit a case. Without it, execution continues to the next case (**fall-through**).
## 🔁 2. Iterative Statements (Loops)

### 🔹 `while` Loop

Executes a block of code **as long as the condition is true**.

```cpp
int i = 1;
while (i <= 5) {
    cout << i << " ";
    i++;
}
```
### 🔹 `do-while` Loop

Executes the block of code **at least once**, then repeats **while the condition is true**.

```cpp
int i = 1;
do {
    cout << i << " ";
    i++;
} while (i <= 5);
```
> 💡 Ensures the loop runs at least once.

### 🔹 `for` Loop

Best used when the number of iterations is known.

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
```
| Loop Type | Best Use Case                     |
|-----------|-----------------------------------|
| `while`   | When number of iterations is unknown |
| `do-while`| At least one execution needed     |
| `for`     | Fixed number of iterations        |

## 📦 3. Arrays in C++

### 🔹 What is an Array?

An array is a **collection of elements** of the **same data type** stored in **contiguous memory locations**. It allows you to store and access multiple values using a single variable name and an index.

---

### 🔹 Declaration & Initialization

```cpp
int nums[5];                     // Declaration only
int nums2[5] = {1, 2, 3, 4, 5};  // Initialization
```
### 🔹 Accessing Elements

```cpp
cout << nums2[0]; // Output: 1
nums2[3] = 10;    // Modify 4th element
```
### 🔹 Input & Output with Arrays

```cpp
int marks[3];

// Input values
for (int i = 0; i < 3; i++) {
    cin >> marks[i];
}

// Output values
for (int i = 0; i < 3; i++) {
    cout << marks[i] << " ";
}
```
## 🧪 Example: Sum of Array Elements

```cpp
#include <iostream>
using namespace std;

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    int sum = 0;
    
    for (int i = 0; i < 5; i++) {
        sum += numbers[i];
    }
    
    cout << "Sum = " << sum;
    return 0;
}
```
## 📝 Class Activity

**Task:**  
Write a program to:

- Take **name** and **marks** of a student  
- Calculate **percentage**  
- Display **name** and **percentage**

---

