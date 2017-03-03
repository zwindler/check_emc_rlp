# check_emc_rlp
Nagios compatible plugin to check if there are RLP (Reserved LUN Pool) remaining. Works for EMC disks array (like VNX 5300, 5200, etc)

# Prerequisites
 - Install Naviseccli for Linux on your Nagios server
 - As Nagios user, create a certicifate if you don't want to 
  specify EMC global admin password in the Naviseccli command 
  line (recommended...) :
     naviseccli -user sysadmin -password sysadmin -scope 0 \
     -AddUserSecurity