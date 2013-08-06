rc4-prbs
========

A [Verilog](http://en.wikipedia.org/wiki/Verilog) open-source implementation of a RC4 encryption algorigthm using a pseudorandom binary sequence ([PRBS](http://en.wikipedia.org/wiki/Pseudorandom_binary_sequence)) for [FPGA](http://en.wikipedia.org/wiki/Fpga) synthesis.


#Why?

I was looking for a quick implementation of [RC4](http://en.wikipedia.org/wiki/RC4) and I couldn't find one, 
so I wrote one based on the wikipedia example.

#Usage

It's quite easy to use:

    1) First, issue rst
    2) Load the password byte-by-byte into the password\_input port. The lenght of the password is KEY\_SIZE
    3) Issue 768 clocks to perform key expansion
    4) Wait 1536 clocks while the module discards the first 1536 weak bytes of the stream (as per rfc4345.txt).
    5) Now you should start receiving the pseudo-random stream via the output bus, one byte every clock. 
       The output\_ready signal signals when a valid byte is present at the output K.

To encrypt or decrypt using RC4 you simply xor your data with the output stream.


#How to test

The testbench and makefile work using icarus verilog and you can peer into rc4\_tb.v to see an example implementation. 
After installing icarus verilog in your path, just issue:

    make
    ./rc4.vvp

And you should see the output of the simulation.

#Credits

Any question or suggestion send an email to Alfredo Ortega at (alfred@groundworkstech.com / aortega@alu.itba.edu.ar)

#Lincense

RC4-PRBS
Copyright (c) 2013, Groundworks Technologies, All rights reserved.

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 3.0 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library.

