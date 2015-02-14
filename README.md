# pyserialcom.py
## Developpement information

 * Maintainer : Thomas Maurice <tmaurice59@gmail.com>
 * Current version : 0.2
 * Developpement status : Still being developped :)
 * Portability : Linux and Windows (with Python 2.6)

## What is this ?
This is a python script which allow you to communicate with
serial devices.

As I noticed that sometimes minicom is not enough to debug serial devices
(especially if they send you non printable ascii chars) I decided to develop
a small alternative, here it is.

## Requirements
To run this software you need:

 * python (version 2.7.5 in my case but works fine with 2.6 too)
 * pyGTK (version >= 2.0)
 * pyserial (the latest the better)
 * docopt

You simply run the program by typing ```./pyserialcom.py``` in
a terminal and here you go ! It will try to find the first USB to serial
adapter and open it (ttyACMX ot ttyUSBX devices), the default baudrate is 9600.

## More precise syntax
If you require a specific port or baudrate, here is the compete syntax :

    Usage:
        pyserialcom.py [--baudrate=<BAUD>] [--port=<PORT>]
        
    Options:
        -h --help                      Displays help
        -p PORT --port=<PORT>          The serial port file to use
        -b BAUD --baudrate=<BAUD>      The baudrate to use [default: 9600]
        
    If no options are provided, the default 9600 baudrate will be used
    and the serial port will be detected from any /dev/ttyACM* or /dev/ttyUSB*



## Display modes
Once you have connected to the device, it will print in the console
every byte recieved which can be a problem if the characters are not
printable. Your console can quickly become a mess !

To avoid that you can select the way you want data to be output in
the console :

 * ASCII (default) : Will just print out the characters to the console regardless of their printability
 * Hex : Will output the hexadecimal value of the characters
 * Both : will output the hex value, and the ASCII one if the character is printable

To be more clear, here is a small recap :

Character 'a'. ASCII : **a**, Hex : **[0x61]**, Both **[0x61 a]**

Another exemple with a non printable one :

Character '\n'. ASCII : **\n**, Hex : **[0xa ]**, Both **[0xa  .]**

Enjoy :)
