<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Buffers

Working with binary packed data is typically reserved for highly performance sensitive situations or passing data into and out of extension modules. In such situations, you can optimize by avoiding the overhead of allocating a new buffer for each packed structure. The pack\_into\(\) and unpack\_from\(\) methods support writing to pre-allocated buffers directly.

```text
import struct
import binascii

s = struct.Struct('I 2s f')
values = (1, 'ab', 2.7)
print 'Original:', values

print
print 'ctypes string buffer'

import ctypes

b = ctypes.create_string_buffer(s.size)
print 'Before  :', binascii.hexlify(b.raw)

s.pack_into(b, 0, *values)
print 'After   :', binascii.hexlify(b.raw)
print 'Unpacked:', s.unpack_from(b, 0)

print
print 'array'

import array

a = array.array('c', '\0' *s.size)
print 'Before  :', binascii.hexlify(a)

s.pack_into(a, 0, *values)
print 'After   :', binascii.hexlify(a)
print 'Unpacked:', s.unpack_from(a, 0)
```

The  _size_  attribute of the Struct tells us how big the buffer needs to be.

```text
$ python struct_buffers.py

Original: (1, 'ab', 2.7)

ctypes string buffer
Before  : 000000000000000000000000
After   : 0100000061620000cdcc2c40
Unpacked: (1, 'ab', 2.700000047683716)

array
Before  : 000000000000000000000000
After   : 0100000061620000cdcc2c40
Unpacked: (1, 'ab', 2.700000047683716)
```

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/endianess.md" > Continue to Next Topic </a>
