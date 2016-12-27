# The Dive - boot.s
I'll start by explaining the code in *boot.s*. This file is the start of everything. Since we're relying on   grub, we've made sure to make it multiboot compatible (v1.6).
The necessary code is explained below-

```MAGIC equ 0xE85250D6
ARCH equ 0  
HEADER_LENGTH equ multiboot_end - multiboot_end  
CHECKSUM equ -(MAGIC + ARCH + HEADER_LENGTH)  
ALIGN 8, db 0  
section .multiboot
multiboot_start:
        DD MAGIC
        DD ARCH
        DD HEADER_LENGTH
        DD CHECKSUM
multiboot_end:```
