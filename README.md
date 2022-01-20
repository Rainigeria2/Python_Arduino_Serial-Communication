# Python_Arduino_Serial-Communication
This repository contains sample codes of pyserial communication between python and arduino.This allows us to send data between a computer though Arduino's serial.

# Step 1: Install Python on Your Computer
You can skip this step if you have installed the Python IDLE already in your computer.

1. Go to the python website and download it (https://www.python.org/downloads/).

2. Once you have done downloading, you can move on to installation by keeping the directory in which the python is getting installed by default.

# Step 2: Install PySerial
PySerial is a Python API module which is used to read and write serial data to Arduino or any other Microcontroller. To install on Windows, simply visit (https://pypi.org/project/pyserial/2.7/) and following the steps bellow :

1. Download the PySerial from the link above or Open CMD and type
 
 _pip install pyserial_

2. Install it by keeping the setting as the default. You should be sure that Pyserial worked correctly, To check this You can open IDLE and type in

_import serial_

If you are not getting any error, it means you installed it correct, else you can check your installation.

# Step 3: Python Code
First up, we need a simple program to get the Python sending data over the serial port

``# Importing Libraries
import serial
import time
arduino = serial.Serial(port='COM4', baudrate=115200, timeout=.1)
def write_read(x):
    arduino.write(bytes(x, 'utf-8'))
    time.sleep(0.05)
    data = arduino.readline()
    return data
while True:
    num = input("Enter a number: ") # Taking input from user
    value = write_read(num)
    print(value) # printing the value`` 

# Step 4: Arduino Code

``int x;
void setup() {
 Serial.begin(115200);
 Serial.setTimeout(1);
}
void loop() {
 while (!Serial.available());
 x = Serial.readString().toInt();
 Serial.print(x + 1);
}``

