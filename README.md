# MINDSTORMS Remote Control

## Android app

The Android App is written using http://kodular.io. The graphics are designed by Anton from http;//antonsmindstorms.com.


## Protocol

The remote control sens its control data in a structure:

|bytes | format | specification |
|------|--------|---------------|
| 1 | b | l_stick_hor |
| 1 | b | l_stick_ver |
| 1 | b | r_stick_hor |
| 1 | b | r_stick_ver |
| 1 | B | l_trigger |
| 1 | B | r_trigger |
| 2 | B | padding |
| 4 | i |  

Transmit struct('bbbbBBiiB'_ with l_stick_hor,l_stick_ver,r_stick_hor,r_stick_ver,l_trigger,r_trigger,

## SPIKE / MINDSTORMS python application