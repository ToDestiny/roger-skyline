# roger-skyline
42 - Initiation project for System and Network Administrator
<br>
<br>
Correction :<br>
<br>
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
7 - Modify your /etc/ssh/sshd_config to include at least the following :<br>
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
7 - Go to your Mac terminal and type : ssh-keygen<br>
