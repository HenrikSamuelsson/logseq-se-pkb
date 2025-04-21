Type::  [[permanent_note]]  
Created:: [[2025-04-21]]  
Tags:: [[c_programming]] [[bug]]   
Source:: [[Embedded Expert's Guide to C]]

- *Wild pointer* in C is an uninitialized pointer, containing a random memory address thus pointing to an invalid or non-existent memory location.
- Example: Wild pointer
  ```c
  char *dp;    /* dp is a wild pointer. */
  ```
- Prevention strategies:
	- Initialize the pointer directly at the point of declaration.
	- As a backup we can also explicitly set to `NULL` to be able to  safely check if it’s usable before dereferencing.