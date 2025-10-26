# skill-assesment1

Write an assembly language program in 8051 to search for a given number in an array of N elements and display whether the number is found or not found.

Aim

To write an assembly language program in 8051 to search for a given number in an array and store the result in memory.

Algorithm

Start the program at address 0000H.

Load the starting address of the array (30H) into R0.

Load the array size (number of elements) into R1.

Load the number to be searched (07H).

Compare each element in the array with the given number.

If a match is found → store 0FFH in address 40H (means FOUND).

If no match after checking all elements → store 00H in address 40H (means NOT FOUND).

Stop the program.

PROGRAM:
```
ORG 0000H

ARRAY_ADDR     EQU 30H      
ARRAY_SIZE     EQU 08H       
NUMBER_TO_FIND EQU 07H   
RESULT_ADDR    EQU 40H     

MAIN:
    MOV R0, #ARRAY_ADDR     
    MOV R1, #ARRAY_SIZE      

SEARCH_LOOP:
    MOV A, @R0               
    CJNE A, #NUMBER_TO_FIND, NEXT  

    MOV A, #0FFH             
    MOV 40H, A            
    SJMP DONE                
NEXT:
    INC R0                  
    DJNZ R1, SEARCH_LOOP     


    MOV A, #00H              
    MOV 40H, A

DONE:
    SJMP $

END
```
output:

<img width="1037" height="758" alt="Screenshot 2025-10-25 161600" src="https://github.com/user-attachments/assets/8e100df4-ea23-46b6-9a65-c4631b82b29e" />



Result:

The assembly language program was executed successfully.
When the number 07H was searched in the given array
(01H, 02H, 03H, 04H, 05H, 06H, 07H, 08H),

the result stored at memory location 40H = FFH,
which indicates that the number is FOUND in the array. 
