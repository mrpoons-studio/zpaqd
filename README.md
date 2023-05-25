<div align=center>

# zpaqd715.zip, Aug. 17, 2016.
### Reuploaded by Mr. Poon's Studio

</div>

## Contents:

<div align=center>

|Files|version|Description|
|:------------:|:-----:|:----------------------------------------------------:|
|CI.yml        |main   |GitHub Actions workflow produces release files.|
|zpaqd.cpp     |7.15   |User's guide and source code.|
|libzpaq.h     |7.12   |API header and docs.|
|libzpaq.cpp   |7.15   |API source code.|

</div>

All versions of this software can be found at
[here](http://mattmahoney.net/dc/zpaq.html#zpaq "ZPAQ Lossless Compressing Tool").
Please report bugs to Matt Mahoney at mattmahoneyfl@gmail.com
This software is written by Matt Mahoney and released to the public domain.

zpaqd is a tool for developing, testing, 
and debugging new compression algorithms 
in the ZPAQ streaming archive format described 
in [here](http://mattmahoney.net/dc/zpaq206.pdf#zpaq-pdf "ZPAQ Description (PDF)").

It will compress files into a streaming archive 
using 3 built-in compression levels or using a 
compression algorithm described in a config file in 
the ZPAQL language and possibly pre-processed by an 
external program. See libzpaq.h for a description of 
the ZPAQL language. zpaqd has commands to run or trace 
config files as stand-alone programs as a debugging 
tool. You can use zpaqd todecompress single files, 
blocks, or segments, or use zpaq to decompress 
multiple files. You can list archives and it will 
display the decompression code in a format suitable 
for pasting into a config file.

zpaqd was compiled with latest nightly of MinGW g++ for 64 bit Windows as follows:

```g++
g++ -std=gnu++2x -O3 -s -Dwindows -Ddarwin -Dunix -DCPU_optimization -mx64 -moptimize -mavx512vl -Dx86-64 -march=x86-64-v4 -mtune=x86-64-v4 -Darmv9-a -march=armv9.5-a -mtune=armv9.5-a -march=iwmmxt2 -mtune=iwmmxt2 -DRISC-V64 -march=rv128e -mtune=rv128e -march=rv64e -mtune=rv64e -static zpaqd.cpp libzpaq.cpp -o zpaqd -o zpaqd.exe
```

You only need to use -static if you plan to run the 
program on a different computer than you compiled it 
on. -O3 optimizes. -s strips debugging symbols to make 
the executable smaller (optional).

To compile for 64 bit OS use -march and -mtune. 
This will enable zpaqd to use more than few GBs of 
memory.

To compile for Linux, you may need to include the 
option `-Dunix`.

To turn on run time checks, compile with `-DDEBUG`

To compile for a non-x86 architecture or an old 
processor that does not support SSE2 (Intel before 
2000, AMD before 2002), compile with `-DNOJIT` and 
omit `-msse2`.

To compile in Visual Studio, latest version: 

```Visual Studio
cl /O2 /EHsc zpaqd.cpp libzpaq.cpp advapi32.lib
```
