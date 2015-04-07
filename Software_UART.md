UART or Universal Asynchronous Receiver Transmitter is used for serial data communication; it converts bytes of data to and from asynchronous start‐stop bit streams represented as binary electrical impulses. UARTs are commonly used in conjunction with other communication standards such as RS‐232. The word **asynchronous** indicates that UARTs recover character timing information from the data stream, using designated **start** and **stop** bits to indicate the framing of each character. In synchronous transmission, the clock data is recovered separately from the data stream and no start / stop bits are used.

In many microprocessors in built hardware is not available, or the available hardware UART pins might have been exhausted. Many times, the user might need one more UART for some application. A software based UART stack is what comes to your rescue in such cases. Generic Software UART written in C language can be implemented on any micro-controller with a C compiler.

### Operation: ###
  * In idle state, the line is held at logic ‘1’. When data is to be transmitted, the start bit, which is a logic ‘0’ is transmitted for a period of 1 bit time. This causes a ‘1’ to ‘0’ transition at the line. This can be detected by the receiver and is used as a notification that data is coming.
  * The data bits are then transferred serially, starting with the Least Significant Bit. The logic value corresponding to the data bit being transmitted is held at the line for 1 bit time.
  * When data bits have been transmitted, a stop bit is transferred. A stop bit is a logical ‘1’ and puts the line back to idle state before a new start bit followed by the data can be transmitted.
  * An even or odd parity bit according to number of ones in the data can be send before stop bit if required by the user. This parity bit can be checked at receiver side which can be helpful in error detection. If parity error is detected while reception the program sets the parity\_error flag to ‘1’.
  * The receiver must sample the data during every bit time in order to receive the data properly. The sampling frequency is generally taken to be a multiple of the baud rate so that all the bits are samples correctly.
  * This software UART requires a timer interrupt to be set to 3 times the baud rate and two software controlled pins for the receive and transmit functions. Hence the program enters the timer ISR for every delay of 3 times the baud rate.
  * A counter for sampling is initialized to 4 at the start of receiving. After detection of start bit that counter is made to 3. This feature makes possible that after start bit each data bit is sampled around the middle of time-period of that bit.
  * The received characters are buffered in an array so that there is no loss of data for a continuous sequence of characters.
  * When the above functions are managed by software, the resulting module is known as software UART.

### Key Features: ###
  1. An interface similar to hardware UART with transmit and receive interrupts.
  1. Interrupt driven implementation.
  1. Allows user defined Baud rate, Clock frequency in sw\_uart\_config.h.
  1. Allows 5,6,7,8 bit Tx/Rx as defined by user.
  1. Allows 1 or 2 Stop bits as per need.
  1. Parity bit can be added or checked with data frame for error detection.
  1. Minimal hardware usage.
  1. User can change UART configuration in sw\_uart\_config.h
  1. Can be used for any microcontroller by changing timer control registers accordingly.

### Implementation: ###

The project consists of two main header files. “sw\_uart.h” consists the functions and timer ISR of s/w UART. There is no need for user to change this file. For using s/w UART user has to include “sw\_uart.h” file in the program. While “sw\_uart\_config.h” is a header file using which the user can configure the UART as per his requirement based upon application. The following modules are implemented in the solution-

  1. **int get\_rx\_pin\_status(void)**
> > Function which returns 0 or 1 dependent on whether the receive pin is high or low.
  1. **void set\_tx\_pin\_high( void )**
> > Function to set the transmit pin to the high state.
  1. **void set\_tx\_pin\_low( void )**
> > Function to set the transmit pin to the low state.
  1. **void timer0\_init( )**
> > Function which sets the timer0 of Atmega 128 to 3 times the baud rate, enables interrupt and reset on every match of the timer counter.
  1. **void sw\_uart\_init(void)**
> > Function to initialize the sw UART to idle state and sets appropriate flags and initialize the timer.
  1. **void sw\_UART\_Transmit\_char(char ch)**
> > Function which defines the frame to be transmitted and outputs the byte serially on the TX pin and initializes flags to initiate transfer on the next interrupt.
  1. **char sw\_UART\_Receive\_char( void )**
> > Function which returns the data frame from the RX pin.
  1. **void flush\_input\_buffer( void )**
> > Function to clear the input buffer.
  1. **static void sw\_uart\_io\_init(void)**
> > Function to initialize s/w UART Tx/Rx pins
  1. **void frame\_calc(unsigned char)**
> > Function to calculate the frame format according to start, stop and parity bits configuration.

### Download source ###

The source code along with a sample example can be downloaded from [here](http://uniboard.googlecode.com/files/sw%20UART.zip)

### Author ###
[Prashant Mehta](http://groups.google.com/groups/profile?enc_user=iOK7OBIAAADyAE1DGQZHab1aiF6QZATT8rhlH0Pnl47z4AZhN98BFg)