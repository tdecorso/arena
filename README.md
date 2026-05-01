# Linear Arena Allocation in C
Basic implementation of arena linear allocation. It lets you allocate a block of memory and then "borrow" data from it. You then deallocate the whole block, and this enables a better cache behavior in alternative to many allocations.

## Usage 
Just include **arena.h** in your project.
### Allocation
```
arena_t* arena = arena_alloc(sizeof(int) * 100000); // you need to specify the total size of the arena data
arena_free(arena);
```
### Borrowing
```
arena_t* arena = arena_alloc(sizeof(int) * 100000);
int* region = arena_borrow(arena, sizeof(int) * 1000); // no need to allocate and free memory for the region
if (!region) printf("Space finished!\n");
arena_free(arena);
```
