# BCPLLibraries2

More functions and a look at vectors.

This version of the strings library includes the following common string functions: -

 . Length
 . Concat
 . Left
 . Right
 . Mid
 . IndexOf

This compiles in the same way as Libraries 1, from drive 0: - 

    BCPL strings LIBstr
    *drive 1
    save LIBStr

To use this with strtest: - 

    BCPL strtest tmp 
    *drive 1 
    SAVE tmp 
    NEEDCIN tmp LIBSTR exe 
    *destroy tmp

When run this shows the examples of using the function calls.

Strings and vectors: - 

A string is basically a vector, which is a one dimensional array of BCPL words. Note that a BCPL word on the Beeb is 2 bytes.

The string 'Hello World!' contains 12 characters which would require 6 words in a vector. In a string vector the first byte of the first word holds the length of the string and therefore the length can be accessed by a call such as vector%0 where vector is the name of the string.

There is a program vecshow which lists the contents of a vector a byte at a time to illustrate this. It requires needcin as it uses the VDU command.

To build and run this from drive 0: - 

    BCPL vecshow veccode
    *drive 1
    save veccode
    NEEDCIN veccode lib vecexe
    *destroy veccode

More to follow about vectors!
