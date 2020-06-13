
# Hadoop - Installation

👉 System Requirements

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Windows 10 (64 bit) or any other OS that can run virtual machines

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Minimum 8GB RAM

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Internet connection

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ Virtualization should be enabled 👌

🚫 If these conditions are not met exactly then there might be issues in installation 🚫<br/>


## Steps:<br/>


1.  🌍 [Download](https://download.virtualbox.org/virtualbox/6.1.6/VirtualBox-6.1.6-137129-Win.exe) & install Oracle VirtualBox

2.  🌍 [Download](https://bitnami.com/redirect/to/995396/bitnami-hadoop-3.2.1-2-linux-debian-9-x86_64.ova) Bitnami Hadoop Stack

3.  🌍 [Download](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) & install Putty

4.  🌍 [Download](https://winscp.net/download/WinSCP-5.17.3-Setup.exe) & install WinSCP

5.  Importing the VM
	>1.  Launch VirtualBox
	>2.  Select “File➡️Import Appliance” menu option in VirtualBox and select the *.ova* file downloaded from the Bitnami website. Click “Continue” to proceed.
	>3.  Click “Import” to proceed ❗ *Ensure that the memory is set to at least 6GB* ❗
	>4.  Then go to Settings➡️Network adapter 1:NAT
	➡️Network adapter 2:host-only

6.  Start the VM
7.  Login to the VM using username and password as **bitnami**
❗password is not visible while typing don't be afraid it's there❗

8.  Enable SSH - enter the commands below
	```
	sudo rm -f /etc/ssh/sshd_not_to_be_run
	sudo apt install openssh-server
	sudo systemctl enable ssh
	sudo systemctl start ssh
	sudo ufw allow ssh
	sudo systemctl status ssh
	```
	
	❗ *After this status should be✅active* ❗
	
	![SSH Active](https://raw.githubusercontent.com/nipun24/hadoop-install-docs/master/images/image1.png)
	
	🌍 Refer [this](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/) site for further info
	
9.  Run the following command to check the IP address of the VM 
	```
	sudo ifconfig
	```
	❗ Note down the **inet** IP. It will be something like **192.168.x.x** ❗
	
	![IP address](https://raw.githubusercontent.com/nipun24/hadoop-install-docs/master/images/image2.png)
	
	❗ ❗ ❗ If mouse pointer is stuck inside VM press **right ctrl** ❗ ❗ ❗

10. Checking if everything is working or not
	>1. Open Chrome 
	>2. Type the IP noted above➡️Hit enter 
	>3. You’ll be prompted to type Username & Password 
	>4. Go to the VM and type `cat ./bitnami_credentials`  
	>5. Note ‘em and type them in the chrome tab [Yes, I know the password is irritating 😠] 
	>6. You’ll see a cute 🐘 which implies you’re good to proceed to the next step. 
	
11. Create a **.txt** file on your PC➡️name it accordingly➡️put a ton of 💩 inside it➡️save it.

12. Add the file to the VM
	>1. Open WinSCP 
	>2. Select protocol as **SFTP** 
	>3. Enter the inet IP address noted above in the Host Name 
	>4. Enter username and password as **bitnami** 
	>5. Click Login 
	>6. The left pane is the VM’s file directory and right one is your file directory 
	>7. In the VM’s directory navigate to **/home/bitnami** and paste the .txt you created in the above step  
	>8. Close WinSCP (you can even uninstall it if you want 😂, JK don't uninstall it) 
	
13. SSH to the VM 
	>1. Open PuTTY  
	>2. Enter the inet IP address noted above in the Host Name 
	>3. Connection type: **SSH** 
	>4. Click Open 

14. Finally 🏆 run these commands in Putty’s terminal
	```
	hadoop fs -rmr /tmp/hdfs-example-output  
	hadoop fs -put -f /home/bitnami/input_file.txt  /tmp/hdfs-example-input 
	hadoop jar  /opt/bitnami/hadoop/share/hadoop/mapreduce/hadoop-mapreduceexamples-*.jar grep /tmp/hdfs-example-input  /tmp/hdfs-example-output '[a-zA-Z0-9]+'  
	hadoop fs -cat /tmp/hdfs-example-output/part-r-00000
	```
	Replace `/input_file.txt` with the name of the text file you created

© 2020, Nipun Haldar & Kesava Karri, All rights reserved 💪   
