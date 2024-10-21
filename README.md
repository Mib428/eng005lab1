#include <msp430.h>
#define RED_LED BIT0 // P1.0
#define BUTTON1 BIT1 //push button P4.1
void main(void)

{
WDTCTL = WDTPW | WDTHOLD;
P1OUT &= ~BIT0;
P1DIR |= BIT0;

P4DIR &= ~BIT1;
P4REN |= BIT1;
P4OUT |= BIT1;

PM5CTLO &= ~LOCKLPM5;

int count = 0;
while(1) {
        if((P4IN & BUTTON1) == 0x00) {
        _delay_cycles(5000);
        if((P4IN & BUTTON1) == 0x00) {
                P1OUT ^=RED_LED;
            } while((P4IN & BUTTON1) == 0x00)
        }
        
}
}
