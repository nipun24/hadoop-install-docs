
# Hadoop - Installation

👉 System Requirements

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Windows 10 (64 bit)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Minimum 8GB RAM

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Internet connection

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Virtualization should be enabled 👌

🚫 If these conditions are not met exactly then there might be issues in installation 🚫<br/>


## Steps:<br/>


1.  Download & install Oracle VirtualBox

	🌍[[https://download.virtualbox.org/virtualbox/6.1.6/VirtualBox-6.1.6-137129-Win.exe](https://www.google.com/url?q=https://download.virtualbox.org/virtualbox/6.1.6/VirtualBox-6.1.6-137129-Win.exe&sa=D&ust=1587059116143000)]

2.  Download Bitnami Hadoop Stack

	🌍[[https://bitnami.com/redirect/to/995396/bitnami-hadoop-3.2.1-2-linux-debian-9-x86_64.ova](https://www.google.com/url?q=https://bitnami.com/redirect/to/995396/bitnami-hadoop-3.2.1-2-linux-debian-9-x86_64.ova&sa=D&ust=1587059116144000)]

3.  Download & install Putty

	🌍[[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.google.com/url?q=https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html&sa=D&ust=1587059116145000)]

4.  Download & install WinSCP

	🌍[[https://winscp.net/download/WinSCP-5.17.3-Setup.exe](https://www.google.com/url?q=https://winscp.net/download/WinSCP-5.17.3-Setup.exe&sa=D&ust=1587059116145000)]

5.  Importing the VM
    >1.  Launch VirtualBox
    >2.  Select “File➡️Import Appliance” menu option in VirtualBox and select the *.ova* file downloaded from the Bitnami website. Click “Continue” to proceed.
    >3.  Click “Import” to proceed
    ❗ Ensure that the memory is set to at least 6GB ❗
    >4.  Then go to Settings➡️Network adapter 1:NAT
    ➡️Network adapter 2:host-only

6.  Start the VM
7.  Login to the VM using username and password as **bitnami**
❗password is not visible while typing don't be afraid it's there❗

8.  Enable SSH - enter the commands below
	```shell
	sudo rm -f /etc/ssh/sshd_not_to_be_run
	sudo apt install openssh-server
	sudo systemctl enable ssh
	sudo systemctl start ssh
	sudo systemctl status ssh
	```
	![Image of Yaktocat]([https://raw.githubusercontent.com/nipun24/hadoop-install-docs/master/images/image1.png](https://raw.githubusercontent.com/nipun24/hadoop-install-docs/master/images/image1.png))
