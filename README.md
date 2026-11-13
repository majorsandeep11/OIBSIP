# OIBSIP
#!/bin/bash
# UFW firewall configuration script
# Author: Shlok Pandey
# Run with: sudo bash ufw_configuration.sh

# Install and enable UFW
apt install ufw -y
ufw --force enable

# Allow SSH (port 22)
ufw allow ssh

# Deny HTTP (port 80)
ufw deny http

# Deny HTTPS (port 443)
ufw deny https

# Block one specific IP address
ufw deny from 100.122.127.107

# Show all active rules
ufw status verbose