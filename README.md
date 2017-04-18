# check_emc_rlp
Nagios compatible plugin to check if there are free LUNs remaining in the RLP (Reserved LUN Pool). 

This allows you to avoid running out of free space for snapshot differential blocks, which will freeze your snapshot (and break your database).

Works for EMC disks array (like VNX 5300, 5200, etc)

# Prerequisites
 - Install Naviseccli for Linux on your Nagios server
 - As Nagios user, create a certicifate if you don't want to 
  specify EMC global admin password in the Naviseccli command 
  line (recommended...) :
     naviseccli -user sysadmin -password sysadmin -scope 0 \
     -AddUserSecurity