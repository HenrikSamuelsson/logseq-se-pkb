Type::  [[permanent_note]]  
Created:: [[2025-04-20]]  
Tags:: [[c_programming]] [[bug]]   
Source:: [[Embedded Expert's Guide to C]]

- A pointer becomes a *dangling pointer* if it references a variable that have gone out of scope, or if it references a memory location that has been deallocated.
- *Example*: Returning a pointer to a local stack variable
  ```c
  char* get_fruit(void)
  {
    char fruit[] = "apple";
    return &fruit[0];
  }
  ```
- Dereferencing a dangling pointer is a bug, and must be avoided.
- Prevention strategies:
	- Avoid returning pointers to local stack variables.
	- Avoid [[dynamic memory allocation]].
- See also [[Wild Pointer]].