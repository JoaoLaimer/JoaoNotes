## Long Term Storage
Three requisites are essential:
- Must be possible to store a large quantity of information.
- The information must survive the ending of a process that it uses.
- Multiple process must be able to access the information concurrently.

The writing and reading of information are essential to any application.

## Files
In the point of view of the user the file system is one of the main parts of the OS, is the most commonly used activities.
The OS abstracts the logic storage: files.

Files are logical information units, created by processes.
Files are stored by the OS in different physical devices (tape, pendrives, HD, SSD, etc).

A file system gives us a collection of function used to be executed (create, delete, read, close, write).

There are some attributes associated with files, like: Name, size, owner, date/hour, protection, flags, password.

- Flags: control something like hiding.

## File Structure
Files can be structured in three different ways.
- byte sequences, register sequences and trees.
#### Byte Sequence
Simplest form of file structure, the system has no logical structure to data, everything the system sees are bytes.
Any meaning and organization must be imposed by user programs.
Offers maximum flexibility.
Windows and Unix

#### Registry Sequence
The file is seen as a sequence of registries of fixed size. The ideia is that the operation of reading returns a registry and the write operation overwrites or index a registry.
This was used in older SO.  For example: mainframes.

#### Trees
A file is built by a registry tree, that can have different sizes.
Each registry must have a key for faster searching.
Used in modern mainframes.

## Accessing Files
#### Sequential Access
The first kinds of system used to offer this access - tapes.
Reads the position of the file and advances to the next position automatically, can't read out of order.

#### Direct Access or Random Access
Based on files in the disk.
Allows blocks to be read and stored at any order.
Essential to a lot of applications.
The most used method.

## File Implementation
It's more important to know which blocks on the disk are related to each files.
Which strategy is most used:
- Continuous Allocation.
- Linked Allocation.
- Indexed Allocation.

### Continuous Allocation
Simplest allocation schema.
Files are stored in continuous blocks in disk.

In the directory table there is the start address and allocated area size.

Advantages:
- Simple
- Good Performance
Disadvantages:
- Disk becomes fragmented when files are removed leaving spaces between used files.
- Compacting is costly.

Continuous allocation can be used efficiently with single write files (won't grow in size).

### Linked Allocation
Each file is kept like a linked list of blocks on disk.
The first word of each block is used like a pointer to the next block, the rest of the block is used for data.
There is no external fragmentation. A freed block is used to attend to a request >?
It's not necessary to define maximum size of the file.

Disadvantages:
- There's no direct access. When accessing block i, you need to start from the first file block and follow the pointers until block i.
- Wastes more space with pointers
- Less stable -> Broken pointer.

A important variation of the linked allocation is the use of a file allocation table (FAT).

### FAT
A section of disk in the start of each partition is reserved to control the table.
The table has an entry to each block of the disk, table is indexed by block number
FAT is used as a linked list, loaded in the main memory, the linkage is done in the main memory, without referencing the disk.
The disadvantage is that the whole table must be in memory, doesn't work in big disks.

## Indexed Allocation
The index block has pointers to every block in the file.
The i entry of the index block points the i block of the file
The directory table stores the addresses of the index block.

Supports direct access to the blocks
Like the linked allocation, this one doesn't suffer of external fragmentation.
Space is wasted with the allocation of index blocks.
- Consider a file with just two blocks:
- In the linked allocation, space is lost by one word by block because of the storage of the pointer. 
- In indexed allocation, a whole block is allocated to store the index block.

## Directory Structure
Is the way a system organizes the files logically the various files store in disk.
The directory is a structure of data that the entries are associated with files.
When a file in opened, the OS uses the name of the path provided by the user to find its entry in the directory structure.
The entry provides information necessary to find the file blocks.
Depending on the system this information can be: 
- The first address of the whole file (continuous).
- The first address of the first block (linked).
- The index block address (indexed).

#### Single Level Directory
Simpler way, only one root directory that has all files.
User management is hard if it has too many files. If the system has many users, the problem aggravates. Naming and grouping files is also a problem.

Used on embedded system like digital cameras.
#### Two Levels Directory
Creates a directory to each user (User File Directory - UFD) and a master directory (Master File Directory - MFD).
The MFD is indexed by user name or user id.
Each entry in the MFD points to a user directory.

Eliminates the conflicts between names of files of different users.
The UFD still has problems organizing, because it works like a single level.

#### Tree Directory
Each user can have as many directories as it is needed, allowing to group files in a better way.
Each user has a directory:
- If the file is not in the current directory, it must specify a path.
- Path names can be relative or absolute.
- A user can access files of other users.

Used by the majority of operating systems.

## Monitoring Free Blocks
To control the free space in the disk, the system keeps a list of freed blocks
#### Bit Maps
The free blocks can be mapped used a bit vector, each bit represents a block, if the bit is set to 1, the block is free, if 0 the block is used.

#### Linked List
Freed blocks are kept in a linked list.
There is no space problem in the main memory, because it doesn't need a allocation table.
It takes longer to find free blocks, because the list must be scrolled through.
- Wastes more time with I/O
- Loses a space next to the block to store the address to the next.