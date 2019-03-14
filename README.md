# roger-skyline
42 - Initiation project for System and Network Administrator


Correction :

1 - Launch create-vm.sh (Automation Script)
2 - Accept network settings and setup VM (on VirtualBox)
3 - After installing(with only SSH and Basic setup), launch VM
4 - Edit with nano this file : nano etc/apt/sources.list . Comment the cdrom part.
5 - Command : apt-get update && apt-get install vim
6 - Command : vim /etc/network/interfaces to change the primary network from dhcp to static.
Then add those lines :
    address : 10.13(third floor).X.X but try to choose a random port as someone else could use the same!
    netmask : 255.255.255.252 (subject ask for static netmask of 30)
    gateway : 10.13.254.254
Save and reboot your VM
7 - Go to your Mac terminal and type : ssh-keygen
