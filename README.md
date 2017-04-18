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
     
# Examples

```
$ ./check_emc_rlp.pl 10.1.1.1 1 95
OK: there are enough free LUNs in RLP| lun17=67.3%;95;95;0;100 lun19=67.1%;95;95;0;100 lun16=68.1%;95;95;0;100 lun0=68.2%;95;95;0;100 free_rlp_per_lun=4;1;;0;

$ ./check_emc_rlp.pl 10.1.1.1 5 50
WARNING: there are less than 4 free LUNS in RLP (for each LUN using RLP)! You asked me to warn you if the is less than 5 free LUN in RLP per LUN using RLP| lun17=67.3%;50;50;0;100 lun19=67.1%;50;50;0;100 lun16=68.1%;50;50;0;100 lun0=68.2%;50;50;0;100 free_rlp_per_lun=4;5;;0;
```
