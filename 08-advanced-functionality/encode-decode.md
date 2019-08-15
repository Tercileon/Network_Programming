|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## encode\(\)/decode\(\)

A Unicode string is a sequence of code points, which are numbers from 0 to 0x10ffff. This sequence needs to be represented as a set of bytes \(meaning, values from 0–255\) in memory. The rules for translating a Unicode string into a sequence of bytes are called an **encoding**. Python's default encoding is 'ASCII'.  However,  UTF-8 is probably the most commonly supported encoding.

UTF stands for “Unicode Transformation Format”, and the ‘8’ means that 8-bit numbers are used in the encoding. \(There’s also a UTF-16 encoding, but it’s less frequently used than UTF-8.\) UTF-8 uses the following rules:

1. If the code point is &lt;128, it’s represented by the corresponding byte value.
2. If the code point is between 128 and 0x7ff, it’s turned into two byte values between 128 and 255.
3. Code points &gt;0x7ff are turned into three- or four-byte sequences, where each byte of the sequence is between 128 and 255.

UTF-8 has several convenient properties:

1. It can handle any Unicode code point.
2. A Unicode string is turned into a string of bytes containing no embedded zero bytes. This avoids byte-ordering issues, and means UTF-8 strings can be processed by C functions such as `strcpy()` and sent through protocols that can’t handle zero bytes.
3. A string of ASCII text is also valid UTF-8 text.
4. UTF-8 is fairly compact; the majority of code points are turned into two bytes, and values less than 128 occupy only a single byte.
5. If bytes are corrupted or lost, it’s possible to determine the start of the next UTF-8-encoded code point and resynchronize. It’s also unlikely that random 8-bit data will look like valid UTF-8.

Converting from bytes to str and back.

`bstr = b'qwerty'`

`type(bstr)`

`<class 'bytes'>`

`str = bstr.decode('utf-8')`

`type(str)`

`<class 'str'>`

The method **encode\(\)** returns an encoded version of the string.

`bstr2 = str.encode('utf-8')`

`type(bstr2)`

`<class 'bytes'>`

**References:** [https://docs.python.org/2/howto/unicode.html](https://docs.python.org/2/howto/unicode.html)

---

|[Next Topic](/08-advanced-functionality/in-memory-data-structures.md)|
|---|
