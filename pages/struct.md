Type:: permanent_note
Created:: 2025-04-22
Tags:: [[c_programming]], [[aggregate type]]
Source:: [[Embedded Expert's Guide to C]]

- A `struct` in C is a user-defined data type that groups related variables (called members) under a single name. It is widely used to model complex data structures in embedded systems and general programming.
- ## 🧱 Defining a `struct`
  ```c
  struct Point {
    int x;
    int y;
  }
  ```
- ## 🎯 Accessing Members
  ```c
  int a = p1.x;
  p1.y = 25;
  ```
  If we have a pointer to a struct, it is best practice to use the [[arrow operator]] to access the members
  ```c
  struct Point *ptr = &p1;
  ```
- ## 🎯 Accessing Members
  ```c
  int a = p1.x;
  p1.y = 25;
  ```
  If we have a pointer to a struct, it is best practice to use the [[arrow operator]] to access the members
  ```c
  struct Point *ptr = &p1;
  int b = ptr->x;   // same as (*ptr).x
  ```