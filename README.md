Code for multiplication :
; code for multiplication of
; two numbers by repeated
; addition
; two numbers to be multiplied
; are stored in 0002H and
; 0003H, ; output is stored in 0004H
MOV B,0002H
MOV C,0003H
MVI A,00H
LOOP: ADD B DCR C
JNZ LOOP
STA 0004H
Multiplying row vector with
colum vector :
LXI H, 8500H
PUSH 8508H
Method: MOV M, A
XCHG
MOV M,B
CALL MUL
STA 8516H
INX H
XCHG
INX H
JMP Method
Matrix Multiplication :
MVI C, 002H
MVI D, 002H
8
Method2: DCR C
Method3: CALL MRC
DCR D
JNZ Method4
Method4: ORI C, 00H
JNZ Method5
Method5: LXI H, 8500H
JMP Method3
ORI C, 00H JZ
Method6: LXI H, 8508H
JMP Method3
ORI D, 00H
JZ Method7:
Method7: INX H, 8508H
MVI D, 002H ORI C, 00H
JNZ Method3
ORI C, 00H JZ Method8
Method8: HLT
FINAL CODE :
MVI C, 00
LXI H,
Method2: DCR C
Method3: CALL MRC
DCR D
JNZ Method4
Method4: ORI C, 00H
JNZ Method5
Method5: LXI H, 8500H
JMP Method3
ORI C, 00H JZ
Method6: LXI H, 8508H
JMP Method3
ORI D, 00H
JZ Method7:
Method7: INX H, 8508H
MVI D, 002H ORI C, 00H
JNZ Method3
ORI C, 00H JZ Method8
Method8: HLT
FINAL CODE :
MVI C, 00
LXI H, 8500
LOOP2: LXI D, 8600
CALL MUL
MOV B,A
INX H
INX D
INX D
CALL MUL
ADD B
CALL STORE
DCX H
DCX D
CALL MUL
MOV B,A
INX H
INX D
INX D
ADD B
CALL STORE
MOV A,C
CPI 04
JZ LOOP1
INX H
JMP LOOP2
LOOP1: HLT
MUL: LDAX D
MOV D,A
MOV H,M
DCR H
JZ LOOP3
LOOP4: ADD D
DCR H
JNZ LOOP4
LOOP3: MVI H,85
MVI D,86
RET
STORE: MVI B,87
STAX B INR C
RET
