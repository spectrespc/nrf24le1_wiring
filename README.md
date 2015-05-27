# nrf24le1 Wiring
A Wiring-like wrapper to use the nrf24le1 SoC

Go to https://hackaday.io/project/5794-nrf24le1-wiring-library for more details

#Basics
####pinMode, digitalRead, digitalWrite, analogRead, analogWrite
`pinMode(P0_0, INPUT | PULLUP);`
`digitalRead(P0_0);`
`digitalWrite(P0_0, HIGH);`

pinMode is slightly different in that you `|` together the options which are:
* PULLUP
* PULLDOWN
* INPUT
* OUTPUT
* HIGH_POWER
* NORMAL_POWER

`digitalRead`, `digitalWrite`, `analogWrite` work as usual.

`noPullup()` and `pullup()` are absent and rolled into `pinMode()`

#####Analog and PWM Functions
ADC is setup in 12 bit resolution, PWM pre-scaler to 10 and width to 8 bits. 

####Interupts
Not implemented yet but `'interupts()` and `noInterrupts()` work as expected.

####Timing
`millis()` not implemented yet

`delay()` and `delayMilliseconds()` work as expected

####Serial
`serialBegin()` setups up at 38400 8n1

Print and Println are not implemented

`debugPrint(format, args)` is a macro that wraps `printf_tiny()` and is enabled if DEBUG is defined:

`debugPrint("nrf24le1 with no args", 0);`
`debugPrint("nrf24le1 version %u", 1);`

####I2C
Automatically set up in master mode at 400kHz. I would like this to be made more Wiring-like. 

`wireWrite8(slave address, data)` returns W2_NACK_VAL or W2_ACK_VAL

`wireRead8(slave address, address)` returns W2_NACK_VAL or W2_ACK_VAL

`wireRead16(slave address, address)` returns W2_NACK_VAL or W2_ACK_VAL

####Pins
Are defined as `P0_0` `P1_1`etc. 

gpio.h has defines for all three variants and also the special names for the pins which can be used as well. 
