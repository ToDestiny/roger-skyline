# roger-skyline
42 - Initiation project for System and Network Administrator
<br>
<br>
Correction :<br>
<br>
<b>*INSTALL VM ON VIRTUALBOX*</b><br>
1 - Launch create-vm.sh (Automation Script) <br>
<br>
2 - Accept network settings and setup VM (on VirtualBox)<br>
<br>
3 - After installing(with only SSH and Basic setup), launch VM <br>
<br>
4 - Edit with nano this file : nano etc/apt/sources.list . Comment the cdrom part.<br>
<br>
5 - Command : apt-get update && apt-get install vim <br>
<br>
6 - Command : vim /etc/network/interfaces to change the primary network from dhcp to static.<br>
<br>
Then add those lines :<br>
<br>
    address : 10.13(third floor).X.X but try to choose a random port as someone else could use the same!<br>
    netmask : 255.255.255.252 (subject ask for static netmask of 30)<br>
    gateway : 10.13.254.254<br>
    <br>
Save and reboot your VM<br>
<br>
7 - <b>*INSTALL SSH*</b><br>
On your VM, do the following :<br>
    - mkdir ~/.ssh<br>
    - cd .ssh<br>
    - touch authorized_keys<br>
    - chmod 0600 authorized_keys<br>
Go to your Mac terminal and type : ssh-keygen<br>
Try to connect first time to your VM through terminal : <br>
    - ssh toto@10.13.1.63 -p 2222<br>
Once connected exit.<br>
Copy your ssh key to debian server using :<br>
    - ssh-copy-id -i ~/.ssh/id_rsa.pub toto@10.12.1.63 -p 2222<br>
<br>
8 - <b>* AUTHORIZE PUBLICKEY ACCESS & PREVENT SOME DDOS ATTACKS *</b><br>
Modify your /etc/ssh/sshd_config to include at least the following :<br>
<br>
Port 2222<br>
PermitRootLogin no<br>
PubkeyAuthentication yes<br>
AuthorizedKeysFile      .ssh/authorized_keys<br>
PasswordAuthentication no<br>
PermitEmptyPasswords no<br>
ChallengeResponseAuthentication no<br>
UsePAM yes<br>
X11Forwarding yes<br>
PrintMotd no<br>
AcceptEnv LANG LC_*<br>
Subsystem       sftp    /usr/lib/openssh/sftp-server<br>
MaxAuthTries 1<br>
<br>
Save and reboot your VM<br>
Connect from Mac terminal and accept.<br>
<br>
9 - *DDOS ATTACKS AND DEFENDING OPEN PORTS*<br>
    - Implement the rules on /etc/iptables (or whatever the name of your script for iptables)<br>
<br>
10 - *Disable non-needed services*<br>
    - Tocheck enabled services : systemctl list-unit-files | grep enabled<br>
    - Disable the one not needed : - Apache2 (if installed) / apt-daily.timer and apt-daily-upgrade.timer<br>
    

