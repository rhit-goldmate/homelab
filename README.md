# Cybersecurity Home Lab
This project goes over the different tools used to create a homelab. You can view the network topology for the project in the homelab-network.pdf file. I will be using these repository to store files for all of my projects that I'm completing using my homelab. Below, I will give an overview of the homelab and links to resources so you can create a similar homelab yourself.
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
The links below will direct you to the website I referenced when setting up my network environment:
- [Part 1: Project Overview & Installing VirtualBox](https://blog.davidvarghese.dev/posts/building-home-lab-part-1/)
- [Part 2: pfSense Setup & Configuration](https://blog.davidvarghese.dev/posts/building-home-lab-part-2/)

## Management VMs
