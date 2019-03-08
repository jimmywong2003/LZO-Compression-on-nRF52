# LZO-Compression-on-nRF52

## Lossless Compression Algorithm Overview

* Run-length encoding (RLE) – Simple scheme that provides good compression of data containing lots of runs of the same value
* Huffman coding – Pairs well with other algorithms, used by Unix's pack utility
* Prediction by partial matching (PPM) – Optimized for compressing plain text
* bzip2 – Combines Burrows–Wheeler transform with RLE and Huffman coding
* Lempel-Ziv compression (LZ77 and LZ78) – Dictionary-based algorithm that forms the basis for many other algorithms



## Show how to use the LZO compression / decompression library on nRF52 Series

This demo is to add the miniLZO compression / decompression library on the nRF52 series.

miniLZO is a very lightweight subset of the LZO library intended for easy inclusion with your application. It is generated automatically from the LZO source code and contains the most important LZO functions.

Very easy to use - it only takes a few minutes to add data compression to your application!

## Memory Usage:

### Algorithm size:
Flash : 3.5KB

### Worst RAM buffer

* Input buffer: IN_LEN 
* Output buffer: (IN_LEN + IN_LEN / 16 + 64 + 3)
* Dictionary table (64KB) – working memory for dictionary (Compression need only)


## Requirement

Nordic SDK 15.3 

Softdevice : S132v6.1.1 / S140v6.1.1

HW: NRF52832 DK / NRF52840 DK


## Note

The project may need modifications to work with later versions or other boards. To compile it, clone the repository in the /nRF5_SDK_15.3.0/examples/ directory. The application is built to be used with the official nRF5 SDK that can be downloaded from developer.nordicsemi.com

Refer to the URL: http://www.oberhumer.com/opensource/lzo/


========================
### miniLZO -- mini subset of the LZO real-time data compression library


 Author  : Markus Franz Xaver Johannes Oberhumer
           <markus@oberhumer.com>
           http://www.oberhumer.com/opensource/lzo/
 Version : 2.06
 Date    : 12 Aug 2011

 I've created miniLZO for projects where it is inconvenient to
 include (or require) the full LZO source code just because you
 want to add a little bit of data compression to your application.

 miniLZO implements the LZO1X-1 compressor and both the standard and
 safe LZO1X decompressor. Apart from fast compression it also useful
 for situations where you want to use pre-compressed data files (which
 must have been compressed with LZO1X-999).

 miniLZO consists of one C source file and three header files:
    minilzo.c
    minilzo.h, lzoconf.h, lzodefs.h

 To use miniLZO just copy these files into your source directory, add
 minilzo.c to your Makefile and #include minilzo.h from your program.
 Note: you also must distribute this file ('README.LZO') with your project.

 minilzo.o compiles to about 6 KiB (using gcc or Visual C on an i386), and
 the sources are about 30 KiB when packed with zip - so there's no more
 excuse that your application doesn't support data compression :-)

 For more information, documentation, example programs and other support
 files (like Makefiles and build scripts) please download the full LZO
 package from
    http://www.oberhumer.com/opensource/lzo/

 Have fun,
  Markus


 P.S. minilzo.c is generated automatically from the LZO sources and
      therefore functionality is completely identical


 Appendix A: building miniLZO
 ----------------------------
 miniLZO is written such a way that it should compile and run
 out-of-the-box on most machines.

 If you are running on a very unusual architecture and lzo_init() fails then
 you should first recompile with '-DLZO_DEBUG' to see what causes the failure.
 The most probable case is something like 'sizeof(void *) != sizeof(size_t)'.
 After identifying the problem you can compile by adding some defines
 like '-DSIZEOF_VOID_P=8' to your Makefile.

 The best solution is (of course) using Autoconf - if your project uses
 Autoconf anyway just add '-DMINILZO_HAVE_CONFIG_H' to your compiler
 flags when compiling minilzo.c. See the LZO distribution for an example
 how to set up configure.ac.


 Appendix B: list of public functions available in miniLZO
 ---------------------------------------------------------
 Library initialization
    lzo_init()

 Compression
    lzo1x_1_compress()

 Decompression
    lzo1x_decompress()
    lzo1x_decompress_safe()

 Checksum functions
    lzo_adler32()

 Version functions
    lzo_version()
    lzo_version_string()
    lzo_version_date()

 Portable (but slow) string functions
    lzo_memcmp()
    lzo_memcpy()
    lzo_memmove()
    lzo_memset()


 Appendix C: suggested macros for 'configure.ac' when using Autoconf
 -------------------------------------------------------------------
 Checks for typedefs and structures
    AC_CHECK_TYPE(ptrdiff_t,long)
    AC_TYPE_SIZE_T
    AC_CHECK_SIZEOF(short)
    AC_CHECK_SIZEOF(int)
    AC_CHECK_SIZEOF(long)
    AC_CHECK_SIZEOF(long long)
    AC_CHECK_SIZEOF(__int64)
    AC_CHECK_SIZEOF(void *)
    AC_CHECK_SIZEOF(size_t)
    AC_CHECK_SIZEOF(ptrdiff_t)

 Checks for compiler characteristics
    AC_C_CONST

 Checks for library functions
    AC_CHECK_FUNCS(memcmp memcpy memmove memset)


 Appendix D: Copyright
 ---------------------
 LZO and miniLZO are Copyright (C) 1996, 1997, 1998, 1999, 2000, 2001,
 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010, 2011
 Markus Franz Xaver Oberhumer <markus@oberhumer.com>.

 LZO and miniLZO are distributed under the terms of the GNU General
 Public License (GPL).  See the file COPYING.

 Special licenses for commercial and other applications which
 are not willing to accept the GNU General Public License
 are available by contacting the author.

