/*
  Demonstrates the use of an IRF740 N-Channel MOSFET to switch a
  3W High Intensity LED with a microcontroller.
  https://www.addicore.com/3W-White-LED-on-Heat-Sink-p/155.htm
  https://www.addicore.com/IRF740-N-Channel-Power-MOSFET-p/162.htm
  It has been tested on a Texas Instruments MSP430F5529 LP using
  Energia and an Arduino Uno.
  
  Created by Frank Milburn, 29 May 2015
  Released into the public domain.
  
  These LEDs are very bright and use more current than a microcontroller
  can supply on it's own through a pin.  An IRF740N-Channel MOSFET is used
  here as a switch. MOSFETs have the advantage of drawing little input
  current from the microcontroller and can control large currents and 
  voltages (see datasheet).
  
  When selecting a MOSFET for this type application make sure that the
  gate threshold is less than the logic level of the MOSFET.  For
  instance, the IRF740 will operate fine at the 5V level of an Arduino
  but at the 3.3V level of a LaunchPad it will be much dimmer and a
  MOSFET with a lower threshold would be better.  
 
  Excusing the poor ASCII art, the schematic looks something like this:                                    
                                    
                                       Vin = 6V
                                          ___
    5V                                     |                      
    ___                                    Rs = 4.7 ohms                     
     |                                     |                       
  _______                                 LED                    
  |  M  |                                  |
  |  I  |                                  D
  |  C  |  Pin 9                           |
  |  R  |--------------------------- G -----   IRF740 
  |  O  |                                  |
  -------                                  S
     |                                     |
    GND --------------------------------- GND
 
  where S = Source
        G = Gate
        D = Drain
 
  In words:
  * Connect pin 9 of the microcontroller to the Gate (G) of the MOSFET
  * Connect GND of the microcontroller to Source (S) of the MOSFET
  * Connect the positive terminal of the power supply to the resistor Rs
  * Connect the other end of the resistor Rs to the Anode (+) of the LED
  * Connect the Cathode (-) of the LED to the Drain (D) of the MOSFET
  * Connect the negative terminal of the power supply to GND on the microcontroller
  
  Design Considerations:
 
  Power Supply:
  It is possible, and frequently desireable, to use a different power
  source than the microcontroller. The LED description lists the forward
  current as 700mA.  This could stress the power supply on the microcontroller.
  This example will use a separate 6V battery for Vin above.
  
  Limiting Current Resistor:
  The current through the LED should be limited to 700mA with a resistor
  (Rs above).  The voltage drop across the LED is listed as 3.2-3.6V. If
  the voltage drop across the MOSFET is ignored and 3.2V is conservatively
  used for Vled then the minimum size of the resistor can be determined by 
  the following equation:
  
  Rs = (Vin - Vled) / Iled = (6 - 3.2) / 0.7 = 4 ohms (4.7 is next std size up)
    where Vin = Voltage source (Volts)
          Vled = Voltage drop across the LED from the datasheet (Volts)
          Iled = Manufacturer's maximum rated current (Amps)
   I actually used a 10 ohm resistor because it was the smallest I had on hand
   and the LED was still very bright.  This would be about 0.28 Amps.
   
   Pin:
   Any digital pin can be used.  This circuit will work with PWM if one of
   the pins capable of PWM is selected.
 
   Note that the code that follows is the same as that in the standard
   "Hello World" blink an LED except perhaps for the pin.
*/
  
// the setup function runs once when you press reset or power the board
void setup() 
{
  pinMode(9, OUTPUT);       // initialize high powered LED as output
}

// the loop function runs over and over
void loop()
{
  digitalWrite(9, HIGH);    // turn on high intensity LED
  delay(1000);              // wait for a second
  digitalWrite(9, LOW);     // turn off high intensity LED
  delay(1000);              // wait for a second
}
