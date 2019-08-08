## WireShark
### What to hand in
```
The goal of this first lab was primarily to introduce you to Wireshark. The following questions will 
demonstrate that you’ve been able to get Wireshark up and running, and have explored some of its 
capabilities. Answer the following questions, based on your Wireshark experimentation:


1.List 3 different protocolsthat appear in the protocol column in the unfiltered packet-listing 
window in step 7 above.


2.How long did it take from when the HTTP GET message was sent until the HTTP OK reply was 
received? (By default, the value of the Time column in the packet-listing window is the 
amount of time, in seconds, since Wireshark tracing began.  To display the Time field in 
time-of-day format, select the Wireshark Viewpull down menu, then select Time Display Format,
then select Time-of-day.)


3.What is the Internet address of the gaia.cs.umass.edu (also known as www-net.cs.umass.edu)?
What is the Internet address of your computer?


4.Print the two HTTP messages (GET and OK) referred to in question 2 above. 
To do so, select Printfrom the Wireshark Filecommand menu, and select 
the“Selected Packet Only”and “Print as displayed”radial buttons, and then click OK.
```
1.Start up your favorite web browser, which will display your selected homepage.

2.Start up the Wireshark software.  You will initially see a window similar to that shown in the figure below.
Wireshark has not yet begun capturing packets.

![Untitled](https://user-images.githubusercontent.com/47218652/60916589-695a7800-a254-11e9-8517-edd0717905a1.png)

3.To begin packet capture, select the Capture pull down menu and select Interfaces.This will cause the “Wireshark: Capture Interfaces” window to be displayed, as shown in the figure below.

![Untitled](https://user-images.githubusercontent.com/47218652/60916676-a4f54200-a254-11e9-818c-0faba009c82b.png)

4.You’ll see a list of the interfaces on your computer as well as a count of the packets that have been observed on that interface so far.  Click on Startfor the interface on which youwant to begin packet capture (in the case, the Gigabit network Connection). Packet capture will now begin -Wireshark is now capturing all packets being sent/received from/by your computer!

5.Once you begin packet capture, a window similar to that shown in the figure below will appear.  This window shows the packets being captured.  By selectingCapturepulldown menu and selecting Stop, you can stop packet capture.  But don’t stop packet capture yet.Let’s capture some interesting packets first.  To do so, we’llneed to generate some network traffic.  Let’s do so using a web browser, which will use the HTTP protocol that we will study in detail in class to download content from a website.

![Untitled](https://user-images.githubusercontent.com/47218652/60916815-061d1580-a255-11e9-8430-bf48cd6adfa2.png)

6.While Wireshark is running, enter the URL: http://gaia.cs.umass.edu/wireshark-labs/INTRO-wireshark-file1.htmland have that page displayed in your browser. In order to display this page, your browser will contact the HTTP server at gaia.cs.umass.edu and exchange HTTP messages with the server in order to download this page.  The Ethernet frames containing these HTTP messages (as well as all other frames passing through your Ethernet adapter) will be capturedby Wireshark.

7.After your browser has displayed the INTRO-wireshark-file1.html page(it is a simple one line of congratulations), stop Wireshark packet capture by selecting stop in the Wireshark capture window.  The main Wireshark window should now look similar to Figure 3. You now have live packet data that contains all protocol messages exchanged between your computer and other network entities!  The HTTP message exchanges with the gaia.cs.umass.edu web server should appear somewhere in the listing of packets captured.  But there will be many other types of packets displayed as well (see, e.g., the many different protocol types shown in the Protocolcolumn in Figure 3).

8.Type in “http” (without the quotes, and in lower case –all protocol names are in lower case in Wireshark) into the display filter specification window at the top of the main Wireshark window.  Then select Apply(to the right of where you entered “http”).  This will cause only HTTP message to be displayed in the packet-listing window.  

9.Find the HTTP GET message that was sent from your computer to the gaia.cs.umass.edu HTTP server.(Look for an HTTP GET message in the “listing of captured packets” portion of the Wireshark window (see Figure 3) that shows “GET” followed by the gaia.cs.umass.edu URL that you entered.When you select the HTTP GET message, the Ethernet frame, IP datagram, TCP segment, and HTTP message header information will be displayed in the packet-header window2. By clicking on ‘+’ and ‘-‘ right-pointing and down-pointing arrowheadsto the left side of the packet details window, minimizethe amount of Frame, Ethernet, Internet Protocol, and Transmission Control Protocol information displayed. Maximizethe amount information displayed about the HTTP protocol.  Your Wireshark display should now look roughly as shown in the figure below.(Note, in particular, the minimized amount of protocol information for all protocols except HTTP, and the maximized amount of protocol information for HTTP in the packet-header window).

![Untitled](https://user-images.githubusercontent.com/47218652/60917154-e2a69a80-a255-11e9-9941-c0e660fcd0a5.png)

10.Exit Wireshark
