## Architecture of the Unix Operation System
* two central concepts
    1. files - file system has "places"
    2. processes - processes has "life"

* three level:
    1. user
        * `system call` or `sophisticated library` represents the `border` between user programs and the kernel
        * libraries are `linked` with programs at `compile` time
    2. kernel
    3. hardware 

### file subsystem:
Purpose:
1. allocate file space
2. administer free space
3. control access to file
4. retrieve data for user

Data Structure used in file system:
1. User file descriptor table (per process)
2. File table (kernel global)
  * keep track of byte offset
3. Inode table (kernel global)
  * in-core inode
4. Inode (index node)
  * disk layout
  * access permission
  * owner
  * stored in file system


Kernel deals on `logical level` with file system rather than with disks, treating each one as a `logical device` identified by `logical device number`

A file system consist of a `sequence` of `logical blocks` (512K, 1024K,... multiple of 512 bytes)

A file system structure:
1. boot block
  * may contain bootstrap code
2. super block
  * how large
  * where to find free space
3. inode list
  * kernel references inodes `by index` into the inode list
4. dat blocks
  * file data and administrative data
  * can only belong to one file

* buffer mechanism
Regulate data flow between the kernel and secondary storage devices
    * Block I/O devices are `random access storage device`
    * Raw devices are character devices, include all devices that are not block devices

* process control subsystem:
    1. process synchronization
    2. interprocess communication
    3. memory management
        * If at any time the system does not have enough physical memory for all processes, the kernel moves them between main memory and secondary memory
    4. process schedule

