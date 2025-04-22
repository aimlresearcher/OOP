# 🎓 Lecture 9: Recursion in C++

## 🎯 Learning Objectives

By the end of this lecture, students will be able to:

- Understand the **concept of recursion**
- Write and **trace recursive functions**
- Compare **recursion** with **iteration**
- Apply recursion to **common programming problems**

---

## 🧠 1. What is Recursion?

**Recursion** is a programming technique where a **function calls itself** directly or indirectly  
to solve a **smaller instance** of the same problem.

---

## 🔁 2. Key Concepts

| Term           | Explanation                                                      |
|----------------|------------------------------------------------------------------|
| **Recursive Case** | Part of the function that **calls itself**                    |
| **Base Case**      | Condition to **stop recursion** (prevents infinite loop)      |
| **Stack**          | Each call is stored in memory (**call stack**) until it ends  |
## 🔹 3. Syntax of Recursive Function

```cpp
return_type function_name(parameters) {
    if (base_case_condition)
        return base_case_value;
    else
        return function_name(modified_parameters);
}
```
## 💡 4. Example 1: Factorial Using Recursion

```cpp
int factorial(int n) {
    if (n <= 1)
        return 1;                     // base case
    else
        return n * factorial(n - 1);  // recursive case
}
```
## ▶️ Trace for `factorial(3)`

```cpp
factorial(3) = 3 * factorial(2)
factorial(2) = 2 * factorial(1)
factorial(1) = 1  (base case)
Result = 3 * 2 * 1 = 6
```
## 💡 5. Example 2: Fibonacci Series

```cpp
int fibonacci(int n) {
    if (n == 0)
        return 0;
    else if (n == 1)
        return 1;
    else
        return fibonacci(n - 1) + fibonacci(n - 2);
}
```
> ⚠️ **Note:** This version is simple and easy to understand,  
but **inefficient for large `n`** due to **repeated recursive calls** (exponential time complexity).
## 🔄 6. Recursion vs Iteration

| Feature         | Recursion                      | Iteration                    |
|------------------|-------------------------------|------------------------------|
| Uses stack       | ✅ Yes                        | ❌ No                         |
| Memory usage     | Higher (stack frames)         | Lower                        |
| Code clarity     | Better for tree/graph problems| Better for loops             |
| Performance      | Slower in some cases          | Usually faster               |

---

## ⚠️ 7. Common Mistakes in Recursion

| Mistake             | Problem                                       |
|---------------------|-----------------------------------------------|
| Missing base case   | Infinite recursion (**program crash**)         |
| Incorrect base case | Wrong output or **no termination**            |
| Stack overflow      | Deep recursion without **optimization**       |
| No return value     | Causes **logical errors** in result handling  |

---

## 📦 8. Real-Life Examples of Recursion

- **Factorial, Fibonacci, Power calculation**  
- **Tree Traversals**: Preorder, Inorder, Postorder  
- **Backtracking**: Maze solving, N-Queens  
- **Sorting Algorithms**: QuickSort, MergeSort  
- **Tower of Hanoi** problem  
