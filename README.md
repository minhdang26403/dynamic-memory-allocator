# Dynamic memory allocator

Implementation of malloc(), free(), realloc(), calloc() in C. 

There are three versions of the memory allocator. The `mm-naive.c` is the naive implementation of the memory allocator. It just uses the virtual memory as a large array of bytes to allocate memory and never frees memory. This approach achieves a high throughput (number of requests per time) at the expense of memory utilization. The second implementation `mm-implicit.c` uses an implicit list to store both allocated and free blocks. This version can reuse allocated blocks, thus achieving better memory utilization. However, since we keep a long list of allocated and free blocks, the running time of `malloc()` will be much longer. The third implementation `mm-explicit.c` balances throughput and memory utilization. It uses an explicit free list to store only free blocks since we don't care about allocated blocks. Memory utilization of `mm-implicit.c` and `mm-explicit.c` is roughly the same, but the explicit free list version has better throughput.

These implementations of malloc also impose a minimum block size of 4 words for each allocated block (header, footer, payload, and padding). With the free block in the explicit free list version, we can use the payload to store the predecessor and successor free blocks in the explicit free list.

# Things to improve

Implement the memory allocator using a segregated free list. This is a more sophisticated version of explicit free list since it will keep track many explicit free lists with different size classes.