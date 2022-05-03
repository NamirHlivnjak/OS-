# OS- PROJECT

Project: Shell & N-A (Amela & Namir Shell)
TASK >  Implementation of a Shell in C program
Group members : 1. Amela Redžić
                2. Namir Hlivnjak
FILE :  shell.c

Q1: Do the following actions require the OS to use kernel mode or user mode is sufficient?
    Explain:
            1. A program wants to read from disk.
            2. Reading the current time from the hardware clock.

--- READ ---
        A program requests that data be read from the hard drive. A hardware connection is normally required for a read. Hardware access takes time and is prone to errors, and it may render the computer unusable. Drivers are used by the operating system to control the hardware of the computer. When a driver receives a read, it sends a series of instructions to the disk controller, telling it to read the output, pass it to main memory, and so on. In User Mode, these are potentially risky operations that should never be undertaken.

--- HARDWARE CLOCK ---
        To obtain the current time, the hardware clock is used. If the hardware clocks include memory-mapped registers, you can read them from user mode as long as the mapped region does not contain sensitive data.



Q2: Explain the purpose of a system call. There are different sets of system calls: list them and give at least 2 examples of a system call for each category.
--- SYSTEM CALL ---
           A system call is a way for a running software to communicate with the operating system. It allows the user to take advantage of the services provided by the operating system. These system calls use C, C++, and assembly language processes. Each operating system has its own name for each system call. To identify each system call, it is given a unique number.


System calls: 
1. Procces Control:
    The execution of a program is a procedure. A process must initially be loaded into main memory before it can be executed. It may be necessary to wait,        terminate, or start and stop child processes while it is running.
    Examples of Unix/Windows:
        # fork()/CreateProcess()
        # wait()/WaitForSingleObject()
        # exit()/ExitProcess()

2. File Managment :
    We can generate and erase files thanks to technological advancements. The file's name and other characteristics are necessary for the creation and deletion actions. File characteristics include details such as file type, size, security codes, and accounting information. These properties are used by systems to conduct operations on files and directories. We can open and use the file once it has been created. The system also allows for file activities such as reading, writing, and relocating.
    Examples of Unix/Windows:
        # open()/CreateFile()
        # read()/ReadFile()
        # write()/WriteFile()
        # close()/CloseHandle()


3. Device Managment : 
    When a process is running, it requires the utilization of a variety of resources to fulfill its task. Main memory, hard drives, data, and so on are examples of these resources. The resource is assigned to the process if it is available. The process can read, write, and relocate the resource once it has been assigned to the device.
    Examples of Unix/Windows:
        # read()/ReadConsole()
        # write()/WriteConsole()
        # ioctl()/SetConsoleMode()


4.  Information Maintenance:
    System calls are used to communicate data between a user software and the operating system. The current date and time, the number of active users, the operating system version number, the quantity of free memory or disk space, and so on are all examples of system information. The operating system uses system services like get process characteristics and update program characteristics to keep track of all of its processes.
    Examples of Unix/Windows:
        # getpid()/GetCurrentProcessID()
        # alarm()/SetTimer()
        # sleep()/Sleep()


5. Communication:
    The system's processes communicate with one another. Message queue and shared memory are the two communication models. The sender process connects to the receiving process by providing the receiving process name or identity for message transfer. When the discussion is finished, the system disconnects the communicating processes.
    Examples of Unix/Windows:
        # pipe()/CreatePipe()
        # mmap()/MapViewOfFile()
        # shmget()/CreateFileMapping()


Outline of the Assignment
    
    In the explanation, we'll go over all of the main pieces (commands) that were used in the shell's implementation.

cp

This command copies files, groups of files, or directories. *Options: *

    1. -i(interactive): The letter I stands for interactive copying. The system tells the user about this option before overwriting the target file.
    2. -b(backup): When this option is utilized, the cp command creates a backup of the destination file in the same folder.
    3. -f(force): If the system cannot open the destination file because the user does not have writing permission, the -f option is used to first destroy the file before copying the content from the source to the destination.
    4. -r or -R: The structure of the directory is being replicated. With this option, the cp command duplicates the entire directory structure recursively.
    5. -p(preserve): When using the -p option, Cp keeps the properties of each source file (permission bits, ownership, and so on) in the matching destination file.


 - - - history - - - 

The history command is used to see what commands have been run previously.

Options:

    1. -d offset: Delete the history entry at offset OFFSET
    2. -r: Read the contents of the history file and add them to the history list.
    3-n: Read all history lines from the history file that haven't already been read.
    4. -s: Add the ARGs as a single entry to the history list.
    
- - - free - - -

The free command shows the total amount of free space on the system, as well as the amount of memory used, swap memory, and kernel buffers.

Options:

    1. -b, bytes: It shows the amount of memory in bytes.
    2. -k, kilo: It shows how much memory you have in kilobytes.
    3. -t, total: It adds a line to the output that shows the column totals.
    4. -lp: It displays a help message and exit.


- - - fortune/ Random Quotes Randomly displays frightening, uplifting, silly, or sarcastic statements from a quotation database. - - -

Options:

    1. -e: Make the chance of picking a fortune file equal to the chance of picking any other file.
    2. -i: Make regular expression searching case-insensitive when used with -m.
    3. -o: Only use databases that are "offensive."
    4.-w: Wait a certain amount of time before terminating; this is important in instances when a fortune must be read before the screen is cleared.


- - - vfork - - -

    Vfork() is a method for starting a new process. Because both processes share the same address space, the child process suspends the parent process's execution until the child process is finished, whereas the fork() child and parent processes have separate memory regions.

- - - vfork bomb - - -

    A fork bomb is a sort of DoS attack that targets a Linux system. It forks processes endlessly to fill memory.

Instructions for compiling
    gcc shell.c -o shell
    ./shell



Challenges
    Lack of knowledge and resources
    Difficulties in finding resources
    
    https://www.guru99.com/introduction-to-shell-scripting.html

    https://securitronlinux.com/bejiitaswrath/very-useful-c-program-print-a-random-fortune/

    https://tuxthink.blogspot.com/2012/12/c-program-in-linux-to-find-username-of.html



