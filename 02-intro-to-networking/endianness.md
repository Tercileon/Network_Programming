<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Endianness

A number is represented by a sequence of bytes. A 32 bit integer is 4 bytes.

* Least Significant Byte \(LSB\)- The byte representing the smallest part of a number \(e.g. the "ones"\)
* Most Significant Byte \(MSB\) The place representing the largest part of a number

Endianness tells us how to read a grouping of bytes.

* Big Endian - MSB is first
* Little Endian - LSB is first

![](/assets/Endianness_example.png)

## **00xDEADBEEF \(4 bytes\)**

* Little Endian - 0xEF, 0xBE, 0xAD, 0xDE
* Big Endian - 0xDE, 0xAD, 0xBE, 0xEF

### Network byte order is Big Endian

### x86/x86\_64 are Little Endian

### Know what endian your data is in or you will have problems with binary data

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/02-intro-to-networking/rfcs-pydocs-man-pages/README.md" > Continue to Next Topic </a>
