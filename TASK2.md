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


## Next we will make a c code which will do the fatorial of number 5
### The code is : 

        #include <stdio.h>

        int main() {
            int x = 5;  // Number to compute the factorial
            int i;
            int factorial = 1;  // Initialize factorial to 1

        for(i = 1; i <= x; i++) {
        factorial *= i;  // Multiply factorial by i in each iteration
    }

        printf("Factorial of %d is %d\n", x, factorial);
        return 0;
     }

### We will run the debug the code using gcc and spike both (*The name of file is fact.c*)

#### First we will perform gcc using the command

       gcc fact.c

#### Then use the following command to get output

       ./a.out

       
![Screenshot 2024-12-27 150804](https://github.com/user-attachments/assets/1578b8a9-e942-431b-b5a3-59261af31f06)



### Next we will make an riscv file of the same code using the command 

        riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o fact.o fact.c
and use the command 

           riscv64-unknown-elf-objdump -d fact.o
to view the file and its address

![Screenshot 2024-12-27 151218](https://github.com/user-attachments/assets/d365a9c0-4c0f-4602-b7c1-95b4233f3525)


### After that we will compile the code using spike command as below

        spike -d pk fact.o

### Since the main starts from the hexadecimal 10184 we use the command 

        until pc 0 10184

and compile it , and it should give us the output ater it 

![Screenshot 2024-12-27 151342](https://github.com/user-attachments/assets/ffc0e6ca-4c0f-4e14-b323-d4e521bd866e)

Thus , we have successfully compiled our code using gcc and spike simmulation

THAT WAS ALL FOR THE TASK2 😊


              
