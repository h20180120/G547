Link to repo: https://github.com/h20180120/G547/tree/master/usb-servo

Servo Motor Control using ATmega8A

Summary:
The main aim of this project is to control servo motor connected to ATmega8 using CLI. Servos are connected with three-wire-cables. A red and a black one for the power, and a yellow one for the signal. Power has to be between 4.8 and 6 volts, so the 5 volts from the USB-port is in the range. The angle of the servo is controlled with pulse width modulation (PWM).

Two implementations were tested. One using libusb and another using ioctl.

Prototype

Compiling & Uploading the firmware:

This project requires avr-gcc and avr-libc.

Steps to build:

*Firmware* (firmware directory)

1. Set the fuse-bits to use the external crystal:

`$ avrdude -p atmega8 -P /dev/parport0 -c stk200 -U hfuse:w:0xC9:m -U lfuse:w:0x9F:m`

2. Compile

`$ make`

3. Flash

`$ make program`

*libusb userspace* (comandline-libusb directory)

1. build

`$ make all`

2. Usage

`$ ./usb-servo status` Returns the current servo motor angle

`$ ./usb-servo set <angle>` Rotates the motor to the requested angle

*ioctl userspace and kernel module* (comandline-ioctl directory)

Compiling

`$ make all`

Inserting

`$ make insert`

To compile user space code

`$ make user`

To execute the user space code: (Same as libusb)
