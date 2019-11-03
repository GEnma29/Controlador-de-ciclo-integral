```c



#pragma config FOSC = XT        // Oscillator Selection bits (XT oscillator)
#pragma config WDTE = OFF       // Watchdog Timer Enable bit (WDT disabled)
#pragma config PWRTE = OFF      // Power-up Timer Enable bit (PWRT disabled)
#pragma config CP = OFF         // FLASH Program Memory Code Protection bits (Code protection off)
#pragma config BOREN = OFF      // Brown-out Reset Enable bit (BOR disabled)
#pragma config LVP = OFF        // Low Voltage In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for programming)
#pragma config CPD = OFF        // Data EE Memory Code Protection (Code Protection off)
#pragma config WRT = ON          // FLASH Program Memory Write Enable (Unprotected program memory may be written to by EECON control)

#include <xc.h>
#define _XTAL_FREQ 4000000
unsigned int n,k;
unsigned int  m,a;
void PIC_Configuracion_Inicial();

void main(void) {

    PIC_Configuracion_Inicial();
    a = 0;
    int b = 0;
    int i;
    int j;
    int x = 0;

    __delay_us(1000);

    while (1) {
        if(a == n){
            PORTBbits.RB4 = 0;
            }
        while (a < n) {
        if ((PORTDbits.RD0 == 1) && (a < n)) {
            PORTBbits.RB0 = 1; // pulso
            __delay_us(50);
            PORTBbits.RB0 = 0;
            a = x++;
        }
            }

            
    }
}

void __interrupt () my_isr_routine (void) {
 if(RBIF) //Si hay cambio de estado en PORTB
 {
     while(m < 20 ){
         if(PORTDbits.RD0 == 1){
             PORTBbits.RB0 = 0;
             m=m++;
             a = 0;
             } 
         }
    
 RBIF = 0; //Desactivar bandera...
 }
}


void PIC_Configuracion_Inicial() {

    TRISD = 1;
    TRISA = 0;
    ADCON0 = 0b00000000;
    TRISB = 0B11110000;
    PORTB = 0;
    PORTBbits.RB4 = 1;
    RBIF = 0; // Bandera de Interrupciones del RB4 al RB7 a 0
    INTCON = 0; // Limpia Registro INICON
   INTCONbits.RBIE = 1; //Habilitar interrupciones de puerto B.
   INTCONbits.RBIF = 0; //Bandera desactivada.
   INTCONbits.GIE = 1; //Interrupciones globales habilitadas.
}

```
