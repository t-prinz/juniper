# Example Ansible playbooks to manage Juniper devices

These playbooks use netconf to connect to the devices so, if needed, enable netconf over ssh[^1]:

```
[edit]
user@host# set system services netconf ssh
user@host# commit
```

Use the following to verify proper connectivity[^2][^3]:

```
ssh user@hostname -p 830 -s netconf
ssh user@hostname -t netconf
```

For reference, these playbooks were tested with a vSRX firewall deployed in AWS[^4].

### CLI commands to perform/verify various tasks

Set the hostname

`set system host-name aws-vsrx`

Set up interfaces

```
set interfaces ge-0/0/0 unit 0 family inet address 10.0.2.236/24
set interfaces ge-0/0/1 unit 0 family inet address 10.0.3.43/24
```

Set up security zones

```
set security zones security-zone untrusted-public-zone interfaces ge-0/0/0.0
set security zones security-zone trusted-private-zone interfaces ge-0/0/1.0
```

Save a rescue configuration

`request system configuration rescue save`

Delete the rescue configuration

`request system configuration rescue delete`

[^1]: https://www.juniper.net/documentation/us/en/software/junos/netconf/topics/topic-map/netconf-ssh-connection.html#d10e304
[^2]: https://www.juniper.net/documentation/us/en/software/junos/netconf/topics/task/netconf-session-connecting-to-server.html
[^3]: https://www.juniper.net/documentation/us/en/software/junos-ansible/ansible/topics/task/junos-ansible-connection-errors-troubleshooting.html
[^4]: https://www.juniper.net/documentation/us/en/software/vsrx/vsrx-consolidated-deployment-guide/vsrx-aws/topics/task/security-vsrx-aws-cli-configuring.html
