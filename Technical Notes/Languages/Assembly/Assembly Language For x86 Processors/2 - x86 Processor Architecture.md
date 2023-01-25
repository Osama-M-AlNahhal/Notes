
# General Concepts
## Basic Microcomputer Design
| component           | info                                                                                                                                           |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| CPU                 | Contains<br>1. Clock: for syncronization. (basic unit of time for machine instructions is machine(clock) cycles.<br>2. Control Unit (CU): coordinates the execution of instructions.<br>3. ALU : performs operations. |
| Memory Storage Unit | where the data resides before it's copied into the CPU to be executed.                                                                         |
| I/O Devices         | varrying, not our focus.                                                                                                                       |
| Bus                 | Group of parallel wires that transfer data.<br>1. Address bus.<br>2. Control bus.<br>3. Data bus.<br>4. I/O bus.                                                                                                                                               |


## Instruction Execution Cycle
*predefined sequence of steps for executing a machine instructions*

1. **Fetch** the instruction from the *instruction queue*, and increment *EIP*.
2. **Decode** the instruction.
3. **Fetch** the Operands (if there's any), which might involve address calculations.
4. **Execute** the instruction, and update the *status flags*.
5. **Store Results** in an operand (if the instruction says so).

## Reading From Memory
*Much slower than reading from Registers*

**Why is it much slower?**
**A:** because it involves 4 steps:
	1. place the address on the address bus.
	2. Assert the RD (Read) pin.
	3. Wait for response.
	4. Copy data from data bus to operand.

**Caching:**
- Cache hits vs misses.
- Cache memory is faster than Static (conventional/normal) memory.

## Loading and Executing a Program
*`Program Loader` loads instructions from desk into memory before execution*

1. OS looks for file name in current desk directory.
2. if found -> get size and address.
3. OS finds an empty place in memory and loads the file into it.
4. OS begins execution from the program's entry point (program is now called `Process`).
5. Process continues to run on its own (OS keeps track of it, and deletes it from memory when it's done).


---

# 32-bit x86 Processors

## Modes of Operation
| Mode                   | Info                                                                                                                                   |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Protected Mode         | - nativ state of processor.<br>- programs are assigned `segments` of memory.<br>- all features are available only inside your segment.<br>- Prevents programs from directly accessing system Hardware. |
| Virtual-8086 Mode      | - moden OS runs multiple programs concurrently on this mode.<br>- OS runs in Protected mode.<br>- each program runs in Virtual-8086 mode simulating a Real-address mode computer with 1Mb memory                                                                          |
| Real-Address Mode      |               - implements the programming environment of an early Intel Processor.<br>- extra features: ability to switch to other modes.<br>- programs can access ANY memory address, including those linked with system hardware.                                                                                                                          |
| System-Management Mode | - Allows OS to implement:<br>1. Power Management.<br>2. System Security.                                                                                                                                       |

## Basic Execution Environment
### Address
- 32-bit Protected Mode : Up to 4GB memory
	- P6+ Processors : 64GB (using *Extended Physical Addressing*).
- 16-bit Real-Address Mode : 1Mb only.
- Processor in Protected Mode and running multiple programs in Virtual-8086 mode : 1Mb each

### Registers
- 8 General Purpose (32 bits).
- 6 Segment (16 bits) : 
	- Real-address mode : base addresses of segments.
	- Protected mode : pointers to descriptor tables (code/instructions, data/variables, stack segment).
- EFLAGS (32 bits) :
	- Control Flags & Status Flags
- EIP (32 bits).


- 8 MMX (64 bits) :
	- for multimedia and communications
	- support SIMD (Single Instruction, Multiple Data) which operate in parallel on the MMX registers.
	- These are the same registers used for floating-point arithmetic, just given a different aliase and task.
- 8 XMM (128 bits) :
	- for streaming SIMD extensions to the instruction set.

**Floating Point Unit (*FPU*):**
- 8 Data (80 bits).
- Opcode (80 bits).
- FPU Instruction Pointer (48 bits).
- FPU Data Pointer (48 bits).
- Tag (16 bits).
- Control (16 bits).
- Status (16 bits).

### Flags
*first 8 bits (right to left)*

| #   | Flag           | Use                                |
| --- | -------------- | ---------------------------------- |
| 0   | Carry          | Unsigned - too large to fit in dst |
| 1   | 1              |                                    |
| 2   | Parity         |             Least significant byte has an even number of 1s                       |
| 3   | 0              |                                    |
| 4   | Auxilary Carry |            carry from bit 3 to 4 (in 8-bit operand)                        |
| 5   | 0              |                                    |
| 6   | Zero           |                                    result = 0|
| 7   | Sign           |             result = negative                       |
| 11  | Overflow               |                      Signed - too large to fit in dst              |


---

# 64-bit x86-64 Processors
## Operation Modes
1. Compatibility Mode : allows 16bit and 32bit applications to run.
2. 64-bit Mode.

## Basic Execution Environment
| difference                | 32-bit                              | 64-bit                              |
| ------------------------- | ----------------------------------- | ----------------------------------- |
| General Purpose Registers | 8                                   | 16                                  |
| Floating-Point Register   | 8                                   | 8                                   |
| RFLAG                     | 32-bit                              | 64-bit (only the lower 32 are used) |
| Instruction Pointer       | EIP = 32 bit                        | RIP = 64 bit                        |
| MMX                       | 8 (64 bit, alias for FPU registers) | 8 (64 bit, dedicated)               |
| XMM                       | 8 (128 bit)                         | 16 (128-bit, dedicated)                                    |

## Important Details
1. in 64-bit mode : can't access a high byte and a new low byte (ex: DIL) in a single instruction.
2. status flags are the same as 32-bit mode.

----

# Components of a Typical x86 Computer
## Motherboard
## Memory
| Type     | Info                                                                                                   |
| -------- | ------------------------------------------------------------------------------------------------------ |
| ROM      | perminent, can't be erased                                                                             |
| EPROM    | can be slowly erased with UV-light and reprogrammed                                                    |
| DRAM     | must be refreshed every millisecond<br>ECC Memory                                                      |
| SRAM     | cache ram, expensive but doesn't need refreshing                                                       |
| VRAM     | for video data<br>dual ported (one writes data to screen, the other refreshes the screen continuously) |
| CMOS RAM | stores system setup info<br>refreshed by the battery so doesn't lose data on poweroff                                                                                                       |

---

# Input/Output System