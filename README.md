Experiment:

18.Write an assembly language program in 8051 to search for a given number in an array of N elements and display whether the number is found or not found.
Aim:

To write an assembly language program to search a given number in an array of numbers stored in memory using 8051 microcontroller and to display the result through Port 1.

If the number is found → P1 = FFH

If not found → P1 = 00H



---

Algorithm:

1. Start the program.


2. Initialize the data pointer register R0 with the starting address of the array (30H).


3. Load R1 with the total number of elements in the array.


4. Load the accumulator (A) with the number to be searched (NUM).


5. Clear the carry flag (used as “found” flag).


6. Compare each array element with the number to be searched:

If equal → set carry flag and jump to the end.

If not equal → increment R0 to point to the next element.



7. Repeat steps until all elements are checked.


8. If carry flag is set → output FFH on Port 1 (found).


9. If carry flag is not set → output 00H on Port 1 (not found).


10. Stop the program.

Program:
```
ORG 0H   
MOV R0, #30H      ; Start address of array
MOV R1, #N        ; Number of elements
MOV A, #NUM       ; Number to search
CLR C             ; Clear carry (flag)

SEARCH:
    MOV A, @R0    
    CJNE A, #NUM, NEXT  
    SETB C         
    SJMP END_SEARCH

NEXT:
    INC R0         
    DJNZ R1, SEARCH 

END_SEARCH:
    JNC NOT_FOUND  

FOUND:
    MOV P1, #0FFH  
    SJMP $          

NOT_FOUND:
    MOV P1, #00H   
    SJMP $          

ARRAY: DB 11,22,33,44,55  
N EQU 5                    
NUM EQU 77                 

END


```

Output:
<img width="929" height="594" alt="Screenshot 2025-10-25 071351" src="https://github.com/user-attachments/assets/ac1f01eb-bcfb-44ce-9613-cd32cdcb77dc" />

Result:

The program was executed successfully in Keil software.

Since the number 77 is not found in the array,
Port 1 output = 00H
(P1 = 0x00) → Number not found.# skill-assesment1
