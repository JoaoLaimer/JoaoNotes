Is the technique in memory managing where the space of virtual addressing, is divided in blocks of different sizes called segments. A program is divided logically in sub-routines and data structures, that are allocated in segments in the main memory.
The main difference between paging and segmentation is:
- In paging the program is split in pages of fixed sizes without any connection with its structure. 
- Segmentation allows the relation between the logic of the program and its parts in memory.

The definition of a program segments is done by the compiler, the virtual addressing space of a process has a maximum number of segmentes, each segment can varie with the size limit.  The size of each segment can be altered during execution. 
Independent addressing spaces allow a sub-routine to be altered without the necessity to recompile the main program and its sub-routines.

Segments have their own independent addressing space.

Mapping mechanism is similar to the paging one, in this case the segments are mapped though segment tables.
Each process has its own process segmentation table.
- Virtual addresses are composed by the number of virtual segment and an offset.
- The number of the virtual segment identifies the entry in the segment table that has the address of the physical segment.
- The offset says the position in the relation of the initial address of the segment.
- The physical address is the combination of the segment address and the offset.

Each entry of the segment table has additional information such as:
- Size: size of a segment
- Valid Bit: If set, the segment is in the main memory.
- Modification Bit: If set, the segment has been altered.
- Reference bit: if set, the segment was referenced recently.
- Protection bit: tell us which kind of access we are making to the segment.

An advantage segmentation has over paging is:
- The ease of handling dynamic data structures.
- The size of segment can be easily altered.
- In paging, the expansion of an array implies in allocating more pages, and consequently, changing the page table.
Different to paging, segmentation doesn't have internal fragmentation, but has external fragmentation, when new areas are not big enough to allocate new segments.

Only referenced segments are loaded to the main memory.
If applications are not developed in modules, big segments will be loaded to the main memory unnecessarily.
To allocated segments to the main memory, the OS keeps the information with the freed and occupied areas of the memory.
When a new segment is referenced, the OS selects a free space that fits the segment to be allocated.
We can adopt the best-fit, first-fit or worst-fit policies.

## Segmentation with Paging
Has the objective of combining both approaches.
- Paging avoids external fragmentation.
- Segmentation is easier to deal with the dynamic data structures, because the size of the segment can be altered.

- Shares the virtual addressing space with the segments
- Each segment is split into pages
- In the programmers eye, his application is still mapped in different sized segments.
- The system treats each segment as a set of same size pages, with this, a segment doesn't need to be continuous in the memory and eliminates the problem of external fragmentation.

A virtual address is built by:
- Virtual segment number
- Virtual page number
- Offset
