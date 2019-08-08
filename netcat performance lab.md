## Network Lab 1
In this lab, you will be running two machines (Linux and Windows) on Virtualbox. 
Both are connected via a network bridge, so they are part of the internal network.
Both machines have Netcat installed.

On the Windows machine, we created a simple text file that we want to send to the Linux machine
```
The appropriate syntax would be:
nc target_ip port < file.txt
So in this scenario we would be using:
>nc 192.168.0.114 1234 < zero-day.txt
```
![Untitled](https://user-images.githubusercontent.com/47218652/60911957-eaf8d880-a249-11e9-9d01-e43961cf8462.png)

### The syntax used was nc target_ip port < file.txt


![image](https://user-images.githubusercontent.com/47218652/60907394-0a3e3880-a23f-11e9-9849-55827c900736.png)


![Untitled](https://user-images.githubusercontent.com/47218652/60912573-45466900-a24b-11e9-8f5b-649359890ec7.png)



###    nc (run Netcat)
###    -lvp 1234 (Listen Verbosely on Port 1234)
###    > zeroday.txt (output > any data transferred to a file called zeroday.txt)


![Untitled](https://user-images.githubusercontent.com/47218652/60913370-d833d300-a24c-11e9-9566-0ade3e8d6d44.png)
