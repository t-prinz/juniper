# juniper
Playbooks to manage Juniper devices

Enable netconf over ssh (if needed)
Reference: https://www.juniper.net/documentation/us/en/software/junos-ansible/ansible/topics/task/junos-ansible-connection-errors-troubleshooting.html

[edit]
user@host# set system services netconf ssh
user@host# commit

Testing connectivity
Reference: https://www.juniper.net/documentation/us/en/software/junos/netconf/topics/task/netconf-session-connecting-to-server.html

ssh user@hostname -p 830 -s netconf

ssh user@hostname -t netconf

vSRX initial set up
Reference: https://www.juniper.net/documentation/us/en/software/vsrx/vsrx-consolidated-deployment-guide/vsrx-aws/topics/task/security-vsrx-aws-cli-configuring.html

set system host-name aws-vsrx

Set up interfaces

set interfaces ge-0/0/0 unit 0 family inet address 10.0.2.236/24 
