# RISC-V INSTRUCTION TYPES
## The RISC-V has various types of instruction formats which we can be grouped in two types : 
### BASE INSTRUCTION FORMATS :
In the base RV32I ISA , there are four main instruction formats mainly the R-Type , I - type , S - type and U - type .
All are 32 bits long.The base ISA has IALIGN=32, meaning that instructions must be aligned on a four-byte boundary in memory.
If there is an misalignment an exception is taken such it branches or there will occur an unconditional jump , techincally *instruction-address-misaligned exception*.

![image](https://github.com/user-attachments/assets/ba58b088-d2c8-4fe9-bf97-87fd1d983aef)

**As in the image there are source resistors termed as **rs** *(These are the registers that hold the input values for a particular operation or instruction)*.  and destination resisters **rd** *(This register holds the result of the operation performed by the instruction.)* . The **funct3** is a 3-bit field *(field refers to a specific segment or portion of an instruction that contains particular information necessary for the processor to execute that instruction)*  and **funct7** a 7-bit field  and opcode *(an instruction that specifies the operation to be done by the processor)***

The RISC-V ISA keeps the source (rs1 and rs2) and destination (rd) registers at the same position in all
formats to simplify decoding. 

###  Immediate Encoding Variants 
There are a further two variants of the instruction formats   based on the handling of immediates namely B-Type and J-Type
![image](https://github.com/user-attachments/assets/fda21dc2-3feb-49a3-9fd8-9af8128fd977)
![image](https://github.com/user-attachments/assets/b624e997-6112-40cd-9702-5d9823d0a4b7)

