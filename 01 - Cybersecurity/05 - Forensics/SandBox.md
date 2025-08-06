In [[Malware Analysis]], a sandbox is an isolated environment mimicking the actual target environment of a malware, where an analyst runs a sample to learn more about it. Malware analysis sandboxes heavily rely on Virtual Machines, their ability to take snapshots and revert to a clean state when required.
## Construction of a sandbox

For malware analysis using sandboxes, the following considerations make the malware analysis effective:

- Virtual Machine mimicking the actual target environment of the malware sample
- Ability to take snapshots and revert to clean state
- OS monitoring software, for example, Procmon, ProcExplorer or Regshot, etc.
- Network monitoring software, for example, Wireshark, tcpdump, etc.
- Control over the network through a dummy DNS server and webserver.
- A mechanism to move analysis logs and malware samples in and out of the Virtual Machine without compromising the host (Be careful with this one. If you have a shared directory with your malware analysis VM that remains accessible when running malware, you might risk malware affecting all files in your shared directory)

### Cuckoo's Sandbox

[Cuckoo's sandbox](https://github.com/cuckoosandbox/cuckoo) is the most widely known sandbox in the malware analysis community. It was developed as part of a Google Summer of Code project in 2010. It is an open-source project that you will often see deployed in SOC environments and with enthusiasts' home labs. Advantages of Cuckoo's sandbox include huge community support, easy-to-understand documentation, and lots of customizations. You can deploy it on your network and let the community signatures guide you into identifying which files are malicious and which are benign because of the vast corpus of community signatures that come with it.

Cuckoo's sandbox has been archived, and an update is pending. It also doesn't support Python 3, making it obsolete right now. However, all is not lost because we have alternatives.

### CAPE Sandbox

[CAPE Sandbox](https://github.com/kevoreilly/CAPEv2) is a little more advanced version of Cuckoo's sandbox. It supports debugging and memory dumping to support the unpacking of packed malware (We will learn more about packing and unpacking in the advanced malware analysis module). Though beginners can use this sandbox, advanced knowledge is required for making full use of it. A community version of this sandbox is available online, which can be used to test run it before installing. CAPE Sandbox is so far actively developed and supports Python 3.

## Online Sandboxes:

Setting up and maintaining a sandbox can be a time-consuming task. Keeping that in view, online sandboxes can be of great help. Some of the most commonly used online sandboxes are as follows:

- [Online Cuckoo Sandbox](https://cuckoo.cert.ee/)
- [Any.run](https://any.run/)
- [Intezer](https://analyze.intezer.com/)
- [Hybrid Analysis](https://hybrid-analysis.com/)

## Sandbox evasion:

As we have seen previously, we can always run a sample in a sandbox to analyze it. In many cases, that might help us analyze samples that evade our basic static analysis techniques. However, malware authors have some tricks up their sleeves that hamper that effort. Some of these techniques are as follows:

- **Long sleep calls:** Malware authors know that sandboxes run for a limited time. Therefore, they program the malware not to perform any activity for a long time after execution. This is often accomplished through long sleep calls. The purpose of this technique is to time out the sandbox.
- **User activity detection:** Some malware samples will wait for user activity before performing malicious activity. The premise of this technique is that there will be no user in a sandbox. Therefore there will be no mouse movement or typing on the keyboard. Advanced malware also detects patterns in mouse movements that are often used in automated sandboxes. This technique is designed to bypass automated sandbox detection.
- **Footprinting user activity:** Some malware checks for user files or activity, like if there are any files in the MS Office history or internet browsing history. If no or little activity is found, the malware will consider the machine as a sandbox and quit. 
- **Detecting VMs:** Sandboxes run on virtual machines. Virtual machines leave artifacts that can be identified by malware. For example, some drivers installed in VMs being run on VMWare or Virtualbox give away the fact that the machine is a VM. Malware authors often associate VMs with sandboxes and would terminate the malware if a VM is detected.