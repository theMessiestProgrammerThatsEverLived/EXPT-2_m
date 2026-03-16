AIM:-

To write an assembly language program in 8086 to rotate the motor at different speeds.

APPARATUS REQUIRED:-

|S.no|      ITEM            |       SPECIFICATION            |  QUANTITY       |  
|----|----------------------|--------------------------------|-----------------|
| 1. | MICROPROCESSOR KIT   |   8086                         |    1            |
| 2. | POWER SUPPLY         |  +5 V DC, +12 V DC             |    1            |
| 3. |Stepper motor         |                                |                 |
|    |  interface           |              _                 |    1            |
|    |     board            |                                |                 |              
| 4. | Stepper Motor        |             -                  |    1            |
 
THEORY :-

A motor in which the rotor is able to assume only discrete stationary angular positions is a stepper motor. The rotary motion occurs in a stepwise manner from one equilibrium position to the next.

Two-phase scheme: Any two adjacent stator windings are energized. There are two magnetic fields active in quadrature and none of the rotor pole faces can be in direct alignment with the stator poles. A partial but symmetric alignment of the rotor poles is of course possible.

ALGORITHM :-

For running the stepper motor in clockwise and anticlockwise directions:

1.Get the first data from the lookup table.

2.Initialize the counter and move data into the accumulator.

3.Drive the stepper motor circuitry and introduce delay.

4.Decrement the counter. If not zero, repeat from step (iii).

5.Repeat the above procedure both for backward and forward directions.

SWITCHING SEQUENCE OF STEPPER MOTOR:-

|MEMORY LOCATION     | A1   | A2   | B1   | B2    | HEX CODE  |
|--------------------|------|------|------|-------|-----------|
| 1200               |   1  |  0   |  0   |   0   |    09H    |
| 1201               |   0  |   1  |  0   |   1   |    05H    | 
| 1202               |   0  |   1  |  1   |   0   |    06H    |
| 1203               |   1  |   0  |   1  |   0   |    0AH    |


PROGRAM:-

; Stepper Motor Interfacing Program in 8086 Assembly

START:   MOV DI, 1200H        ; Initialize memory location to store array
         MOV CX, 0004H        ; Initialize array size

DOWN1:   MOV AL, [DI]         ; Copy the first data into AL
         OUT C0, AL           ; Send it through port address

         MOV DX, 1010H        ; Delay subroutine
L1:      DEC DX
         JNZ L1

         INC DI               ; Go to next memory location
         LOOP DOWN1           ; Repeat until all data is sent

         JMP START            ; Continuous rotation

         HLT                  ; Stop

DATA:    DB 09H, 05H, 06H, 0AH ; Array of data

OUTPUT OF THE RESULT:-

<img width="916" height="1465" alt="image" src="https://github.com/user-attachments/assets/f297454b-cb52-4a97-93a5-021a80e07632" />

<img width="1165" height="1600" alt="image" src="https://github.com/user-attachments/assets/fb4ebaac-c96b-4971-8304-961ad8dadbfc" />

RESULT:-

Thus, the assembly language program for rotating the stepper motor in both clockwise and anticlockwise directions was written and verified.








