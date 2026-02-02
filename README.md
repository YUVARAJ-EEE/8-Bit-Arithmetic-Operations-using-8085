## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4300H ; Load first number from memory into A
MOV B, A  ; Move to register B
LDA 4301H ; Load second number from memory into A
ADD B     ; Add B to A
STA 4400H ; Store sum in memory loction 4300H
JC STORE_CARRY ; If carry is set, jump to STORE_CARRY
HLT       ; Halt the program

STORE_CARRY: MVI A, 01H;
MVI A, 01H ; Load carry value
STA 4401H ; Store carry in memory location 4301H
HLT       ; Halt the program
```
### Verification:
![WhatsApp Image 2026-02-02 at 8 03 19 PM](https://github.com/user-attachments/assets/31a253b2-7c43-41a2-8346-0dd233a8af1b)
![WhatsApp Image 2026-02-02 at 8 03 33 PM](https://github.com/user-attachments/assets/0ed22c0f-5f77-45c8-8a4d-7bf64171d11b)


### Output:
<img width="1915" height="898" alt="Screenshot 2026-02-02 123431" src="https://github.com/user-attachments/assets/67ee7db0-07e4-4f76-b8f9-9abf8abb9b18" />
<img width="1904" height="888" alt="Screenshot 2026-02-02 123513" src="https://github.com/user-attachments/assets/a585e9c8-c52f-40a3-9a21-1cb96f8ca758" />



### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
SWAP:
MOV B,A
MOV A,C
SUB B
STA 4300H
HLT
```
### Verification:
![WhatsApp Image 2026-02-02 at 8 06 42 PM](https://github.com/user-attachments/assets/e3192a2b-d72e-46be-b189-feadea4641b4)
![WhatsApp Image 2026-02-02 at 8 06 42 PM (1)](https://github.com/user-attachments/assets/d687ef5f-418b-44eb-9576-245cd4843a2a)


### Output:
<img width="1894" height="830" alt="Screenshot 2026-02-02 174704" src="https://github.com/user-attachments/assets/4baac222-552e-4163-87fc-3a87b9ee54ef" />
<img width="1888" height="827" alt="Screenshot 2026-02-02 174739" src="https://github.com/user-attachments/assets/41ec479c-6dba-4a4e-b79c-d7df5c719794" />


### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP:ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```
### Verification:
![WhatsApp Image 2026-02-02 at 8 11 41 PM](https://github.com/user-attachments/assets/ca73bdf3-9d51-4ffd-a9cf-c269a2121ff5)
![WhatsApp Image 2026-02-02 at 8 11 42 PM](https://github.com/user-attachments/assets/423fe44f-20d8-49d4-9e94-570613dc0a9b)

### Output:
<img width="1898" height="829" alt="Screenshot 2026-02-02 191650" src="https://github.com/user-attachments/assets/b970668b-06e2-4b50-adf1-de6d92158ef5" />
<img width="1899" height="825" alt="Screenshot 2026-02-02 191251" src="https://github.com/user-attachments/assets/d2bd3c21-66f8-482e-b3ee-de10a30af86f" />

### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: MOV A,C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END: MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```
### Verification:
![WhatsApp Image 2026-02-02 at 8 16 19 PM](https://github.com/user-attachments/assets/06f40dff-3c1b-4d74-8cf0-f26398883d8e)
![WhatsApp Image 2026-02-02 at 8 16 20 PM](https://github.com/user-attachments/assets/38667ad8-58ed-4084-b838-5550b0c487fe)
![WhatsApp Image 2026-02-02 at 8 16 20 PM (1)](https://github.com/user-attachments/assets/bef4e8d8-acee-4793-a2c8-e09b069b6dcc)


### Output:
<img width="1881" height="825" alt="Screenshot 2026-02-02 192324" src="https://github.com/user-attachments/assets/4443ad84-d13c-4cde-b0ac-d828d82715d7" />
<img width="1880" height="825" alt="Screenshot 2026-02-02 192343" src="https://github.com/user-attachments/assets/e17d040e-5dfa-43c3-bbd1-96b2e4cd5eaa" />

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

