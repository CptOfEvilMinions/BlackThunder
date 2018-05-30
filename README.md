# BlackThunder
Threat hunting repo for my independent study on network threat hunting with Bro.

## Graylog
0. vim hosts and set "[graylog-server]":
    1. [hostname] ansible_host=[ip addr] ansible_python_interpreter=/usr/bin/python3
0. mv group_vars/all.example group_vars/all
0. vim group_vars/all and set:
    1. base_domain - The domain used in your env
    1. timezone - Set timezone by default is set to EST
    1. Set cert generation data
    1. slack_channel and slack_token - optional
0. mv group_vars/graylog-server.example group_vars/graylog-server
0. vim group_vars/graylog-server and set:
    1. graylog_url - Set to download location of latest Graylog deb package
        2. Set to Graylog 2.4 by default
        2. Tested with Graylog 2.4.3
    1. graylog_admin_password - password for Graylog admin login
0. ansible-playbook -i hosts deploy_graylog.yml -u [username]

## Bro
THE INSTANCE MUST HAVE TWO INTERFACES!!!!

0. mv group_vars/bro-node.example group_vars/bro-node
0. vim group_vars/bro-node and set:
    1. bro_management_interface - interface used to access the machine via SSH
    1. bro_promiscuous_interface - interface used to monitor network traffic
    1. bro_local_network - Local network in CIDR notation that Bro will monitor
    1. bro_mail_to - Place to send e-mail alerts from BRO
0. ansible-playbook -i hosts deploy_bro.yml -u [username]


## Supported operating systems
* Ubuntu Server 16.04 64-bit

## Resources/Sources
* Github repo: https://github.com/CptOfEvilMinions/ThreatWaffle
* Bro install docs: https://www.bro.org/sphinx/install/install.html#configure-the-run-time-environment
* Graylog install docs: http://docs.graylog.org/en/2.4/pages/installation.html