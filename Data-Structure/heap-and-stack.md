# Heap and Stack
Programming language books usually explain that value types are created on the stack, and reference types are created on the heap, without really explaining what these two things are. With my only programming experience being in high level languages, I haven't read a clear explanation of this. I mean I understand what a stack is, but where and what are they (relative to the physical memory of a real computer)?
- To what extent are they controlled by the OS or language runtime?
- What is their scope?
- What determines the size of each of them?
- What makes one faster?

### 1. Answer One
The heap is memory set aside for dynamic allocation. Unlike the stack, there's no enforced pattern to the allocation and deallocation of blocks from the heap; you can allocate a block at any time and free it at any time. This makes it much more complex to keep track of which parts of the heap are allocated or free at any given time; there are many custom heap allocators available to tune heap performance for different usage patterns.
Each thread gets a stack, while there's typically only one heap for the application (although it isn't uncommon to have multiple heaps for different types of allocation).

- **To what extent are they controlled by the OS or language runtime**?
    - The OS allocates the stack for each system-level thread when the thread is created. Typically the OS is called by the language runtime to allocate the heap for the application.

- **What is their scope?**
    - The stack is attached to a thread, so when the thread exits the stack is reclaimed. The heap is typically allocated at application startup by the runtime, and is reclaimed when the application (technically process) exits.

- **What determines the size of each of them?**
    - The size of the stack is set when a thread is created. The size of the heap is set on application startup, but can grow as space is needed (the allocator requests more memory from the operating system).

- **What makes one faster?**
    - The stack is faster because the access pattern makes it trivial to allocate and deallocate memory from it (a pointer/integer is simply incremented or decremented), while the heap has much more complex bookkeeping involved in an allocation or free. Also, each byte in the stack tends to be reused very frequently which means it tends to be mapped to the processor's cache, making it very fast. Another performance hit for the heap is that the heap, being mostly a global resource, typically has to be multi-threading safe, i.e. each allocation and deallocation needs to be - typically - synchronized with "all" other heap accesses in the program.
    
    ![](./img/heap_stack_0.png?raw=true)

### Answer Two
- Stack
    - Stored in computer RAM just like the heap
    - Variables created on the stack will go out of scope and automatically deallocate
    - Much faster to allocate in comparision to variables on the heap
    - Implemented with an actual stack data structure
    - Stores local data, erturn addresses, used for parameter passing
    - Can have a stack overflow when too much of the stack is used. (mostly from infinite or too much recursion, very large allocations)
    - Data created on the stack can be used without pointers
    - You would use the stack if you know exactly how much data you need to allocate before compile time and it is not too big.
    - Usually has a maximum size already determined when your program starts.

- Heap 
    - Stored in computer RAM just like the stack.
    - Variables on the heap must be destroyed manually and never fall out of scope. The data is freed with delete, delete[] or free
    - Slower to allocate in comparison to variables on the stack.
    - Used on demand to allocate a block of data for use by the program.
    - Can have fragmentation when there are a lot of allocations and deallocations
    - In C++ data created on the heap will be pointed to by pointers and allocated with new or malloc
    - Can have allocation failures if too big of a buffer is requested to be allocated.
    - You would use the heap if you don't know exactly how much data you will need at runtime or if you need to allocate a lot of data.
    - Responsible for memory leaks

- Example
```
int foo()
{
  char *pBuffer; //<--nothing allocated yet (excluding the pointer itself, which is allocated here on the stack).
  bool b = true; // Allocated on the stack.
  if(b)
  {
    //Create 500 bytes on the stack
    char buffer[500];
    //Create 500 bytes on the heap
    pBuffer = new char[500];
   }//<-- buffer is deallocated here, pBuffer is not
}//<--- oops there's a memory leak, I should have called delete[] pBuffer;
```

The most important point is that heap and stack are generic terms for ways in which memory can be allocated. They can be implemented in many different ways, and the terms apply to the basic concepts.
- In a stack of items, items sit one on top of the other in the order they were placed there, and you can only remove the top one (without toppling the whole thing over).
- In a heap, there is no particular order to the way items are placed. You can reach in and remove items in any order because there is no clear 'top' item.

