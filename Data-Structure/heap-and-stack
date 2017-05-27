# Heap and Stack
Programming language books usually explain that value types are created on the stack, and reference types are created on the heap, without really explaining what these two things are. With my only programming experience being in high level languages, I haven't read a clear explanation of this. I mean I understand what a stack is, but where and what are they (relative to the physical memory of a real computer)?
- To what extent are they controlled by the OS or language runtime?
- What is their scope?
- What determines the size of each of them?
- What makes one faster?

### 1. To what extent are they controlled by the OS or language runtime?
The heap is memory set aside for dynamic allocation. Unlike the stack, there's no enforced pattern to the allocation and deallocation of blocks from the heap; you can allocate a block at any time and free it at any time. This makes it much more complex to keep track of which parts of the heap are allocated or free at any given time; there are many custom heap allocators available to tune heap performance for different usage patterns.
Each thread gets a stack, while there's typically only one heap for the application (although it isn't uncommon to have multiple heaps for different types of allocation).
- **To what extent are they controlled by the OS or language runtime**?
The OS allocates the stack for each system-level thread when the thread is created. Typically the OS is called by the language runtime to allocate the heap for the application.
- **What is their scope?**
The stack is attached to a thread, so when the thread exits the stack is reclaimed. The heap is typically allocated at application startup by the runtime, and is reclaimed when the application (technically process) exits.
- **What determines the size of each of them?**
The size of the stack is set when a thread is created. The size of the heap is set on application startup, but can grow as space is needed (the allocator requests more memory from the operating system).
- **What makes one faster?**
The stack is faster because the access pattern makes it trivial to allocate and deallocate memory from it (a pointer/integer is simply incremented or decremented), while the heap has much more complex bookkeeping involved in an allocation or free. Also, each byte in the stack tends to be reused very frequently which means it tends to be mapped to the processor's cache, making it very fast. Another performance hit for the heap is that the heap, being mostly a global resource, typically has to be multi-threading safe, i.e. each allocation and deallocation needs to be - typically - synchronized with "all" other heap accesses in the program.
    ![](heap_stack_0.png?raw=true)
