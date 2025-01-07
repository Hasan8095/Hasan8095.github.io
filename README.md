#!/bin/bash

# Update packages and install prerequisites
sudo apt-get update
sudo apt-get install -y wget gnupg2

# Add Kali Linux repository
echo "deb http://http.kali.org/kali kali-rolling main non-free contrib" | sudo tee /etc/apt/sources.list.d/kali.list

# Add Kali Linux public key
wget -q -O - https://archive.kali.org/archive-key.asc | sudo apt-key add -

# Update package list with Kali repository
sudo apt-get update

# Install Kali Linux base system
sudo apt-get install -y kali-linux-core

# Install KDE Plasma desktop environment
sudo apt-get install -y kali-desktop-kde

# Set KDE as the default desktop environment
sudo update-alternatives --set x-session-manager /usr/bin/startplasma-x11

# Clean up
sudo apt-get clean

# Extended Tools
sudo apt-get update
sudo apt-get install -y wget gnupg2

# Add Kali Linux repository
echo "deb http://http.kali.org/kali kali-rolling main non-free contrib" | sudo tee /etc/apt/sources.list.d/kali.list

# Add Kali Linux public key
wget -q -O - https://archive.kali.org/archive-key.asc | sudo apt-key add -

# Update package list with Kali repository
sudo apt-get update

# Install Kali Linux base system
sudo apt-get install -y kali-linux-core

# Install KDE Plasma desktop environment
sudo apt-get install -y kali-desktop-kde

# Set KDE as the default desktop environment
sudo update-alternatives --set x-session-manager /usr/bin/startplasma-x11

# Clean up
sudo apt-get clean

# Install Tools CustomScript

apt-get upgrade -y && apt-get dist-upgrade -y
apt-get install -y firefox-esr-l10n-ja flashplugin-nonfree
systemctl start postgresql
systemctl enable postgresql

#Enable Metasploit log
apt-get install -y metasploit-framework
msfdb init

#The Backdoor Factory
echo "spool /root/msf_console.log" > /root/.msf4/msfconsole.rc
git clone https://github.com/secretsquirrel/the-backdoor-factory /opt/the-backdoorfactory
cd /opt/the-backdoorfactory/
./install.sh 
cd

#HTTPScreenShot
curl -kL https://bootstrap.pypa.io/get-pip.py | python
pip install selenium
git clone https://github.com/breenmachine/httpscreenshot /opt/httpscreenshot
cd /opt/httpscreenshot
chmod +x install-dependencies.sh && ./install-dependencies.sh 
cd

#SMBexec
git clone https://github.com/pentestgeek/smbexec /opt/smbexec
cd /opt/smbexec && ./install.sh
cd

#Masscan
apt-get install -y libpcap
git clone https://github.com/robertdavidgraham/masscan /opt/masscan
cd /opt/masscan/
make
make install
cd
history 

#Gitrob
git clone https://github.com/michenriksen/gitrob /opt/gitrob
gem install bundler


# Install Boxes as GUI
sudo apt install qemu uml-utilities virt-manager gnome-boxes
sudo update
sudo reboot
