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

# Reboot the system to apply changes
sudo reboot
