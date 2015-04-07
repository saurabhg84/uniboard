## NOTE ##

  1. While you are using the uNiBoard v1.1 on windows you are bound to use WinAVR. The usbasp driver provided  in the downloads section would sometimes fail to work with versions of WinAVR other than 2007 (provided in the downloads section).
  1. To ensure that your toolchain and driver works correctly, we advise you to use the [WinAVR2007 version](http://uniboard.googlecode.com/files/WinAVR-20070122-install.exe) provided in the downloads section along with the [usbasp driver](http://uniboard.googlecode.com/files/usbasp.zip) provided.
  1. For any other combinations of WinAVR and usbasp driver, we do not guarantee success. We will very soon find a usbasp driver that works with the latest version of WinAVR. Till then you can continue using WinAVR2007.

## Getting started ##

  1. After following the above procedure, download the test program folder by clicking [here](http://uniboard.googlecode.com/files/Test_program_uniboard.zip).
  1. The test program contains the hex file to be dumped on the uNiBoard v1.1 for two popular applications, SNAKE and ARKANOID game
  1. On windows platform you can use the snake.bat file to program the SNAKE application.
  1. Once that is done, you would be able to play SNAKE on your hyperterminal by selecting a baud rate of 115200 with 8 data bits, no parity and 1 stop bit.
  1. Use arkonoid.bat to load the arkonoid game which would again work with the same  hyperterminal settings
  1. For Linux users, we have kept script files, snake.sh and arkonoid.sh which can be run to program the uNiBoard v1.1
  1. Linux would require super user privileges to program, which can be done by entering the root password when prompted on running the script