

; PIC16F877A Configuration Bit Settings

; Assembly source line config statements

    ; CONFIG
      CONFIG  FOSC = HS             ; Oscillator Selection bits (HS oscillator)
      CONFIG  WDTE = OFF            ; Watchdog Timer Enable bit (WDT disabled)
      CONFIG  PWRTE = OFF           ; Power-up Timer Enable bit (PWRT disabled)
      CONFIG  BOREN = OFF           ; Brown-out Reset Enable bit (BOR disabled)
      CONFIG  LVP = OFF             ; Low-Voltage (Single-Supply) In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for programming)
      CONFIG  CPD = OFF             ; Data EEPROM Memory Code Protection bit (Data EEPROM code protection off)
      CONFIG  WRT = OFF             ; Flash Program Memory Write Enable bits (Write protection off; all program memory may be written to by EECON control)
      CONFIG  CP = OFF              ; Flash Program Memory Code Protection bit (Code protection off)

   // config statements should precede project file includes.
    #include <xc.inc>


;---------Initializing-----------
  
    PSECT start, CLASS = CODE, DELTA=2
    start:
    
    delay1 equ 0x20
    delay2 equ 0x21
    
    PAGESEL MAIN
    GOTO MAIN
    PSECT CODE, DELTA=2
 
 ;----------END Initializing--------
 
     //Copying values to to delay vairables
     MOVLW 0x0F
     MOVWF delay1
     MOVWF delay2

     //Enabling PORTC pins as outputs

     BSF STATUS,5
     BCF TRISC,1 //DIN - DataIn
     BCF TRISC,2 //CS - ChipSelect
     BCF TRISC,3 //CLK - Clock
     BCF STATUS,5
 
 
    MAIN:
         //Printing of EH21498756 instead of EN21498756
        //Since N or n is not available

        //Initialization of Registers
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        ;=============================================================================;     

        //Decode Mode

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Decode Mode Register
        //1001

        //D11
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Decoding Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;=============================================================================;  
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Intensity

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Intensity Mode Register
        //1010

        //D11
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Intensity Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;=============================================================================;  
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Scan Limit

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Scan Limit Mode Register
        //1011

        //D11
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Scan Limit Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;=============================================================================;  
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

         //Shutdown

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Shutdown Mode Register
        //1011

        //D11
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Shutdown Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Display Test

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Display Test Mode Register
        //1011

        //D11
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Display Test Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start


       ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 01 - E

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 02 - H

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 03 - 2

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //0010 - 2

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 04 - 1

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001 

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //0001 - 1

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 05 - 4

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //0100

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 06 - 9

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //1001 - 9

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 07 - 8

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //1000 - 8

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 08 - 7

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //0111 - 7

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 09 - 5

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //0101 - 5

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        ;==============================================================================;
        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
        BCF PORTC, 2 //ChipSelect Disable (Enable Data Input)

        //Digit 0 - Letter 10 - 6

        //Dont Care Terms 
        //D15 - D12

        //D15
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D14
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D13
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D12
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Accessing Digit0 Register
        //0001

        //D11
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D10
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D09
        BCF PORTC,1 //DIN Low
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D08
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        //Digit0 Data 
        //D07 - D00
        //0110 - 6

        //D07
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D06
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D05
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D04
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D03
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D02
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D01
        BSF PORTC,1 //DIN High
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start
        //D00
        BCF PORTC,1 //DIN LOW
        BSF PORTC,3 //CLK High
        CALL delay_start
        BCF PORTC,3 //CLK Low
        CALL delay_start

        BSF PORTC, 2 //ChipSelect Enable (Disable Data Input)
    
    GOTO MAIN
    
    delay_start:
      DECFSZ delay1 //reduced by 1 (5-1 = 4)
      goto delay_start //when delay is 0, this will be skipped
      MOVLW 0xFF // copy 5 to W register
      MOVWF delay1 // copy W to delay1

      DECFSZ delay2 //reduced by 1 (5-1 = 4)
      goto delay_start //when delay is 0, this will be skipped
      MOVLW 0x5F // copy 5 to W register
      MOVWF delay2 // copy W to delay1

    RETURN



