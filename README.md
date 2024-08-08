# Cybersecurity Home Lab
This project goes over the different tools used to create a homelab. You can view the network topology for the project in the homelab-network.pdf file. I will be using these repository to store files for all of my projects that I'm completing using my homelab. This lab is capable of red teaming and blue teaming. For example, we can use Kali Linux to attack our Windows server, and then detect that attack using the Splunk instance. There is a lot more that can be done in this lab, and you can learn more by reading below and looking through many of the projects I will be working on. Below, I will give an overview of the homelab and links to resources so you can create a similar homelab yourself. If you plan on following a step-by-step guide, I recommend following all of the tutorials posted in order, though I may not link them all in order. I followed the tutorial pretty closely while setting up my lab, found on [David Varghese's Blog: Source Code](https://blog.davidvarghese.dev/).
***
![Homelab Network Topology](homelab-network.png)
***
## Set Up
Prior to diving into making your own network topology or downloading various tools, make sure you have a virtual machine software such as VirtualBox or VMware that can store the various VMs you will be creating. You will also need to decide what to use as your preffered firewall for the lab environment (OPNsense and pfSense are common, pfSense is what I used and is what the step-by-step instructions guide you through). 
### Hardware Requirements:
1. 64-bit multi-threaded CPU (minimum 4 cores) with Virtualization Support
2. 16GB RAM
3. ~250GB Disk Space
> NOTE: Disk space will fill up quickly as you download .iso images for various VMs, however once you set up a VM the corresponding .iso file can usually be deleted

### Step-by-step:
- [Part 1: Project Overview & Installing VirtualBox](https://blog.davidvarghese.dev/posts/building-home-lab-part-1/)
- [Part 2: pfSense Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-2/)
***
## LAN: Management VMs
This part of the network consists of the Kali Linux VM. It is used for managing the homelab, as it is on the LAN network. While setting up the homelab, I used my Kali VM to access the web UI of my pfSense firewall and router, and I was able to manage it from there including assigning firwall rules to block other VMs from accessing certain subnets / the Internet.
> NOTE: You can download the Kali Linux VM image [here](https://www.kali.org/get-kali/#kali-installer-images), it is ~4GB in size

### Step-by-step: 
- [Part 3: Kali Linux Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-3/)
> NOTE: If you are following step-by-step instruction, [Part 4: pfSense Configuration](https://blog.davidvarghese.dev/posts/building-home-lab-part-4/) needs to be completed before moving to the next section
***
## Cyber Range
This section of the network consists of 2 vulnerable VMs. Metasploitable 2 (VM that is intentionally vulnerable to common exploits) and Chronos 1 (a beginner-friendly challenge VM from vulnhub). Using Kali Linux you will be able to access the machines in the Cyber Range part of the network. You can also add more vulnerable VMs as you wish, as this is meant to be used for your very own CTF challenge space. Many resources can be found at [vulnhub.com](https://vulnhub.com/).
> NOTE: Download [Metasploitable 2]() and [Chronos 1]() here
### Step-by-step:
- [Part 5: Cyber Range Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-5/)
***
## Active Directory
The Active Directory lab contains 3 VMs. The first one is the [Windows 2019 Server](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019) which will act as the Domain Controller for the environment, and the other two are instances of [Windows 10 Enterprise](https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise) which will be the clients that use the environment. You can also setup this environment with a single client VM, however some attacks require more than one client. There are also multiple AD attacks you can find online (and at the end of the Part 7 tutorial).
> NOTE: If you wish to set up Splunk in the Security lab, then you'll need to set up the Windows Server, as this will be where we forward data to Splunk

### Step-by-step:
- [Part 6: Active Directory Lab Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-6/)
- [Part 7: Active Directory Lab Setup (cont.)](https://blog.davidvarghese.dev/posts/building-home-lab-part-7/)
***
## Malware Analysis
The Malware Analysis lab contains 2 VMs. The first one is FlareVM and the second is REMnux. Both of these VMs are preloaded with malware analysis tools for things like reverse engineering. Flare VM has a collection of scripts used to automate the installation of many malware analysis tools for Windows machines. Whereas REMnux, is a malware analysis toolkit for Linux machines. With both of these VMs you will be able to explore many types of malware on different machine types. 

### Step-by-step:
- [Part 8: Malware Analysis Lab Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-7/)
***
## Security VMs
There are two Security VMs in this homelab. Tsurugi Linux is the first, and is a large digital forensics VM (DFIR). Splunk is the other security tool, running on an Ubuntu VM. This instance of Splunk Enterprise runs on this VM, and you can install a Splunk Universal Forwarder on your Windows 2019 Server from the Active Directory Lab. By doing this, the Splunk instance is able to collect local event logs from the Windows machine.
> NOTE: You need an account to download Splunk Enterprise, and it is a free trial for 60 days. You need to take a snapshot of the "fresh install" of the VM in order to restore the VM back to this stage after the trial expires, and you will be good for another 60 days.

### Step-by-step:
- [Part 9: Tsurugi Linux Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-9/)
- [Part 10: Splunk Setup](https://blog.davidvarghese.dev/posts/building-home-lab-part-10/)
> NOTE: There is a Part 11 on the Blog for a step-by-step process on how to get malware files for analysis into the malware analysis lab. Since it is isolated from the network, you can do this through SSH from the Tsurugi Linux machine
***
