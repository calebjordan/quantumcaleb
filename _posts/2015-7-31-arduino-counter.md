---
layout: post
title: Arduino Counter
tag: Software
---


Development of an Arduino based counter for use with a Josephson Photomultiplier. 

# Background

For JPM Experiments, we need to be able to count switching events. While applying a current bias pulse through the JPM, we should see a voltage develop accros the device if it is in its resistive (switched) state. This voltage is amplified through an SRS preamp (usually around x1e3, with heavy filtering over 30kHz). We need to be able to discriminate between the voltage that we are supplying the JPM, and the voltage that is a result of a switched junction. The outcome of this discriminator should be a presence or absence of a voltage pulse. This pulse is then fed to an Arduino for acquisition.

# Version 1

The first iteration of this device is a simple discriminator circuit, an Arduino's onboard counter, and a fiber optic connection between the two to avoid a hard electrical connection between the Arduino and the junction. Using a direct connection led to many blown junctions during the first few experiments. 

## Circuit v1

## Arduino Driver v1

The arduino ran a simple code that enabled an onboard counter, returned the value of the counter when triggered over Serial query, and then reset the counter. 

```c
/*
CounterV1.ino
Caleb Howington 2014
Plourde Research Group
Syracuse University
*/

int count = 0;
int incomingByte = 0;
int reps = 0;

//Initialize 
void setup()
{
 startCounting();
 Serial.begin(115200);
 attachInterrupt(0,print,RISING);
}

//Initialize Counter
void startCounting()
{
 TCCR1A = 0;
 TCCR1B = 0; 
 TIMSK1 = bit (TOIE1);   // interrupt on Timer 1 overflow
 GTCCR = bit (PSRASY);        // reset prescaler now
 TCCR1B =  bit (CS10) | bit (CS11) | bit (CS12);
 TCNT1 = 0;      // Both counters to zero
}

//Reset Counter
void reset_counters()
{
 TCNT1 = 0;
}

//Main Operation Loop
void loop()
{
   // send data only when you receive data:
        if (Serial.available() > 0) {
                // read the incoming byte:
                incomingByte = Serial.read();
                switch (incomingByte) {
                 case 113: //recieved 'q'
                    print();  //Query Count
                    break;
                 case 116: //recieved 't'
                    reset_counters();
                    break;
                }
        }
}

//Print Value of Counter, reset
void print()
{
 count = TCNT1;
 TCNT1=0;
 Serial.println(count); 
}
```

# Version 2

The next version of this setup needs to be much more robust and capable. Since we will be implementing the JPM readout protocol with full qubit and cavity control, we will be using the very nice BBN software [PyQLab](https://github.com/BBN-Q/PyQLab) for our experiment control flow. I have forked this code to add JPM control and measurment functionality [here](pyqlab.md). 

## Circuit v2

## Arduino Driver v2
