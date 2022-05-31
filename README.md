# Cortex-M MCU 

### Register 

R0
R1
R2
R3
R4
R5
R6
R7
R8
R9
R10
R11
R12
SP(R13)
LR(R14)
PC(R15)
(Special Registers)
PSR
PRIMASK 
FAULTMASK
BASEPRI
CONTROL


R0 - R7: Low Registers
R8 - R15: High Registers
SP: Stack Pointer
LR: Link Register
PC: Program Counter

R0-R12: General-purpose Registers

PSR: Program Status Register

Exception Mask Register
PRIMASK
FAULTMASK
BASEPRI
CONTROL: CONTROL Register

### R0-R12 GP Registers

R0-R12 are 32-bit general-purpose registers for data operations

### Stack Pointer

The Stack Pointer (SP) is R13. In Thread mode, bit[1] of the CONTROL register indicates the stack pointer to use





