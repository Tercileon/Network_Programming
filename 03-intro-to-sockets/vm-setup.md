# **VMWare Setup with Fedora 64**

![](/assets/vmware.PNG)At the home screen in VMWare Workstation 12 Begin by clicking the first box: "**Create a New Virtual Machine**"

![](/assets/vmware1.PNG)

Select **Typical **and click **Next**.

![](/assets/vmware2.PNG)

Select **Installer disc image file \(iso\), **click **Browse **and navigate to your Fedora Workstation .iso file.

Then click **Next**.

![](/assets/vmware3.PNG)

Name the Virtual Machine and click **Next**.

![](/assets/vmware4.PNG)

Set **Maximum disk size \(GB\)** to at least **20GB **and click** Next.**

![](/assets/vmware5.PNG)

Click **Customize Hardware...**

![](/assets/vmware6.PNG)

Set **Memory **to at least **4 GB ** and **Processors **to at least **2**.

Then click **Add...**

![](/assets/vmware7.PNG)

Select **Network Adapter **and click** Next.**

![](/assets/vmware8.PNG)

Select **Custom: Specific virtual network **and **VMnet4** from the drop-down menu.

Then click **Finish**.

![](/assets/vmware9.PNG)

At the **Hardware **menu click **Advanced...**

Then click **Generate **to generate a **MAC Address** for the Virtual Machine.

Then click **OK**, **Close** the **Hardware **menu and continue the installation normally.

After installation, create a **Snapshot**, and create **Clones**, as needed.

Remember to generate a new **MAC Address** for each additional VM.

