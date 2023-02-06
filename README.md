# CC Assembler
An assembler for the CC Virtual Machine

<br />

---

<br />

## Mneumonics
| Mnemonic | Description |
|----------|-------------|
| MOV | Move a value into a register |
| PSH | Push a value onto the stack |
| POP | Pop a value off the stack |
| SYS | Perform a syscall |
| STP | Stop execution |
| FRS | Reset all flags |
| JMP | Jump to a label |
| JNE | Jump to a label if the not equal flag is set |
| JEQ | Jump to a label if the equal flag is set |
| JLT | Jump to a label if the less than flag is set |
| JGT | Jump to a label if the greater than flag is set |
| JOF | Jump to a label if the overflow flag is set |
| CALL | Call a subroutine |
| RET | Return from a subroutine |

<br />

---

<br />

## Syntax
```asm
; Comments work with semicolons

; There are 8 registers: a, b, c, d, e, f, g, h
; You can move data into registers with the MOV instruction
; MOV takes two arguments: the register to move into, and the value to move
; The registers are all in the form of 32 bit unsigned integers
; - You can move a literal value into a register
; - You can move the value of another register into a register
MOV a, 1234
MOV b, a

; The CCVM also has a stack into which you
; can push and pop 32bit unsigned values
PSH 1
PSH 2
POP a
POP b
PSH b
POP c

; You can perform syscalls, a syscall looks at register a to know what 'action'
; it should perform, and optionally looks at the other registers to know the
; arguments to the syscall

; printing syscall
; a = 0
; b = the address of the string to print
; c = the length of the string to print
MOV a, 0
MOV b, 12345
MOV c, 5
SYS

; This is how you stop execution
STP
```