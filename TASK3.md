# RISC-V INSTRUCTION TYPES
## The RISC-V has various types of instruction formats which we can be grouped in two types : 
#### BASE INSTRUCTION FORMATS :
In the base RV32I ISA , there are four main instruction formats mainly the R-Type , I - type , S - type and U - type .
All are 32 bits long.The base ISA has IALIGN=32, meaning that instructions must be aligned on a four-byte boundary in memory.
If there is an misalignment an exception is taken such it branches or there will occur an unconditional jump , techincally *instruction-address-misaligned exception*.

![image](https://github.com/user-attachments/assets/ba58b088-d2c8-4fe9-bf97-87fd1d983aef)

**As in the image there are source resistors termed as **rs** *(These are the registers that hold the input values for a particular operation or instruction)*.  and destination resisters **rd** *(This register holds the result of the operation performed by the instruction.)* . The **funct3** is a 3-bit field *(field refers to a specific segment or portion of an instruction that contains particular information necessary for the processor to execute that instruction)*  and **funct7** a 7-bit field  and opcode *(an instruction that specifies the operation to be done by the processor)* and imm[x:y] means that the immediate value *(a constant data value embedded directly within an instruction)* is derived from the bits in the instruction ranging from position y to position x.
The RISC-V ISA keeps the source (rs1 and rs2) and destination (rd) registers at the same position in all
formats to simplify decoding.**

####  Immediate Encoding Variants 
There are a further two variants of the instruction formats   based on the handling of immediates namely B-Type and J-Type


![image](https://github.com/user-attachments/assets/fda21dc2-3feb-49a3-9fd8-9af8128fd977)


![image](https://github.com/user-attachments/assets/b624e997-6112-40cd-9702-5d9823d0a4b7)

____________________________________________________________________________________________________________________________

### **R-TYPE** : 

![image](https://github.com/user-attachments/assets/5e7a9d07-6329-4bef-921f-fb0dae0cbe1f)


the R-Type is an instruction format in the RISC-V architecture to perform arithmetic and logical operations using registers.
As from above

opcode(6-0)  identifies the operation to be performed (add,subtract,etc) ,

rd(11-7) is the destination register  where the result is stored ,

funct3(14-12) specifies the operation within the opcode category ,

rs1(19-15) indicates the first source register that contains one of the operands for the operation ,

rs2(24-20) indicates the 2nd source register that contains the other operand for the operation ,

funct7(31-25) provides the operation, aloowing for more variations of instructions that share the same opcode and funct3 values.



### **I-Type** :

![image](https://github.com/user-attachments/assets/9e4042df-ee63-4428-b8ba-95d41067dc30)

the  I-Type instruction format in the RISC-V architecture is designed for operations that involve immediate values and registers. 

opcode(6-0)  identifies the operation to be performed (load,add immediate) ,

rd(11-7) is the destination register  where the result is stored ,

funct3(14-12) specifies the operation within the opcode category ,

rs1(19-15) indicates the first source register that contains one of the operands for the operation ,

imm[11:0] (31:20) is a 12 bit immediate value which is a constant directly embedded in the instruction.

### **S-Type** :

![image](https://github.com/user-attachments/assets/0a634506-04d6-48f3-a015-90e53db5c9fd)

the S-Type instruction format in the RISC-V architecture is specifically designed for store operations, which involve writing data from registers to memory.

opcode(6-0) identifies the operation to be performed (SW - for store word) ,

imm[4:0](11-7) these 5 bits of the immediate value specifies an offset to be added to the address in rs1 ,

funct3(14-12) specifies the type of storage operation ,

rs1 

