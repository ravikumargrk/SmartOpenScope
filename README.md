# About
Python (3.8) code that runs on your PC or RPi, interacts with [OpenScope MZ](https://reference.digilentinc.com/reference/instrumentation/openscope-mz/start) (by digilent) over WiFi to automate the process of collecting data from openscope

This code could in RPi and the combo RPi+OpenScope becomes your own smart / automated oscilloscope / Data Acquisition System.

You might want to read this before coding on top this repo : [Digilent Instrumentation Protocol](https://reference.digilentinc.com/reference/software/digilent-instrumentation-protocol/protocol)
# Files
## OpenScope115200.hex
* The standard baudrate this device uses is 1250000 but if usually devices have max baudrate of 115200 
* For OpenScope to communicate with such devices, install this firmware
> Procedure : 

> Download this file, Hold BTNP and press BTNR on device to go into bootloader mode

> Follow [This tutorial](https://reference.digilentinc.com/learn/instrumentation/tutorials/openscope-mz/update-firmware) and in "Available Firmware Versions" Select option "Others" to browse and pick downloaded file.
## usb_omz.py 
* Sets up parameters like sampling rate, sample size and number of acquisitions to be done and wait interval between the acquisitions
* Script takes maxacqCount number of acuisition in different files and saves it as CSV files.
## decode.py 
* Finds all data container files in current diectory generated by usb_omz.py
* Decodes bin files to csv format
## Problems
* Sadly Digilent Openscope has been discontinued. 
* At high sample size, I observed that only 90% is data collected and there is a data loss while reading data from serial input. This problem might be solved by placing right serial object parameters. [Forum Question](https://forum.digilentinc.com/topic/20989-oscilloscope-read-fails-at-high-sample-sizes-greater-than-~3900-samples/)
