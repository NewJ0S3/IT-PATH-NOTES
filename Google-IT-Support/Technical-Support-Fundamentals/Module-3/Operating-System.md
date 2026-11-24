# Operating System

## What’s an Operating System?

Is the whole package that manages our computer’s resources and lets us interact with it.

### Operating System Structure

An OS consist of two main parts: the kernel and the user space. The kernel manages hardware and system resources, while the user space includes programs and interfaces users interact with.

The kernel handles core functions like  file management, process scheduling, memory allocation, and input/output (IO) management.

### Types of Operating Systems

- Windows OS, developed by Microsoft, is widely used in business and consumer PCs.
- Mac OS, by Apple, is mainly used in consumer Apple computers.
- Linux is an oper-source OS kernel with many distributions (e.g., Ubuntu, Debian, Red Hat) used heavily in business and consumer enviroments.
- Chrome OS and Android also run on the Linux kernel, showing Linux’s broad influence.

### Key Kernel Functions

File management organizes data into files and directories for easy access. Process management allows multitasking by scheduling programs efficiently. Memory management allocates system memory to applications as needed. IO management controls communication with external devices like keyboards, disks, and networks.

### User Space Overview

User space includes all software outside the kernel, such  as text editors, music players, and system settings, which users interact with directly.

### File Systems

File systems organize and keep  track of files on storage devices, requiring disk configuration for the OS to read and write data. Different operating systems user different file systems, such as NTFS for Windows and EXT4 for Linux, each with unique features and compatibility considerations.

### File Data Storage

Data is stored in blocks on hard drives, which can be scattered across the disk to improve access speed and storage efficiency. Block storage allows faster data handling and better utilization of disk space compared to storing data in one continuous piece.

### File Metadata

Metadata contains important information about files, including creation date, modification date, access permissions, and file type. File extensions, like .jpg for images, help the operating system identify the file type and how to handle it.

**Process** is a program that’s executing, like our internet browser or text editor.

**Program** is an application that we can run, like Chrome.

**Time Slice** is a very short interval of time that gets allocated to a process for CPU execution.

**Kernel** created processes, efficiently schedules them, and manages how processes are terminated.

### Process Management Basics

A process is an executing program, and multiple processes of the same program can run simultaneously. The kernel must allocate finite hardware resources to these processes to allow multiple programs to run.

### CPU Scheduling and Time Slices

The CPU executes processes one at a time using very short time slices, switching rapidly between processes. This rapid switching creates the illusion of simultaneous execution to the user.

### Resource Management Challenges

If one process uses too many time slices or there are too many processes, the system can slow down. The kernel manages process creatin, scheduling, and termination to reclaim resources and maintain system performance.

**Virtual Memory** is the combination of hard drive space and RAM that acts like memory that our processes can use.

### Memory and Process Execution

Processes require both CPU time and memory space to run efficiently. Physical memory (RAM) is limited compared to hard disk storage, so virtual memory combine RAM and hard drive space to extend usable memory.

### Virtual Memory and Paging

Programs are divided into chunks called pages, which are stored in virtual memory. Pages must be loaded into physical memory (RAM) to be executed, allowing efficient use of memory by loading only needed parts of a program.

### Swap Space and Kernel Management

The portion of the hard drive used for virtual memory is called swap space. The operating system kernel manages the transfer of pages between RAM and swap space, optimizing memory usage without loading entire programs at once.

**I/O devices** are devices that perform input and output.

### Kernel and I/O Devices

The kernel handles communication with various I/O devices such as monitors, keyboards, mice, hard drives, speakers, webcams, and network adapters. It loads device drivers to recognize and interact with hardware, managing data transfer between the system and these devices.

### Data Transfer and Device Communication

The kernel manages data transfer not only between the user and devices but also between devices themselves. It optimizes transfer methods and ensures data integrity by minimizing errors during communication.

### Troubleshooting Performance Issues

Performance problems like slow machines often stem from hardware resource limitations such as insufficient RAM, CPU, or overloaded I/O channels. Understanding these potential bottlenecks is crucial for troubleshooting and improving system responsiveness in IT support roles.

### User space Interaction Methods

Users perform tasks like creating files, opening applications, and deleting items through the user space. Interaction can be done via a shell (text-based commands) or a GUI (visual interface with mouse and icons)

### Graphical User Interface (GUI)

GUIs provide a visual way to interact with the computer using windows, menus, and icons. Commonly used in everyday devices like computers, mobile phones, ATMs, and kiosks, GUIs help users recognize different operating systems by their design.

### Shell and Command Line Interface (CLI)

A shell interprets text commands and sends them to the OS for execution, often used before GUIs were common. The CLI is essential for power users and IT professionals, especially in Linux environments where remote access often lacks a GUI.

### Importance of Learning Both

Knowing how to use both GUI and shell commands is vital in IT support roles. Some tasks and tests require command-line usage, and managing many machines is more efficient  with commands than GUI navigation.

### Understanding Computer Logs

**Logs** are files that record system events on our computer, just like a system’s diary. They capture events such as system startup, driver loading, and error messages.

### Challenges and Benefits of Logs

Logs can be difficult to navigate because they record everything in detail. Despite this, analyzing logs helps identify what happened on a computer and find solutions.

### Practical Application

Computers do not verbally communicate issues, but logs serve as their “voice”. By learning to read and navigate logs, you can effectively troubleshoot and resolve computer problems.

### Boot Process Overview

Booting means starting a computer from nothing to a fully operational system by following a series of steps. The process is similar across most operating systems, involving hardware initialization and loading software.

### BIOS/UEFI and POST

When powered on, the BIOS/UEFI initializes hardware to ensure everything is ready. It runs the Power-On Self-Test (POST) to perform diagnostic checks on the system.

### Boot Device Selection and Bootloader

The BIOS/UEFI checks devices in a configured boot order (hard drives, USB drives, etc.) to find a bootloader. The bootloader is a small program that loads the operating system.

### Operating System and Kernel Loading

After the bootloader runs, it loads the operating system and its kernel. The kernel manages hardware resources and loads drivers to enable hardware-software communication.

### System Processes and User Interaction

Essential system processes and user interface components start, such as user login and desktop environment. This completes the boot process, allowing the  user to interact with the system.

## Installing an Operating System

The operating system in use by an organization have a lot to do with the applications and systems that they need to run.

### Choosing an Operating System

Determine if the OS choice is already made based on organizational requirements or software compatibility. Consider hardware compatibility, including CPU architecture (32-bit vs 64-bit) and manufacturer restrictions.

### Installing the OS

Many computers come with a pre-installed OS that may require final setup  steps like naming and network configuration. For fresh installations, use installation media such as USB drives or disks; USB installation is common and efficient for single computers.

### Scalability and Practical Considerations

Installing OS on multiple machines requires scalable methods beyond single disks. Focus initially on installing the OS on one computer before addressing larger scale deployments.

**Virtual Machine (VM)** is just a copy of a real machine.

### What is a VM

A VM is a software-based copy of a physical computer that runs an operating system isolated from the host machine. It allows running multiple operating systems on one physical machine without needing separate hardware or dual-boot setups.

### Benefits and Use Cases of VMs

VMs use physical resources like CPU, memory, and storage but provide flexibility to run different OSes simultaneously. They are easier to maintain, provision, and reclaim resources when no longer needed.

### Practical Application in IT Support and Learnin

IT support specialists use VMs to create virtual computers on-demand for testing or software compatibility. In this course, learners will use VMs on the Quick Labs platform to complete hands-on exercises in a controlled lab environment.

## Glossary terms from course 1, module 3

### **New terms and their definitions: Course 1 Module 3**

**Android**: A mobile operating system based on Linux

**Application:** A computer program designed for a specific use

**BIOS/UEFI:** A low-level software that initializes our computer's hardware to make sure everything is good to go

**Block storage:** It improves faster handling of data because the data isn't stored in one long piece but in blocks, so it can be accessed more quickly

**Boot:** To start up a computer

**Bootloader:** A small program that loads the operating system

**Chrome OS:** A Linux-based operating system designed by Google

**Command Line Interface (CLI):** A shell that uses text commands to interact with the operating system

**Computer file:** Data that we store and a file can be anything, a word document, a picture, a song, literally anything

**Data blocks:** Data that can be broken down into many pieces and written to different parts of the hard disk

**Distributions:** Some common Linux distributions are Ubuntu, Debian, and Red Hat

**Etcher.io:** A tool you can use to load an install image onto your USB device and make it bootable

**File extension:** The appended part of a filename that tells us what type of file it is in certain operating systems

**File handling:** A process of storing data using a program

**File system:** A system used to manage files

**Finder:** The file manager for all Macs

**Folders/Directories:** Used to organize files

**Hardware resource deficiency:** It refers to the lack of system resources like memory, hard drive space, et cetera

**HFS+/APFS:** HFS+ is a journaling system developed by Apple Inc. and APFS is another but more encrypted Apple journaling system

**Hostname:** Used to identify the computer when it needs to talk to other computers

**Input/Output device:** A device that performs input and output, including monitors, keyboards, mice, hard disk drives, speakers, bluetooth headsets, webcams, and network adapters

**Install image:** A downloadable operating system image used to install an operating system on a device

**I/O management:** Anything that can give us input or that we can use for output of data

**iOS:** A mobile operating system developed by Apple Inc.

**Kernel:** The main core of an operating system that creates processes, efficiently schedules them, and manages how processes are terminated

**Logs:** Files that record system events on our computer

**Mac OS:** Apple's operating system

**Memory management:** One of the functions that a kernel performs; it optimizes memory usage and make sure our applications have enough memory to run

**Metadata:** Tells us everything we need to know about a file, including who created it, when it was last modified, who has access to it, and what type of file it is

**Microsoft Terminal Services Client:** A client program used to create RDP connections to remote computers

**Open SSH:** The most popular program to use SSH within Linux

**Operating system:** The whole package that manages our computers resources and lets us interact with it

**PC:** Personal computer, which technically means a computer that one person uses

**Plink (PuTTY Link):** A tool built into the command line after PuTTY is installed that is used to make remote SSH connections

**Powershell:** A shell (program that interprets text commands) for Windows

**Power user:** Above average computer users

**Process management:** The capacity to manage the many programs in a system - when to run them, the order they run in, how many resources they take up, how long they run, etc.

**Qwiklabs:** An online platform which provides training in cloud services

**Remote connection:** The ability to connect an authorized person to a computer or network remotely; allows us to manage multiple machines from anywhere in the world

**Remote Desktop Protocol (RDP)**: A secure network communication protocol developed by Microsoft that allows a user to connect to another device remotely

**Scalability:** The measure of a system’s ability to increase or decrease in performance and cost in response to varying loads in system processing demands

**Shell:** A program that interprets text commands and sends them to the OS to execute

**SSH (Secure shell):** A protocol implemented by other programs to securely access one computer from another.

**SSH authentication key:** A secure authentication method for accessing a computer from other device

**SSH client:** A program you must have installed on your device in order to establish an SSH connection with another device

**SSH server:** Software installed on a machine that allows for that device to accept an SSH connection

**Standardization:** The process of developing and implementing common technical standards for IT products, systems, and processes.

**Swap space:** The allocated space where the virtual memory is stored on the hard drive when the amount of physical memory space is used up or full

**System:** A group of hardware components and software components that work together to run the programs or processes in the computer

**System settings:** Settings like display resolution, user accounts, network, devices, etc.

**Task bar:** It gives us quick options and shows us information like network connectivity, the date, system notifications, sound etc

**Terminal:** A text based interface to the computer

**Time slice:** A very short interval of time that gets allocated to a process for CPU execution

**Ubuntu:** The most popular Linux consumer distribution

**User name:** A unique identifier for a user account

**User space:** The aspect of an operating system that humans interact with directly like programs, such as text editors, music players, system settings, user interfaces, etc.

**Virtual Box:** An application you can use to install Linux and have it completely isolated from your machine

**Virtual machine (VM):** An application that uses physical resources like memory, CPU and storage, but they offer the added benefit of running multiple operating systems at once

**Virtual memory:** A combination of hard drive space and RAM that acts like memory which our processes can use

**VPN (Virtual private network)**: A secure method of connecting a device to a private network over the internet

### **Terms and their definitions from previous modules**

A

**Abstraction:** To take a relatively complex system and simplify it for our use

**Address bus:** Connects the CPU to the MCC and sends over the location of the data, but not the data itself

**Algorithm:** A series of steps that solves specific problems

**ASCII:** The oldest character encoding standard used is ASCII. It represents the English alphabet, digits, and punctuation marks

**ATA:** The most common interface that hard drives use to connect to our system

**ATX (Advanced Technology eXtended):** The most common form factor for motherboards

B

**Backward compatible:** It means older hardware works with newer hardware

**Binary system:** The communication that a computer uses is referred to as binary system, also known as base-2 numeral system

**Bios (Basic Input Output Services):** The BIOS is software that helps initialize the hardware in our computer and gets our operating system up and running

**BYOD (Bring Your Own Device):** Refers to the practice of allowing people to use their own personal devices for work

**Byte:** A group of 8 bits

C

**Cache:** The assigned stored location for recently or frequently accessed data; on a mobile app it is where anything that was changed or created with that app is stored

**Character encoding:** Is used to assign our binary values to characters so that we as humans can read them

**Charge cycle:** One full charge and discharge of a battery

**Computer:** A device that stores and processes data by performing calculations

**Chipset:** It ****decides how components talk to each other on our machine

**Clock cycle:** When you send a voltage to the clock wire

**Clock speed:** The maximum number of clock cycles that it can handle in a set in a certain time period

**Clock wire:** When you send or receive data, it sends a voltage to that clock wire to let the CPU know it can start doing calculations

**CPU:** Central processing unit

**CPU sockets:** A CPU socket is a series of pins that connect a CPU’s processor to the PC’s motherboard

**Cryptography:** The overarching discipline that covers the practice of coding and hiding messages from third parties

D

**Data sizes:** Metrics that refer to data sizes including bit, byte, kilobyte, kibibyte, and megabyte

**DDR SDRAM (Double Data Rate SDRAM):** A type of RAM that is faster, takes up less power, and has a larger capacity than earlier SDRAM versions

**Decimal form- base 10 system:** In the decimal system, there are 10 possible numbers you can use ranging from zero to nine

**Desktop:** The main screen where we can navigate our files, folders, and applications

**Digital divide:** The growing skills gap between people with and without digital literacy skills

**DIMM:** Dual Inline Memory Module

**Display port:** Port which also outputs audio and video

**DRAM:** Dynamic Random Access Memory

**Drivers:** The drivers contain the instructions our CPU needs to understand external devices like keyboards, webcams, printers

**DVI:** DVI cables generally just output video

E

**Electrostatic discharge:** Electrostatic discharge is a sudden and momentary flow of electric current between two electrically charged objects caused by contact, an electrical short or dielectric breakdown

**External Data Bus (EDB):** It's a row of wires that interconnect the parts of our computer

F

**Factory reset:** Resetting a device to the settings it came with from the factory

**Form factor:** A mathematical way to compensate for irregularities in the shape of an object by using a ratio between its volume and height

H

**Hard drive:** It is a long term memory component that holds all of our data, which can include music, pictures, applications

**Hardware:** External or internal devices and equipment that help you perform major functions

**HDD (Hard disk drive):** Hard disk drives, or HDDs, use a spinning platter and a mechanical arm to read and write information

**HDMI:** A type of cable that outputs both video and audio

**Heatsink:** It is used to dissipate heat from our CPU

I

**Information technology**: The use of digital technology, like computers and the internet, to store and process data into useful information

**Instruction set:** A list of instructions that our CPU is able to run

**ITX (Information Technology eXtended):** A form factor for motherboards that is much smaller than ATX boards

L

**Land Grid Array (LGA):** It is a type of CPU socket that stick out of the motherboard

**Lightning adaptor:** One of the standard power, data and display connector types used in mobile devices

**Linux OS:** Linux is one of the largest an open source operating system used heavily in business infrastructure and in the consumer space

**Logic gates:** Allow transistors to do more complex tasks, like decide where to send electrical signals depending on logical conditions

M

**Mb/s:** megabit per second, which is a unit of data transfer rate

**Memory controller chip (MCC):** A bridge between the CPU and the RAM

**Micro display port:** One of the standard power, data and display connector types used in mobile devices

**Micro HDMI:** One of the standard power, data and display connector types used in mobile devices

**Micro USB:** One of the standard power, data and display connector types used in mobile devices

**Mini HDMI:** One of the standard power, data and display connector types used in mobile devices

**Mini USB:** One of the standard power, data and display connector types used in mobile devices

**Motherboard:** The body or circulatory system of the computer that connects all the pieces together

N

**Northbridge:** interconnects stuff like RAM and video cards

O

**Open source:** This means the developers will let other developers share, modify, and distribute their software for free

**Overclocking:** it increases the rate of your CPU clock cycles in order to perform more tasks

P

**PCI Express:** Peripheral Component Interconnect Express

**PDA (Personal Digital Assistant):** Allows computing to go mobile

**Peripherals:** the external devices which we connect to our computer that add functionality, like: a mouse, a keyboard, and a monitor

**Pin Grid Array (PGA):** CPU socket where the pins are located on the processor itself

**Ports:** Connection points that we can connect devices to that extend the functionality of our computer

**POST (Power On Self Test):** It figures out what hardware is on the computer

**Power supply:** Converts electricity from our wall outlet onto a format that our computer can use

**Programs:** Basic instructions that tell the computer what to do

**Punch cards:** A sequence of cards with holes in them to automatically perform calculations instead of manually entering them by hand

R

**RAM:** Random Access Memory

**Registers:** An accessible location for storing the data that our CPU works with

**Reimaging:** The process of reimaging involves wiping and reinstalling an operating system using a disk image which is a copy of an operating system

**Return merchandise authorization (RMA):** The process of receiving returned merchandise and authorizing a refund

**RGB model:** RGB or red, green, and blue model is the basic model of representing colors

**ROM chip (Read Only Memory):** A read-only memory chip where the BIOS is stored

**RPM:** Revolutions per minute

S

**Safe operating temperature:** The temperature range in which rechargeable batteries must be kept in order to avoid damage

**SATA:** The most popular serial ATA drive, which uses one cable for data transfers

**SDRAM:** It stands for Synchronous DRAM, this type of RAM is synchronized to our systems' clock speed allowing quicker processing of data

**SOC (System On a Chip):** Packs the CPU, Ram, and sometimes even the storage onto a single chip

**Southbridge:** It maintains our IO or input/output controllers, like hard drives and USB devices that input and output data

**SSD:** Solid State Drive

**Standoffs:** Used to raise and attach your motherboard to the case

T

**Thermal paste:** A substance used to better connect our CPU and heat sink, so the heat transfers from to the other better

**Type-C connector:** A type of USB connector meant to replace many peripheral connections

U

**UEFI:** Unified Extensible Firmware Interface

**USB (Universal Serial Bus):** A connection standard for connecting peripherals to devices such as computers

**USB-C adapter:** One of the standard power, data and display connector types used in mobile devices

**UTF-8:** The most prevalent encoding standard used today
