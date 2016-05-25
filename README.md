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

The string function 'left' illustrates a lot of points about using vectors as strings: - 
 
    let left(S,L) = VALOF
    $(
     //return the left ## number of characters
     //if ## is greater than string size return the string as is
     
     let size, vector = 0,0 *1
     
     size := S%0 *2
     
     IF size < L THEN L :=size *3
     
     vector := GETVEC(L/2) *4
     
     FOR N = 0 TO L DO
      vector%N := S%N *5
      
      vector%0 :=L *6
     
     RESULTIS vector *7
    
    $)
    

1 - this defines the variables we will use later

2 - this extracts the size of the string (S) passed into the function as the 0th byte of the string holds the length in bytes

3 - this is a check to make sure that we don't try to take more characters from the left of the string than are present

4 - calls the GETVEC command to convert the variable 'vector' into an actual vector. Note that the vector size is the numebr of bytes divided by 2 as there are two bytes per BCPL word and there is no point wasting RAM

5 - set the byte of new vector equal to the byte of the original vector (string S). This lookps through L (number of bytes to copy) times

6 - set the length of the new vector to L so that if we print the string out or work with it we know where it ends

7 - return the resulting vector to the caller


