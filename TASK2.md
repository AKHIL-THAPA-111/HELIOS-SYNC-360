# DEBUGGING USING SPIKE COMMAND
## We will use the same c file from 1st task and use the command 

        riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o akhil.o akhil.c
        
![Screenshot 2024-12-26 203431](https://github.com/user-attachments/assets/539129d3-c259-4fbe-b29b-5a179e2244b4)
 ## As we can see the  **main** starts from hexadecimal 100b0 in assembly language with a lot of commands after it.
 To start debugging we run the command 
 
         spike -d pk akhil.o 
 IN this spike is a RISC-V simulator which emulates a RISC-V processor and allows you to run programs as if they were running on a real RISC-V hardware processor. In my case the file name is akhil.o

 ## After this as the main is starting at 100b0 we use the command

          until pc 0 110b0

which means the pc will run the code until the given address in 110b0
## We the use the command 
          reg 0 a0

in my case as it starts from a0 , to see the contents we use the given register
#### NOTE : LUI stands for Load Upper Immediate. It is a type of instruction used to load a 20-bit immediate value into the upper 20 bits of a register. 

## Then we can see the contents of the reg

![Screenshot 2024-12-26 203704](https://github.com/user-attachments/assets/2c47b6ea-1fcb-42eb-801a-ff2c480ec7d5)

## After that if we press enter it will move onto next set of instruction, again to check the contents we use the command (in my case).

          reg 0 sp

#### sp stands for the stack pointer the stack is like a special memory storage where the computer keeps track of temporary data , the decimal -16 means that the content in sp got upadted to 10 in hexadecimal 
          
![Screenshot 2024-12-26 203854](https://github.com/user-attachments/assets/2c221a3b-f83b-4c43-aeee-9c3b20a49fac)

## To prove this point we enter q to quit and the run again the command :  

           spike -d pk akhil.o
but in this case we will run until the command reaches satck pointer register which in my case is 3ffffffb50 ,

            until pc 0 3ffffffb50

then we press ENTER

## Then we use the command 
      reg 0 dp

then one can notice that the value got reduced by 10 hexadecimal or by 16 in decimal

#### NOTE :  addi stands for add immediate it’s an instruction in the RISC-V assembly language that adds a constant number to a register.

![Screenshot 2024-12-26 204353](https://github.com/user-attachments/assets/2402ca75-74f8-4ee7-8a8b-4fd7ba307d56)



     

THAT WAS ALL FOR THE TASK2 😊


              
