# 👨‍🏫 Instructor Introduction

**Name:** Syed Hamed Raza  
**Education:** MS in Computer Science from HUST, Wuhan, China  
**Current Roles:**  
- PhD Scholar at COMSATS University  
- Lecturer at University of Management and Technology (UMT), Lahore  

# 🎓 Pointers in C++

## 🎯 Learning Outcomes

By the end of this lecture, students will be able to:

- Understand what **pointers** are and how they work  
- Declare and use pointers with **variables and arrays**  
- Differentiate between **address**, **dereferencing**, and **pointer arithmetic**  
- Use pointers with **functions** and **dynamic memory**

---

## 📌 1. What is a Pointer?

A **pointer** is a variable that stores the **memory address** of another variable.

---

## 🧠 2. Key Terms & Explanations

| Term                    | Explanation                                                              | Example                   |
|-------------------------|---------------------------------------------------------------------------|---------------------------|
| Pointer Variable        | A variable that holds the address of another variable.                   | `int *p;`                 |
| Address-of Operator `&` | Returns the memory address of a variable.                                | `p = &x;`                 |
| Dereferencing Operator `*` | Accesses the value stored at the address a pointer is pointing to.    | `cout << *p;`             |
| Null Pointer            | A pointer that points to nothing (safe initialization).                  | `int* p = nullptr;`       |
| Pointer Arithmetic      | Adding or subtracting integers to move through memory locations.         | `p++` moves to next cell  |
| Dynamic Memory Allocation | Allocating memory at runtime using `new` / deallocating with `delete`. | `int* ptr = new int;`     |
| Dangling Pointer        | A pointer pointing to memory that has been deleted or freed.             | Avoid: `delete ptr; *ptr = 5;` |
| Void Pointer            | A generic pointer that can point to any data type.                       | `void* vp;`               |

## 💡 3. Example: Basic Pointer Usage

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10;
    int *ptr = &x;

    cout << "Value of x: " << x << endl;
    cout << "Address of x: " << &x << endl;
    cout << "Pointer ptr holds: " << ptr << endl;
    cout << "Value pointed by ptr: " << *ptr << endl;

    return 0;
}
```
## 📌  Pointer Arithmetic

In C++, **pointers can be manipulated using arithmetic operators** to move between memory locations.  
This is especially useful when working with arrays or dynamically allocated memory.

---

### 🔹 Valid Pointer Arithmetic Operations

| Operation       | Description                                          |
|-----------------|------------------------------------------------------|
| `ptr + n`       | Moves pointer `n` elements forward                   |
| `ptr - n`       | Moves pointer `n` elements backward                  |
| `ptr++`         | Moves pointer to the next element (post-increment)   |
| `++ptr`         | Same as above (pre-increment)                        |
| `ptr--`         | Moves pointer to the previous element                |
| `ptr1 - ptr2`   | Returns number of elements between two pointers      |
| `ptr1 == ptr2`  | Compares if two pointers point to the same location  |

> ⚠️ All operations are done in **element units**, not bytes.  
For example, if `int` takes 4 bytes and `ptr++` is executed, the pointer moves **4 bytes** ahead in memory.
## 💡 Example 1: Traversing an Array Using Pointer Arithmetic

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int* ptr = arr;  // points to first element

    cout << "Traversing array using pointer arithmetic:\n";
    for (int i = 0; i < 5; i++) {
        cout << "Value at ptr + " << i << " = " << *(ptr + i) << endl;
    }

    return 0;
}
```
### 🧠 Explanation:

- `*(ptr + i)` gives the **value at position `i`** in the array.
- `ptr + i` moves the pointer **`i` elements forward** from the start of the array.
## 💡 Example 2: Using `ptr++` and `*ptr`

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {5, 10, 15, 20};
    int* ptr = arr;

    cout << "Using ptr++ to print values:\n";
    while (ptr < arr + 4) {
        cout << *ptr << " ";
        ptr++;
    }

    return 0;
}
### 🔎 Output:

```cpp
5 10 15 20
```
## 💡 Example 3: Pointer Subtraction

```cpp
#include <iostream>
using namespace std;

int main() {
    int nums[] = {100, 200, 300, 400, 500};
    int* start = nums;
    int* end = nums + 4;

    cout << "Elements between start and end: " << end - start << endl;
    return 0;
}
```
### 📌 Output:

```cpp
Elements between start and end: 4
```
> 📘 **Note:** Pointer subtraction gives the **number of elements** (not bytes) between two pointers.
## 💡 Example 4: Reverse Traversal

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    int* ptr = arr + 4; // last element

    cout << "Reverse order using pointer:\n";
    while (ptr >= arr) {
        cout << *ptr << " ";
        ptr--;
    }

    return 0;
}
```
### 🧠 Output:
```cpp
5 4 3 2 1
```
## ❌ Common Mistakes to Avoid

| Mistake                              | Why it's wrong                               |
|--------------------------------------|-----------------------------------------------|
| Dereferencing uninitialized pointer  | May cause crash (undefined behavior)         |
| Exceeding array bounds               | Leads to memory access violations            |
| Comparing pointers to unrelated arrays | Invalid and misleading results              |
## 📌 Dynamic Memory Allocation
## 📌 1. What is Dynamic Memory Allocation?

**Dynamic Memory Allocation** allows memory to be **allocated during runtime** instead of compile time.

---

### 🔍 Why Use It?

- When the size of data structures like arrays is **not known at compile time**
- Enables **efficient memory management**
- Used heavily in **object-oriented** and **real-time applications**

## 🧠 2. Key Terms

| Term             | Explanation                                       |
|------------------|---------------------------------------------------|
| `new`            | Allocates memory on the **heap**                  |
| `delete`         | Deallocates memory                                |
| **Heap**         | Memory segment used for **dynamic allocation**    |
| **Memory leak**  | Forgetting to `delete` dynamically allocated memory |
| **Dangling pointer** | Pointer to memory that has already been freed  |
## 🧪 3. Allocating Single Variable Using `new`

```cpp
#include <iostream>
using namespace std;

int main() {
    int* p = new int;   // Allocates memory for one int
    *p = 25;

    cout << "Value: " << *p << endl;

    delete p;  // Deallocate memory
    return 0;
}
```
> 🔑 **Always** use `delete` to free dynamically allocated memory once you're done using it to avoid memory leaks.

## 📦 4. Dynamic 1D Array

```cpp
#include <iostream>
using namespace std;

int main() {
    int size;
    cout << "Enter array size: ";
    cin >> size;

    int* arr = new int[size];  // Dynamic array

    cout << "Enter elements:\n";
    for (int i = 0; i < size; i++) {
        cin >> arr[i];
    }

    cout << "You entered:\n";
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }

    delete[] arr;  // Deallocate array memory
    return 0;
}
```
## 🧭 5. Dynamic 2D Array

```cpp
#include <iostream>
using namespace std;

int main() {
    int rows = 3, cols = 4;

    // Step 1: Allocate row pointers
    int** matrix = new int*[rows];

    // Step 2: Allocate columns for each row
    for (int i = 0; i < rows; i++) {
        matrix[i] = new int[cols];
    }

    // Fill matrix
    cout << "Enter matrix elements:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cin >> matrix[i][j];
        }
    }

    // Display matrix
    cout << "Matrix is:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }

    // Free memory
    for (int i = 0; i < rows; i++) {
        delete[] matrix[i];
    }
    delete[] matrix;

    return 0;
}
```
## ⚠️ 6. Common Mistakes

| Mistake                        | Explanation                                              |
|-------------------------------|----------------------------------------------------------|
| Not using `delete`            | Causes **memory leak**                                   |
| Using `delete` instead of `delete[]` | Results in **undefined behavior**                 |
| Accessing deleted memory      | Leads to crash (**dangling pointer**)                    |
| Mixing stack and heap         | Always match `new` with `delete`, and `new[]` with `delete[]` |

## 🎓 Pointers and Functions in C++



## 📌 1. Why Use Pointers with Functions?

- To **modify the original variables** inside a function  
- To **avoid copying** large amounts of data (more efficient)  
- To **return multiple values** from a function  
- To work with **dynamic memory** and arrays

---

## 🧠 2. Parameter Passing Methods

| Method              | Description                                         |
|---------------------|-----------------------------------------------------|
| **Pass-by-Value**   | Copies actual value. Changes don't affect original. |
| **Pass-by-Pointer** | Passes address. Allows modifying original value.    |
| **Pass-by-Reference** | Uses alias to variable. Modifies original directly. |
## 🧪 3. Example: Pass-by-Value (Default)

```cpp
void change(int x) {
    x = 100;
}

int main() {
    int num = 50;
    change(num);
    cout << "num = " << num; // Output: 50
}
```
> 🧩 No change in original value — `x` is a **copy** of `num`.
## 🔁 4. Example: Pass-by-Pointer

```cpp
void change(int* x) {
    *x = 100;
}

int main() {
    int num = 50;
    change(&num);  // pass address
    cout << "num = " << num;  // Output: 100
}
```
> ✅ The value is changed through the pointer using `*x`.

## 📎 5. Example: Pass-by-Reference

```cpp
void change(int &x) {
    x = 100;
}

int main() {
    int num = 50;
    change(num);  // no need for &
    cout << "num = " << num;  // Output: 100
}
```
> 🔁 Reference variable `x` is just another name (**alias**) for `num`.

## 📦 6. Comparing All 3 Methods

| Method             | Syntax in Call | Syntax in Function       | Can Modify Original? |
|--------------------|----------------|---------------------------|-----------------------|
| **Pass-by-Value**  | `change(x)`    | `void change(int x)`      | ❌ No                 |
| **Pass-by-Pointer**| `change(&x)`   | `void change(int* x)`     | ✅ Yes                |
| **Pass-by-Reference** | `change(x)` | `void change(int& x)`     | ✅ Yes                |
## 🔍 7. Example: Swap Function (Pass-by-Reference)

```cpp
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 5, y = 10;
    swap(x, y);
    cout << "x = " << x << ", y = " << y;  // Output: x = 10, y = 5
}
```
## 🧪 8. Example: Array with Pointer Parameter

```cpp
void printArray(int* arr, int size) {
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
}

int main() {
    int nums[] = {10, 20, 30, 40};
    printArray(nums, 4);
}
```
> 📎 Arrays are passed as **pointers by default** in C++, meaning the function receives the address of the first element.
## ⚠️ 9. Common Mistakes

| Mistake                              | Problem                                         |
|--------------------------------------|-------------------------------------------------|
| Forgetting `*` in pointer dereferencing | Will not access or modify the value             |
| Forgetting `&` in pass-by-pointer call | Will pass value instead of address              |
| Modifying through value parameter    | Will not reflect changes in caller              |
| Mixing reference and pointer improperly | Leads to confusion and bugs                     |

