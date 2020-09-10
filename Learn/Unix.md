# Unix

## Standard Input and Output

- Every Program on Unix system can read from the standard input device (stdin) and write to standard output (stdout) 
- By default stdin comes from the Keyboard and stdout gets printed to graphical display.

## Organisation 
- The UNIX operating system is organised in a 3 layer model
    - Layer 1: Kernel (Talk to hardware and manager resources)
    - Layer 2: Shell (Lets user run and interact with Kernel programs)
    - Layer 3: Utilities (Collection of programs which can be reused to do certain frequently occurring tasks)

### Kernel 
- Mediate access to system resources
- Switch between different types of users.
- CPU Scheduling
- I/O to the computer hardware
- Memory 
- Allow standardised interface to lot of hardware like Keyboard and Mouse, Network Card.

**syscall and posix**
// Define about syscall and Posix



> Program request resources from Kernel by making (syscall) System Call.

