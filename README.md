# 🧮 Infix to Postfix and Prefix Conversion using Stack (C++)

This project demonstrates **conversion of an infix expression** (like `A+B*C`) into its equivalent **postfix** and **prefix** forms using a **Stack implemented with a Singly Linked List** in **C++**.  

The program uses fundamental **data structure concepts** such as **stacks**, **linked lists**, and **operator precedence** to evaluate and rearrange arithmetic expressions efficiently.

---

## 🎯 Project Overview

In arithmetic expressions:
- **Infix:** Operators are written *between operands* (e.g., `A + B`)
- **Postfix (Reverse Polish):** Operators are written *after operands* (e.g., `A B +`)
- **Prefix (Polish):** Operators are written *before operands* (e.g., `+ A B`)

Computers prefer **postfix/prefix** formats because:
- They eliminate parentheses.
- Operator precedence and associativity are handled naturally.
- They are **easy to evaluate using a stack**.

This project provides:
- ✅ Conversion of **infix → postfix**
- ✅ Conversion of **infix → prefix**
- ✅ Implementation of **stack** using **linked list**
- ✅ Handling of operators: `+ - * / % ^`
- ✅ Support for parentheses and precedence rules

---

## ⚙️ Features

✔️ Converts any valid infix expression to both postfix and prefix forms  
✔️ Uses **dynamic memory allocation (linked list)** for the stack  
✔️ Handles **operator precedence and associativity** correctly  
✔️ User-friendly command-line interface  
✔️ Code written with **modular functions** and clear structure  

---

## 🧩 Code Structure

### 🧱 1. Node Class
Defines a singly linked list node.

```cpp
class Node {
public:
    char data;
    Node* next;
    Node(char value) {
        data = value;
        next = NULL;
    }
};
