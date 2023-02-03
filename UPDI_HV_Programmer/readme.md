# UPDI HV Programmer
HV UPDI (High-Voltage Unified Program and Debug Interface) programmer for tinyAVR, megaAVR and AVR-Dx microcontrollers built on ATmega8/88/168/328 based on the design and the firmware by Dlloydev (https://github.com/Dlloydev/jtag2updi). The HV UPDI programmer will enable you to use the additional configuration settings for the UPDI pin without the fear of getting locked out from the MCU. It features 3 programming modes: UPDI, HV or PCHV, with the target voltage at 5V.

![UPDI_HV_Programmer_pic1.jpg](https://raw.githubusercontent.com/wagiminator/AVR-Programmer/master/UPDI_HV_Programmer/UPDI_HV_Programmer_pic1.jpg)

**Mode Jumper Settings:**

|Mode Jumper|Prog Mode|PA0 Configurations|HV Pulse|Power Cycle|
|:-|:-|:-|:-|:-|
|no jumper|UPDI|UPDI|NO|NO|
|pins 2-3 shorted|HV|UPDI, RESET|YES|NO|
|pins 1-2 shorted|PCHV|UPDI, RESET, GPIO|YES|YES|

**Modes:**

|Mode|Function|
|:-|:-|
|UPDI Mode|This mode would be used when the UPDI pin is configured as UPDI or for any target device that isn't HV tolerant.|
|HV Mode|This mode applies the 12V UPDI enable sequence (HV pulse) at the start of the programming sequence. This temporarily reconfigures the UPDI/Reset pin to UPDI mode which will remain in this state until the next power on reset (POR). This allows programming to occur when the pin is configured as Reset. A POR needs to occur for any fuse setting changes to take effect.|
|PCHV Mode|Power Cycle High-Voltage mode (PCHV) will initiate a power cycle and HV pulse at the start of the programming sequence. At the end of the sequence, a second power cycle will occur which causes any new fuse setting to take effect. The power cycle OFF duration has been set to 10ms. This mode would be used when the UPDI/Reset pin is configured as Reset or as GPIO.|

**Status LED Operation:**

|LED|Status|
|:-|:-|
|PWR|STEADY ON when programmer is powered|
|PRG|STEADY ON when in programming mode; BLINKING at 4Hz if target overload occurs|
|HV|FLASHING at HV pulses during programming|

- The CH330N can be replaced with a CH340N.
- More information and source code: https://github.com/Dlloydev/jtag2updi

![UPDI_HV_Programmer_pic2.jpg](https://raw.githubusercontent.com/wagiminator/AVR-Programmer/master/UPDI_HV_Programmer/UPDI_HV_Programmer_pic2.jpg)
![UPDI_HV_Programmer_scope.jpg](https://raw.githubusercontent.com/wagiminator/AVR-Programmer/master/UPDI_HV_Programmer/UPDI_HV_Programmer_scope.jpeg)
