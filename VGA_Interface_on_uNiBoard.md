## Description ##

The LCD monitor interfaced with the uniboard using VGA connector. The system is capable of displaying at least 15x15 characters on a VGA monitor using standard VGA frequencies. The data itself is to be received by the micro-controller via its USART port which we are going to display on monitor. All this using a 16 Mhz clock for the AVR.


## Specifications ##
  1. VGA-terminal
  1. Quantity of symbols: 20 lines by 20 characters.
  1. The resolution of a character matrix: 8x12 points
  1. Formed signal: VGA
  1. The resolution: 640x480
  1. Frequency of vertical synchronization: 60Hz
  1. Speed of exchange UART 19200 bps

<img src='http://uniboard.googlecode.com/files/1_VGA.JPG' width='600' height='800' />

## Hardware Description ##

Initial calculations showed that the AVR 8-bit micro-controller from ATMEL, with its 16Mhz clock speed providing approximately 16 MIPS Therefore I concluded that with a clock of 16 MHz I could achieve something in the order of 8 MHz speed of data being transferred out of a port. Following circuit diagram shows minimum hardware required for project.

NOTE : All the required port pins as well as the UART1 interface are readily available on the uniboard.

Here we are using PE4(INT4) and PE5(INT5) port pins to generate horizontal and vertical synchronization signals respectively where as PB2(MOSI) port pin to output the data from controller. UART1 interface is readily available on uniboard using which the controller receiving the data which is to be send to display.

<img src='http://uniboard.googlecode.com/files/2_VGA.JPG' width='796' height='772' />

## Algorithm ##

The project algorithm of rendering the image is traditional enough, the main know-how of the project is the bit-by-bit shifting of the image, utilizing the SPI shift register SPDR via the MOSI pin. Thus two jobs are performed at the same time, when the subsequent byte for rendering is sent, the previous byte is shifted out through the shift register (SPI SPDR MOSI).

## Procedure ##


  1. Make the connection as per the circuit diagram
  1. Upload the program in uC using make utility.
  1. The program will initialize all the peripheral we required in our project.
  1. Using the counter ‘0’ we are generating the horizontal and vertical frequencies of approximately 30 kHz and 60 Hz respectively.
  1. Now we go for the VGA rendering in which we first initialize display buffer and send the uC in sleep mode (it is necessary for disposal of horizontal jitter) for proper synchronization.
  1. Now we check for a received symbol and which intern call VGA terminal handle function.
  1. The VGA handle function Parser received symbols from UART, Check for overflow display buffer and send the symbol to display buffer.
  1. Now we are ready to display the symbol in display buffer so we check for video enable flag if it is true  i.e. if we are in visible field then we Set pointer for render line (display buffer), Set pointer for render line (character generator) and send the data out using SPI.
  1. If we are not in a visible we are counting the frame. You can add here your own handlers.

## Compiler and code snapshot ##

<img src='http://uniboard.googlecode.com/files/5_VGA.JPG' width='892' height='540' />


## Output on LCD monitor ##

<img src='http://uniboard.googlecode.com/files/6_VGA.JPG' width='892' height='540' />

## Download Sourcecode ##
http://uniboard.googlecode.com/files/VGA_code.zip

## Author ##
Amol Jagtap