---
id: Registers
aliases: []
tags: []
---

## Registers Overview

Registers are divided into following categories

- Instruction Pointer
- General Purpose register
- Status Flag Registers
- Segment Registers

### Instruction Pointer

- Contains the address of the next instruction to be executed
- Also called as program counter
- Originally was 16 bit in intel 8086, then known as IP
- In 32-bit processor, it is 32-bit and known as EIP (E stands for Extended)
- In 64-bit processor, it is 32-bit and known as RIP (R stands for Register)

### General Purpose Registers

- In x86 all are of 32 bit size
- In 64 bit (x86_64) all are of 64 bit size
- Used for general execution of instructions by the CPU

![registers](https://tryhackme-images.s3.amazonaws.com/user-uploads/61306d87a330ed00419e22e7/room-content/b3d7e425dae623de1ce2d57b25e4e809.png)

They contains the following registers

- EAX or RAX

  - Called as accumulator register
  - Stores the result of arithmetic operations
  - 32 bit called as EAX and 64 bit called as RAX
  - last 16 bit can be addressed by AX
  - Similarly AX's last 8 bit can be addressed as AL
  - AX's higher 8 bit can be addressed as AH

- EBX or RBX

  - Called as base register
  - Used to store the base address for referencing an ofset
  - 32 bit called as EBX and 64 bit called as RBX
  - last 16 bit can be addressed by BX
  - Similarly BX's last 8 bit can be addressed as BL
  - BX's higher 8 bit can be addressed as BH

- ECX or RCX

  - Called as count register
  - Used for counting operations such as loops etc
  - 32 bit called as ECX and 64 bit called as RCX
  - last 16 bit can be addressed by CX
  - Similarly CX's last 8 bit can be addressed as CL
  - CX's higher 8 bit can be addressed as CH

- EDX or RDX

  - Called as data register
  - Used in multiplication and division operation
  - 32 bit called as EDX and 64 bit called as RDX
  - last 16 bit can be addressed by DX
  - Similarly DX's last 8 bit can be addressed as DL
  - DX's higher 8 bit can be addressed as DH

- ESP or RSP

  - Called stack pointer
  - Points to the top of stack
  - Used in conjuction with stack segment register
  - Has a size of 32 bit in 32 bit processor where called as ESP
  - Has a size of 64 bit in 64 bit processor where called as RSP
  - Cannot be addressed as smaller registers

- ESI or RSI

  - Called source index
  - Used for string operation
  - Used in conjuction the data segment resgister as an offset
  - Has a size of 32 bit in 32 bit processor where called as ESI
  - Has a size of 64 bit in 64 bit processor where called as RSI
  - Cannot be addressed as smaller registers

- EDI or RDI

  - Called destination index
  - Used for string operation
  - Used in conjuction the extra segment resgister as an offset
  - Has a size of 32 bit in 32 bit processor where called as EDI
  - Has a size of 64 bit in 64 bit processor where called as RDI
  - Cannot be addressed as smaller registers

- R8 to R15
  - 64 bit general purpose registers
  - not available in 32 bit systems
  - can be addressed in 32, 16 and 8 bit modes
  - R8B for 8 bit mode (B stands for byte)
  - R8W for 16 bit mode (W stands for word)
  - R8D for 32 bit mode (D stands for double)

### Status Flag Registers

When performing execution, some indication about the status of the execution is sometimes required. This is where the Status Flags come in. This is a single 32-bit register for 32-bit systems called EFLAGS, which is extended to 64-bits for 64-bit systems, and called RFLAGS in the 64-bit system. The status flags register consists of individual single-bit flags that can be either 1 or 0. Some of the necessary flags are discussed below:

#### Zero Flag (ZF)

Denoted by ZF, the Zero Flag indicates when the result of the last executed instruction was zero. For example, if an instruction is executed that subtracts a RAX from itself, the result will be 0. In this situation, the ZF will be set to 1.

#### Carry Flag:

Denoted by CF, the Carry Flag indicates when the last executed instruction resulted in a number too big or too small for the destination. For example, if we add 0xFFFFFFFF and 0x00000001 and store the result in a 32-bit register, the result will be too big for the register. In this case, CF will be set to 1.

#### Sign Flag:

The Sign Flag or SF indicates if the result of an operation is negative or the most significant bit is set to 1. If these conditions are met, the SF is set to 1; otherwise, it is set to 0.

#### Trap Flag:

The Trap Flag or TF indicates if the processor is in debugging mode. When the TF is set, the CPU will execute one instruction at a time for debugging purposes. This can be used by malware to identify if they are being run in a debugger.

| General Registers    | Segment Registers | Status Registers | Instruction Pointer |
| -------------------- | ----------------- | ---------------- | ------------------- |
| RAX, EAX, AX, AH, AL | CS                | EFLAGS           | EIP, RIP            |
| RBX, EBX, BX, BH, BL | SS                |                  |                     |
| RCX, ECX, CX, CH, CL | DS                |                  |                     |
| RDX, EDX, DX, DH, DL | ES                |                  |                     |
| RBP, EBP, BP         | FS                |                  |                     |
| RSP, ESP, SP         | GS                |                  |                     |
| RSI, ESI, SI         |                   |                  |                     |
| RDI, EDI, DI         |                   |                  |                     |
| R8-R15               |                   |                  |                     |

### Segment Registers:

Segment Registers are 16-bit registers that convert the flat memory space into different segments for easier addressing. There are six segment registers, as explained below:

**Code Segment**: The Code Segment (CS ) register points to the Code section in the memory.

**Data Segment**: The Data Segment (DS) register points to the program's data section in the memory.

**Stack Segment**: The Stack Segment (SS) register points to the program's Stack in the memory.

**Extra Segments (ES, FS, and GS)**: These extra segment registers point to different data sections. These and the DS register divide the program's memory into four distinct data sections.
