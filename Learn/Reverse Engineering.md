# Reverse Engineering

## CPU

### Instructions
A primitive CPU command. The simplest examples include:
- Moving data between two registers
- Adding two numbers
- Working with memory

**Each CPU has its own instruction set architecture (ISA)**

### Machine Code 
Code that can be processed directly by CPU. Each instrcution is useually ecndoed by several bytes. 

### Assembly Language
Mnemonic code and some extensions, like macros, that are intended to make a programmers life easier.

### CPU Register
Each CPU has a fixed set of **general purpose registers (GPR)** 
- Approx 8 in x86
- Approx 16 in x86-64
- 16 in ARM

The best way to model a register is to think of it as an untyped temporary variable. 

The program that converts the high-level PL code into assembly is called a compiler.

**A couple of words about different ISAs**
- The x86 ISA has always had variable-length instructions, so when the 64-bit era came, the x64 extensions did not impact the ISA very significantly.
- In fact, the x86 ISA still contains a lot of instructions that first appeared in 16-bit 8086 CPU, yet are still found in the CPUs of today.
- ARM is a RISC 4 CPU designed with constant-length instructions in mind, which had some advantages in the past.
- ARM was later modified to a THUMB mode which consisted of 2bytes long instruction
- And later after they extended the THUMB to THUMB2 which appeared in ARMv7
- Majority of applications for iPod/iPhone/iPad are compiled for the Thumb-2 instruction set.
- Later the 64-bit ARM came out.
- Resulting in us now having three ARM instrution sets: ARM mode, Thumb mode (including Thumb-2) and ARM64.

### Numeral Systems
- A number is a number, while digit is a term from writing systems, and is usually one character.
- The value of a number does not change when converted to another radix; only the writing notation for that value has changed (and therefor the way or representing it in RAM)

### Converting From one Radix to Another

What does 1234 stands for ?
10^3 ⋅ 1 + 10^2 ⋅ 2 + 10^1 ⋅ 3 + 1 ⋅ 4 = 1234 or 1000 ⋅ 1 + 100 ⋅ 2 + 10 ⋅ 3 + 4 = 1234

**It’s the same story for binary numbers, but the base is 2 instead of 10. What does 0b101011 stand for?**
2^5 ⋅ 1 + 2^4 ⋅ 0 + 2^3 ⋅ 1 + 2^2 ⋅ 0 + 2^1 ⋅ 1 + 2^0 ⋅ 1 = 43 or 32 ⋅ 1 + 16 ⋅ 0 + 8 ⋅ 1 + 4 ⋅ 0 + 2 ⋅ 1 + 1 = 43

- Binary numbers are bulky when represented in source code and dumps, so that is where the hexadecimal numeral system can be useful
- A hexadecimal radix uses the digits 0..9, and also 6 Latin characters: A..F.

**How to identify number radix**
- Binary numbers are sometimes prepended with the ”0b” prefix: 0b100110111
- assemblers allow an identifier on decimal radix numbers, in which the number would be written with a ”d” suffix: 1234d.
- Hexadecimal numbers are prepended with ”0x” prefix in C/C++ and other PLs: 0x1234ABCD.
- Alternatively, they are given a ”h” suffix: 1234ABCDh.


## Questions?
- Learn how to store large number like BIG INTEGER in java ?
- 