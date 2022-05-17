# What is an Operating System

## Monolithic vs Microkernel
* In microkernels, the kernel contains handlers that require direct hardware access, everything else is run in userspace. 
* In monolithic designs, everything is included in the kernel and have direct access to the operating system's memory.
* Monolithic kernels will have larger codebases which are harder to manage and change, take up more space on disk and can be less reliable. 
* Microkernels can be less complex, thus more reliable however the need for additional communication makes them slower.

## Communicating with hardware devices
* In UNIX systems, communicating with hardware devices is performed through the reading and writing of "files". 
* The files are not actually files, but more likely memory locations that are designated to be the intermediary between the software and the hardware device.
* The system API is able to see this memory and make the corresponding communications with the device driver.

## Hardware Interrupts
* There are likely many devices that are able to interrupt the CPU with different priorities. 
* Sometimes the CPU is not able to spare the time to service low priority interrupts. 
* Thus an interrupt controller is used that has pins that I/O or other devices can vary the voltage on to let the controller know that they have an interrupt. 
* The interrupt controller sends the interrupt with the highest priority to the CPU if the CPU is accepting interrupts as well as the ID of the device that created the interrupt. 
* The CPU lets the interrupt controller know that the interrupt is serviced which lets the device know. 

## What is an Operating System?
* There is no concrete answer. 
* In general it is software that manages hardware and software and provides common resources and services for programs 