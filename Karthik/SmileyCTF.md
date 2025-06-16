 Smiley CTF Report – fORtran file(binary reverse engineering)
 
We were given an unknown file named fORtran without source code or documentation. While i was not able to get the flag, this writeup contains everything i learnt and used in the process.

Strings 
fORtran | grep -i gfortran
This showed that the program was written in Fortran..this was obvious with the file name but i still did this step for confirmation.

Running the Program
./fORtran
Observation: It prompts for a key: but provides no output for valid or invalid inputs.

I learnt how to use GREP : GLOBAL REGULAR EXPRESSION PRINT to find patterns in text (command prompt ubuntu)
Used to find patterns in files
Use -i for case insensitivity

Strace- system call tracer
I tried using it and saw how the interaction between the system and the file happened. I noticed that it prompted for a key, it uses system calls like read and write
I observed the flow of execution from the OS side
I learnt how to observe different key calls like read(), write(), etc.
I Understood that the binary wasn’t doing anything malicious (like accessing files or spawning shells).

Ltrace for dynamic analysis
I used to Ltrace to track I/O logic flow…I inputted A and B and then observed.
ltrace ./fORtran
echo "A" | ltrace ./fORtran > a.log 2>&1
echo "B" | ltrace ./fORtran > b.log 2>&1
diff a.log b.log
I noticed that:
the same Fortran runtime functions are used for both inputs.
A stop function is always reached, possibly halting the program after the first input read.

