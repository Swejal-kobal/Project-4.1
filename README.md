# Project-4.1

FILL.ASM

(RESTART)
@SCREEN
D=A
@0
M=D	//PUT SCREEN START LOCATION IN RAM0

///////////////////////////
(KBDCHECK)

@KBD
D=M
@BLACK
D;JGT	//JUMP IF ANY KBD KEYS ARE PRESSED
@WHITE
D;JEQ	//ELSE JUMP TO WHITEN

@KBDCHECK
0;JMP
///////////////////////////
(BLACK)
@1
M=-1	//WHAT TO FILL SCREEN WITH (-1=11111111111111)
@CHANGE
0;JMP

(WHITE)
@1
M=0	//WHAT TO FILL SCREEN WITH
@CHANGE
0;JMP
//////////////////////////
(CHANGE)
@1	//CHECK WHAT TO FILL SCREEN WITH
D=M	//D CONTAINS BLACK OR WHITE

@0
A=M	//GET ADRESS OF SCREEN PIXEL TO FILL
M=D	//FILL IT

@0
D=M+1	//INC TO NEXT PIXEL
@KBD
D=A-D	//KBD-SCREEN=A

@0
M=M+1	//INC TO NEXT PIXEL
A=M

@CHANGE
D;JGT	//IF A=0 EXIT AS THE WHOLE SCREEN IS BLACK
/////////////////////////
@RESTART
0;JMP


![image](https://github.com/user-attachments/assets/227553cf-26a9-4dcf-8fb9-05e57090cf00)

![image](https://github.com/user-attachments/assets/3bd65a46-3f27-4c58-9320-d3eed1dc48d7)

![image](https://github.com/user-attachments/assets/f063b465-34b1-4ad7-9c55-80dbf8eba41c)

MULT.ASM

@2	//GO TO FINAL ANSWER BOX
M=0	//ZERO ANS BOX

@0
D=M
@END
D;JEQ	//IF ONE PRODUCT IS ZERO

@1
D=M
@END
D;JEQ	//IF ONE PRODUCT IS ZERO

@0	//NOT NECESSARY
D=M	//
@3	//
M=D	//ONLY TO KEEP THE NUMBERS BEING MUTLIPLED


(LOOP)
@1	//GET 2ND NUM
D=M	//D HAS 2ND NUM

@2	//GO TO FINAL ANSWER BOX
M=D+M	//RAM[2] NOW HAS 2ND NUMBER + ITS PREVIOUS VALUE

@3	//GET 1ST NUM
M=M-1	//1ST NUM-1

D=M	//IDK WHY D NEEDS TO =M?
@LOOP	//WHERE TO JUMP TO
D;JGT	//JUMP		    (WHY CANT THIS BE M;JGT?)


(END)
@END
0;JMP	//FOREVER LOOP

![image](https://github.com/user-attachments/assets/b054881a-5bcb-43e1-87e7-6f50d87c8667)

![image](https://github.com/user-attachments/assets/f282dd40-9f39-4326-ad7e-e239acf873d2)

![image](https://github.com/user-attachments/assets/a4ddd374-c944-4a3c-98c8-a7a1f535fd5a)









