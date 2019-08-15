|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## Data Reassembly

### End of Data

* How to tell if there is no more data?
* recv() will return empty string
```
>>> s.recv(1000)
''
>>>
```
* This means that the other end of the connection has been closed (no more sends)

### Data Reassembly

* Receivers often need to reassemble messages from a series of small chunks
* Here is a programming template for that
```python
fragments = []               # List of chunks
while not done:
    chunk = s.recv(maxsize)  # Get a chunk
    if not chunk:
        break                # EOF. No more data
    fragments.append(chunk)
    
# Reassemble the message
message = "".join(fragments)
```
* Don't use string concat(+=). It's slow.

## If there is no more data being transmitted the _**while**_ loop will _**break_.**

---

![](/assets/chunk1.PNG)

![](/assets/chunk.PNG)

## If there is not any more data being transmitted the _**while**_ loop will **_break_.**

---

|[Next Topic](/03-intro-to-sockets/review.md)|
|---|
