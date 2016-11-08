# TuringMachines -> Project name -> “This is literally a fucking microprocessor implemented as a Turing Machine, FML”

This project can be somewhat divided into 3 parts ->

1) Implement a Turing Machine simulator in Python, with a graphical represention.  Probably load Turing Machines and starting input from a YAML file
2) Create Turing Machines to perform basic opperations on ~5 Registers and infinite memory -> These basic opperations will be representable with basic assembly instructions.  How many and which ones are still TBD.
3) Create a Turing Machine that will incorporate the previously designed machines together, and essentially just run the assembly instructions.  This machine will basically simulate a microprocessor that runs assembly code.

Some useful things that I have decided about this project:
  The tape will be the language of integers, [probably smaller than 2^12 (could be modeled as a 12 bit uint)]
  Programs must be formatted as follows:
    The first value on the tape contains the length (number of instructions) of the program.
    The actual input to be read will begin directly after the program ends on the tape
    The user definable RAM will be all values more than 5 places Left of the start of the program
    The 5 places to the left of the program will be to hold the contents of the registers every time that I do something with the RAM.
       They are written to every time that I journey into the RAM, and they are read from every time that I leave the RAM
       
  The registers are to be used as follows:
    R1 -> The program counter... it says how many instructions into the program we are. This can be modified by the user, essentially a goto
    R2 -> Where we actually are in the tape
    R3 -> User defined
    R4 -> User defined
    R5 -> User defined
    
  The assembly instructions to be used as follows: (Each instruction will be in the form of a number representing which instruction it is, followed by 3 arguements)
    Load constant into register (1,Constant,Register to load to, Blank)
    Load RAM into register (2,Register W/ RAM Location, Register to load to, Blank)
    Add two registers and store result in third register (3, Register 1, Register 2, Register 3)
    Subtract register 1 from register 2 and store the result in register 3 (4, Register 1, Register 2, Register 3)
    Branch to location stored in register 3 if register 1 and 2 are equal (5, Register 1, Register 2, Register 3) // Branch automatically is implicit in the ability to load values to the program counter
    
