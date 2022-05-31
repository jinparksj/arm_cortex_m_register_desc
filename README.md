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
PRIMASK: Priority Mask Register
FAULTMASK
BASEPRI
CONTROL: CONTROL Register

### R0-R12 GP Registers

R0-R12 are 32-bit general-purpose registers for data operations

### Stack Pointer

The Stack Pointer (SP) is R13. In Thread mode, bit[1] of the CONTROL register indicates the stack pointer to use:
0 - Main Stack Pointer (MSP). This is reset value.
1 - Process Stack Pointer (PSP). On reset, the processor loads the MSP with the value from the implementation-defined address, 0x00000000.

### Link Register

The LR is R14. 
It stores the return information for subroutines, function calls, and exceptions. On reset, the processor sets the LR value to 0xFFFFFFFF.

### Program Counter

The Program Counter (PC) is register R15. 
It contains the current program address. 
On reset, the processor loads the PC with the value of the reset vector, which is at the initial value of Vector Table Offset Register(VTOR)
plus 0x00000004. 
Bit[0] of the value is loaded into the EPSR T-bit at reset and must be 1.
https://developer.arm.com/documentation/dui0646/b/Cortex-M7-Peripherals/System-control-block/Vector-Table-Offset-Register?lang=en

### Program Status Register

- Application Program Status Register (APSR): bit 31, 30, 29, 28, 27, 19 - 16
31: N - Negative Flag
30: Z - Zero Flag
29: C - Carry or borrow flag
28: V - Overflow Flag
27: Q - DSP Overflow and Saturation Flag
19-16: GE[3:0] - Greater than or Equal Flag

Desc: APSR contains the current stats of the condition flags from previous instruction executions.


- Interrupt Program Status Register (IPSR): bit 8 - 0
ISR_NUMBER
0 - Thread Mode
1 - Reserved
2 - NMI Non-maskable Interrupt
3 - HardFault
4 - MemManage
5 - BusFault
6 - UsageFault
7-10 - Reserved
11 - SVCall
12 - Reserved for Debug
13 - Reserved
14 - PendSV
15 - SysTick
16 - IRQ0
17 - IRQ1
...
35 - IRQ19
...
255 - IRQ239

Desc: IPSR contains the execution type of the current Interrupt Service Routine (ISR).


- Execution Program Status Register (EPSR): bit 26, 25, 24, 15 - 10
26-25: ICI/IT - Interruptible-continuable instruction bits / IT insruction
24: T - Thumb state bit
15-10: ICI/IT - Interruptible-continuable instruction bits / IT insruction

Desc: EPSR contains the Thumb state bit, and the execution state bits for either the 
If-Then (IT) instruction.
Interruptible-Continuable Instruction (ICI) field for an interrupted load multiple or store multiple instruction.

A, I, EPSR, these registers are mutually exclusive bit fields in the 32-bit PSR.

Example)
1. xPSR=20000000
0010 0000 0000 0000 0000 0000 0000 0000
bit 29 C is 1.


2. xPSR=81000000
1000 0001 0000 0000 0000 0000 0000 0000
bit 31 N and bit 24 T are 1.


3. xPSR=61000023
0110 0001 0000 0000 0000 0000 0010 0011
bit 30 Zero Flag
bit 29 Carry or borrow flag
bit 24 T
bit 8 - 0: 0x23 35(dec) - 16 = 19 - IRQ number 19 - FDCAN1_IT0_IRQn

4.  A1000000
1010 0001 0000 0000 0000 0000 0000 0000
bit 31 N and bit 24 T are 1.
bit 29 C is 1.

BFSR : 00000082
UFSR : 00000000
DFSR : 00000000
AFSR : 00000000
BFAR : 000C0203


