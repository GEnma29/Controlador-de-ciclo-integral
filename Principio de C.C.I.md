# Controlador-de-ciclo-integral
Controlador de ciclo integral con PIC16F877
```
### Main

```c
#include <xc.h>
#pragma config FOSC = XT        // Oscillator Selection bits (XT oscillator)
#pragma config WDTE = OFF       // Watchdog Timer Enable bit (WDT disabled)
#pragma config PWRTE = OFF      // Power-up Timer Enable bit (PWRT disabled)
#pragma config CP = OFF         // FLASH Program Memory Code Protection bits (Code protection off)
#pragma config BOREN = OFF      // Brown-out Reset Enable bit (BOR disabled)
#pragma config LVP = OFF        // Low Voltage In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for programming)
#pragma config CPD = OFF        // Data EE Memory Code Protection (Code Protection off)
#pragma config WRT = ON         // FLASH Program Memory Write Enable (Unprotected program memory may be written to by EECON control)

#define _XTAL_FREQ 4000000

void main(){
    int Cont = 0;
    int ciclos =0;
    int n = 0;
    int n_1,n_2,n_4;
    char E = 0;
    int i = 0;
    TRISA = 1;
    TRISB = 0;
    TRISC = 1;
    if(PORTCbits.RC0 == 1){
        E = 1;
    }
    if(PORTCbits.RC1 == 1){
        E = 2;
    }
    if(PORTCbits.RC2 == 1){
        E = 3;
    }
   

    switch (E) {
        case '1':
            if(PORTAbits.RA2 == 1){
                cont = cont++;
                __delay_us(200);
                for(n = 100; n < 1; n - cont){
                   PORTBbits.RB2 == 1;
                   __delay_us(200);
                }
            }
                E = ' ';
            break;
            
         case '2':
            if(PORTAbits.RA2 == 1){
                cont = cont++;
                __delay_us(200);
                for(n = 100; n < 1; n - cont){
                   PORTBbits.RB2 == 1;
                   __delay_us(200);
                }
            }
                E = ' ';
            break;
            
        case '3':
            if(PORTAbits.RA2 == 1){
                cont = cont++;
                __delay_us(200);
                for(n = 100; n < 1; n - cont){
                   PORTBbits.RB2 == 1;
                   __delay_us(200);
                }
            }
                E = ' ';
            break;
    }
   

   
   



}

```
