<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Struct Module

Struct allows you to pack values into specified data types/sizes and endianess. Packed data is represented by a string of hex bytes. Struct will also unpack data from the hex string and provide you a tuple of the values.

Packing is used to prepare structured binary data such as a protocol header or a message format. This data can then be referenced like a struct in C, or sent across the wire.

It uses a format string and variable arguments \(like print or printf in C\)

`>>> from struct import *`

`>>> pack('hhl', 1, 2, 3)`

`'\x00\x01\x00\x02\x00\x00\x00\x03'`

`>>> unpack('hhl', '\x00\x01\x00\x02\x00\x00\x00\x03')`

`(1, 2, 3)`

## Functions vs. Struct Class

There are a set of module-level functions for working with structured values, and there is also the Struct class \(new in Python 2.5\). Format specifiers are converted from their string format to a compiled representation, similar to the way regular expressions are. The conversion takes some resources, so it is typically more efficient to do it once when creating a Struct instance and call methods on the instance instead of using the module-level functions. All of the examples below use the Struct class.

## Packing and Unpacking

Structs support\_packing\_data into strings, and\_unpacking\_data from strings using format specifiers made up of characters representing the type of the data and optional count and endianess indicators. For complete details, refer to the standard library documentation.

In this example, the format specifier calls for an integer or long value, a two character string, and a floating point number. The spaces between the format specifiers are included here for clarity, and are ignored when the format is compiled.

```text
import struct 
import binascii

values = (1, 'ab', 2.7)
s = struct.Struct('I 2s f')
packed_data = s.pack(*values)

print 'Original values:', values
print 'Format string  :', s.format
print 'Uses           :', s.size, 'bytes'
print 'Packed Value   :', binascii.hexlify(packed_data)
```

The example converts the packed value to a sequence of hex bytes for printing with binascii.hexlify\(\), since some of the characters are nulls.

```text
$ python struct_pack.py

Original values: (1, 'ab', 2.7)
Format string  : I 2s f
Uses           : 12 bytes
Packed Value   : 0100000061620000cdcc2c40
```

If we pass the packed value to unpack\(\), we get basically the same values back \(note the discrepancy in the floating point value\).

```text
import struct
import binascii

packed_data = binascii.unhexlify('0100000061620000cdcc2c40')

s = struct.Struct('I 2s f')
unpacked_data = s.unpack(packed_data)
print'Unpacked Values:', unpacked_data
```

```text
$ python struct_unpack.py

Unpacked Values: (1, 'ab', 2.700000047683716)
```

### See also:

**struct:** The standard library documentation for this module.  [https://docs.python.org/2.7/library/struct.html](https://docs.python.org/2.7/library/struct.html%29%29\)

**array:** The array module, for working with sequences of fixed-type values.  [https://docs.python.org/2/library/array.html](https://docs.python.org/2/library/array.html%29%29\)

**binascii:**  The binascii module, for producing ASCII representations of binary data.

[https://docs.python.org/2/library/binascii.html](https://docs.python.org/2/library/binascii.html%29%29%29\)

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/encode-decode.md" > Continue to Next Topic </a>
