# Memory Acquisition

Memory acquisition refers to the process of creating a copy of the contents of a computer's memory (also known as RAM) for the purpose of analysis. This process is commonly used in the field of digital forensics to collect evidence from a computer that is suspected of being used in criminal activity.
There are several tools and techniques that can be used to acquire the memory of a computer, including:
Using a hardware write-blocker to copy the contents of memory to a storage device.
Utilizing specialized software, such as forensic acquisition utilities like FTK Imager or Memoryze, to create a dump file of the computer's memory.
Extracting the memory using DMA attack, by connecting to it via Firewire or Thunderbolt.
It's important to note that memory acquisition is typically a technically demanding task which require advanced knowledge and tools, and should only be performed by trained professionals with a clear legal authority to do so.
There's also difference between Memory Dump and Memory Snapshot. Memory Dump, simply dumps all the data from the memory, while Memory Snapshot only captures the active processes in memory at the time of the snapshot.

# Winpmem 

Winpmem is a command line tool that can be used to acquire physical memory of Windows systems. It is an open-source tool that can be used to create memory dumps of Windows systems without the need to install any software on the target machine.

The tool can be used to create a full memory dump of the system, which can be useful for forensic analysis and incident response purposes. The memory dump can be saved to a file for later analysis using other tools such as volatility.

Winpmem is primarily intended for use in live forensics, and it is a user-space memory acquisition tool. It is available for download for Windows and Linux.

The winpmem command can be used with several additional independent variables, or options, to modify its behavior.

The "-o" option is used to specify the output file location where the memory dump will be saved. This option allows you to specify the path and filename of the memory dump file that will be created by winpmem.

The "-p" option is used to specify the path to the pagefile.sys file on the target system. This option allows you to include the pagefile.sys file in the memory dump, which can be useful for forensic analysis as it can contain unallocated memory or files that were deleted from the file system.

The "-e" option is used to extract raw image from AFF4 file, This option allows to extract the memory dump from a AFF4 format file. AFF4 is a format for storing forensic images, and this option allow to extract the raw data.

The "-l" option is used to load driver for live memory analysis, this option allows to analyze memory on live systems by loading a driver that allows access to physical memory. This can be useful for incident response and live forensics purposes.

It's important to note that the use of these options may require administrator privileges and may also have additional prerequisites such as specific driver version to use with the -l option.

Here are some examples of how the Winpmem command can be used:

Create a full memory dump of the system and save it to a file named "memory.dump":

    winpmem.exe -o memory.dump

Create a memory dump of the system, but only include pages that have been modified:

    winpmem.exe -o memory.dump --modified

Create a memory dump of the system using the physical memory addressing mode.

    winpmem.exe -o memory.dump --physical

Create a memory dump of the system and encrypt it using AES-256 and save the encrypted dump to a file named "memory.dump.enc"

    winpmem.exe -o memory.dump --encryption aes-256 --keyfile keyfile.bin

Winpmem supports a variety of options, such as compress dumpfile, dump only specific processes and dump only physical memory . It is also possible to use it over network to acquire memory of remote systems.

  It is important to note that when creating memory dumps of live systems, it is important to make sure that the system is not modified during the acquisition process, as this can affect the integrity of the dump.

# DumpIt

DumpIt is a command-line tool that can be used to create a physical memory dump of a Windows system. It is a user-space memory acquisition tool, and it is primarily intended for use in live forensics. DumpIt is developed and maintained by Comae Technologies and can be downloaded from their website.

The basic syntax for using DumpIt is:

    dumpit.exe [options] [output_file]

  Here are some examples of options and usage of the DumpIt command:

The /f option is used to specify the location and name of the output file where the memory dump will be saved. For example, to create a memory dump and save it to a file named "memory.dump" in the "C:" drive, you would use the following command:

    dumpit.exe /f C:\memory.dump

The /s option is used to specify a hashing algorithm to calculate the hash of the memory dump. For example, to create a memory dump and calculate its SHA-256 hash, you would use the following command:

    dumpit.exe /f C:\memory.dump /s sha256

The /t option is used to send the memory dump to a remote host over the network. This option requires that the remote host is running a listener, which can be set up using the /l option. For example, to create a memory dump and send it to a remote host at IP address 192.168.1.100, you would use the following command:

    dumpit.exe /f C:\memory.dump /t 192.168.1.100

It's important to note that, like any memory acquisition tool, the integrity of the dump could be affected by any modification of the running system, and proper handling of the output file is necessary.

In addition to these options, DumpIt supports additional options like compress dumpfile, dump only specific processes, and dump only physical memory. It can also be used in combination with other forensic tools like Volatility for further analysis.

