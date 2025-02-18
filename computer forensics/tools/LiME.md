
LiME (Linux Memory Extractor) is an *open-source forensic tool* designed for live **memory** acquisition on **Linux-based systems**.

It enables the **acquisition** of the entire contents of a system’s RAM in real time, facilitating the recovery of **volatile data** such as passwords, encryption keys (useful for decrypting communications, memory regions, etc.), and evidence of running processes. 

LiME functions as a kernel module, allowing it to interact directly with the operating system and access all memory regions without interference. 

The tool maps the entire physical memory of the system, including user
space, kernel space, and other volatile data. Once mapped, it reads memory contents sequentially and writes them to the specified output destination, depending on whether the acquisition is local or remote.

LiME’s output format preserves the integrity of the memory content, as it performs no compression, modification, or addition of metadata.

Furthermore, it accounts for the system’s endianness to ensure compatibility with the architecture being analyzed. Notably, it supports remote memory acquisition, enabling memory data to be extracted over a network. 

In a **remote acquisition scenario**, the process is initiated remotely, and the memory data is transmitted via sockets to a LiME server for storage. 

For **local acquisitions**, the memory contents are written directly to a file on the machine and then transmitted to forensic workstations for further analysis if needed.
