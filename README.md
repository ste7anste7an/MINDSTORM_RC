# MINDSTORMS Remote Control

## Android app

The Android App is written using http://kodular.io. The graphics are designed by Anton from http://antonsmindstorms.com.

<p align="center">
  <img src="images/MINDSTORM_RC.jpg" width="350" title="MINDSTORMS RC">
</p>

## Protocol

### Sending
The remote control sends its control data in a structure:

|bytes | format | specification | range |
|------|--------|---------------|-------|
| 1 | b | l_stick_hor | -100..100 |
| 1 | b | l_stick_ver | -100..100 |
| 1 | b | r_stick_hor | -100..100 |
| 1 | b | r_stick_ver | -100..100 |
| 1 | B | l_trigger | 0..200|
| 1 | B | r_trigger | 0..200 |
| 2 | h | l_slider | -360..360 |
| 2 | h | r_slider | -360..360 |
| 1 | B | button bits | 1 << (button-1) |

This corresponds to the following Python structure:

`Transmit struct.pack('bbbbBBhhB', l_stick_hor,l_stick_ver,r_stick_hor,r_stick_ver,l_trigger,r_trigger,l_slider,r_slider,buttons)`

### Receiving
The remote control receives a number of messages using the following structure:

| command | description | example |
|---------|-------------|---------|
|`Image` | displays a SPIKE/Mindstorms image on small LCD display | `Image('35790:00000:00000:00000:00000')`|
|`T<text>` | displays test `<text>` in the status line of the LCD display | `THello World` |
|`S<text>` | Uses text-to-speech (english) to convert `<text>` to speech| `SWall detected` |
|`L<value>` | Sets left slider on value `<value>`| `L100` |
|`R<value>` | Sets rightt slider on value `<value>`| `R100` |


## SPIKE / MINDSTORMS python application