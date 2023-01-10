# Manual Memory Management

You allocate and deallocate heap memory yourself.

## C Example

You must call `free` on every pointer you allocate with `malloc`:

```c
void foo(size_t n) {
    int* int_array = (int*)malloc(n * sizeof(int));
    //
    // ... lots of code
    //
    free(int_array);
}
```

Memory is leaked if the function returns early between `malloc` and `free`: the
pointer is lost and we cannot deallocate the memory.

<details>

Challenge: How to make sure you free the memory exactly once at the right time?

* If you free too early, you could end up with use-after-free issues.
* If you free too late, or miss to free the memory, you'd end up with memory leaks.
* If you free multiple times, you get double-free issues. 
</details>
