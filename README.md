# G15-software

The **G15-software** project maintains source code and software artifacts for the Bendix G-15, a 1950s binary, vacuum tube, drum-memory computer system. A software emulator for this system is available in the [retro-g15 GitHub repository](https://github.com/pkimpel/retro-g15/). The emulator is web browser-based and can be run from its [hosting site](http://www.phkimpel.us/Bendix-G15/).

Contributions of new material and corrections to existing material for this repository are most welcome. Please submit a pull request.

Files are organized in top-level directories by program or application and origin. Each top-level directory contains a `README.md` file describing the contents and their provenance.

Most G-15 software was maintained and distributed as object code on five-level paper tape. This project has standardized on the ASCII representation of those binary tapes used by the retro-g15 emulator above and originated by David Green for his G-15 emulator. A basic G-15 system could input and output only hexadecimal data, using the representation 0-9 and u-z instead of the more common 0-9, a-f convention. The paper tape format reflects that limitation.

The ASCII convention used by this project for paper tape is as follows. Note that if the fifth bit is zero, then the fourth bit is ignored, and the remaining three bits represent a binary control or punctuation code. The file name extension for these files should be `.pti`.

|ASCII|Binary|Meaning|
|:-:|:-----:|:-------|
|` `|`0x000`|Space (ignored on input by the reader)|
|`-`|`0x001`|Minus Sign|
|`C`|`0x010`|Carriage Return|
|`T`|`0x011`|Tabulate|
|`S`|`0x100`|Stop (end of block, halts the reader)|
|`/`|`0x101`|Reload|
|`.`|`0x110`|Period ("P" is also accepted on input)|
|`~`|`00111`|Wait|
|`0`|`10000`|Digit 0|
|`1`|`10001`|Digit 1|
|`2`|`10010`|Digit 2|
|`3`|`10011`|Digit 3|
|`4`|`10100`|Digit 4|
|`5`|`10101`|Digit 5|
|`6`|`10110`|Digit 6|
|`7`|`10111`|Digit 7|
|`8`|`11000`|Digit 8|
|`9`|`11001`|Digit 9|
|`u`|`11010`|Digit 10 (hex A)|
|`v`|`11011`|Digit 11 (hex B)|
|`w`|`11100`|Digit 12 (hex C)|
|`x`|`11101`|Digit 13 (hex D)|
|`y`|`11110`|Digit 14 (hex E)|
|`z`|`11111`|Digit 15 (hex F)|

The letter codes above are case-insensitive. Either the upper- or lower-case ASCII characters may be used. Any characters in the file other than those specified above should be considered to be meaningless and ignored on input. For readability, an ASCII new-line sequence should follow each Reload or Stop code, but this is not required.

Paper tape input to the G-15 was prepared in blocks of no more than 108 words, consisting of 28 mantissa bits (seven hex digits) and a sign bit. A Stop code terminated the block and turned off the reader. Within a block, the data had to be organized in groups of no more than four words followed by a Reload code. This arrangement was necessary to accommodate the speed of the G-15's drum memory and its buffering mechanism.

The Space and Period characters were only used for output and were ignored on input. The Minus Sign indicated a word was negative and could be placed at any position within a word's hexadecimal digits. Non-negative words were indicated by the absence of a sign. The Carriage Return and Tabulate codes signaled the end of digits for a word and caused the sign to be stored in its proper position as the low-order bit in the word. Thus, leading zeroes did not need to be present on the tape. A Wait code was not commonly used. On output, it indicated that formatting codes had skipped over a digit from memory when the tape was punched. On input, it was treated the same as a Digit 0.

For more information on G-15 paper tape formatting and operations, see the _[G-15 Paper Tape Format](http://bitsavers.org/pdf/bendix/g-15/G15_PaperTapeFormat_Jan58.pdf)_ document and the _[G-15 Operating Manual](http://bitsavers.org/pdf/bendix/g-15/G15_Operating_Man_Jul59.pdf)_.

For a sample script that converts one form of binary tape image to the convention cited here, see https://github.com/pkimpel/retro-g15/blob/master/software/tools/Pierce-Paper-Tape-Decoder.html.

Source code, if supplied, should be in the form of ASCII or UTF-8 text files. Lines in the files may be delimited by either an ASCII line-feed (hex 0A) or a carriage-return/line-feed pair (hex 0D0A).

Binary data, such as original tape images, should be supplied in the form of zip (.zip) or G-zipped (.gz) or G-zipped tar (.tar.gz) files.
