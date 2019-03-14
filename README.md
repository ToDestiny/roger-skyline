# roger-skyline
42 - Initiation project for System and Network Administrator


Correction :

1 - Launch create-vm.sh (Automation Script) <br>
2 - Accept network settings and setup VM (on VirtualBox)<br>
3 - After installing(with only SSH and Basic setup), launch VM <br>
4 - Edit with nano this file : nano etc/apt/sources.list . Comment the cdrom part.<br>
5 - Command : apt-get update && apt-get install vim <br>
6 - Command : vim /etc/network/interfaces to change the primary network from dhcp to static.<br>
Then add those lines :<br>
    address : 10.13(third floor).X.X but try to choose a random port as someone else could use the same!<br>
    netmask : 255.255.255.252 (subject ask for static netmask of 30)<br>
    gateway : 10.13.254.254<br>
Save and reboot your VM<br>
7 - Go to your Mac terminal and type : ssh-keygen<br>
