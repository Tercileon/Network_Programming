|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

# Filters

## **Click the expression button to the right of the Filter bar OR type it in yourself:**

* eth.addr==aa:bb:cc:dd:ee:ff
* ip.addr== 127.0.0.1
* ip.src== 127.0.0.2
* ipv6.dst == ::1
* tcp.port== 1337
* tcp.sport== 80
* udp.dport== 53

## **You can also filter on protocol:**

* arp
* icmpv6

![](/assets/wireshark-display-filters-59512e443df78cae8136b049.png)

One of the most important feature sets in Wireshark is its filter capabilities, especially when you're dealing with files that are significant in size. Capture filters can be set before the fact, instructing Wireshark to only record those packets that meet your specified criteria.

Filters can also be applied to a capture file that has already been created so that only certain packets are shown. These are referred to as display filters.

Wireshark provides a large number of predefined filters by default, letting you narrow down the number of visible packets with just a few keystrokes or mouse clicks. To use one of these existing filters, place its name in the _Apply a display filter_ entry field \(located directly below the Wireshark toolbar\) or in the _Enter a capture filter_ entry field \(located in the center of the welcome screen\).

There are multiple ways to achieve this. If you already know the name of your filter, simply type it into the appropriate field. For example, if you only wanted to display TCP packets you would type _tcp_. Wireshark's autocomplete feature will show suggested names as you begin typing, making it easier to find the correct moniker for the filter you're seeking.

Another way to choose a filter is to click on the bookmark-like icon positioned on the left-hand side of the entry field. This will present a menu containing some of the most commonly-used filters as well as an option to _Manage Capture Filters_ or _Manage Display Filters_. If you choose to manage either type an interface will appear allowing you to add, remove or edit filters.

You can also access previously-used filters by selecting the down arrow, located on the right-hand side of the entry field, which displays a history drop-down list.

Once set, capture filters will be applied as soon as you begin recording network traffic. To apply a display filter, however, you'll need to click on the right arrow button found on the far-right hand side of the entry field.

---

|[Next Topic](/02-intro-to-networking/wireshark/coloring-rules.md)|
|---|
