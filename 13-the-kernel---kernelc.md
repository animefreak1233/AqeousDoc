#The kernel - kernel.c
```
#include <stdint.h>
...
void ksetup(struct multiboot* multiboot_struct){
    setup_descriptors();
    enable_paging;
    load_drivers();
    kprintf("System setup finished\n");
    kprintf("Loading kernel");
    kmain();
}
...
```
Let's start with the first kernel function executed.
the first thing to notice is `struct multiboot* multiboot_struct`. It's a struct with the memory information passed by GRUB. One of the flags we passed was `MEM_INFO` in the multiboot header. This makes GRUB pass us information about the memory map of the system.
###setup_descriptors()
