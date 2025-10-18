# Analysis and Reporting

1. Which program is fastest? Is it always the fastest?<br/>
alloca.cpp is the fastest with high numbers of blocks, but at low numbers it is comparable to malloc.  

2. Which program is slowest? Is it always the slowest?<br/>
list.cpp is the slowest and it is always the slowest.

3. Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?<br/>
Yes, except for alloca.cpp, the greater the size, the slower the execution time. alloca.cpp stayed consistent no matter the size.  

4. Was there a trend in program execution time based on the length of the block chain?<br/>
No, there was no significant change between a length of 10,000 and 10,000,000.  

5. Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?<br/>
After many different experiments, changing MIN_BYTES, MAX_BYTES, MAX_BLOCKS, and optimization level, the number of breaks listed always stayed at 1 for each.  

6. Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes. Include in the diagram<br/>
  - the relationship of the head, tail, and Node next pointers.
  - show the size (in bytes) and structure of a Node that allocated six bytes of data
  - include the bytes pointer, and indicate using an arrow which byte in the allocated memory it points to.
```
head                         tail
 V                            V
Node* next    (8 bytes) ---> Node* next    (8 bytes) ---> nullptr
Size numBytes (4 bytes)      Size numBytes (4 bytes)
Byte* bytes   (8 bytes)      Byte* bytes   (8 bytes)
        |                            |
        V                            V
memory: 1 2 3 4 5 6          memory: 1 2 3 4 5 6
```

7. There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?<br/>
Allocation is handled differently for each program. list.cpp makes use of std::list, new.cpp uses the new operator, malloc.cpp uses malloc(), and alloca.cpp uses alloca(). Initialization is done  
pretty similarly with each program using std::iota(). Procesing is handled the same in each.

8. As the size of data in a Node increases, does the significance of allocating the node increase or decrease?<br/>
The significance of allocating the node should decrease as data size increases, because the overhead from having larger amounts of data begins to outweigh the overhead from node allocation.
