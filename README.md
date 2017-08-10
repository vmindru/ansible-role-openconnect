openconnect
=========

Configure CLI openconnect client with open-vpn

Requirements
------------

this has been tested on Fedora only

Role Variables
--------------

    openconnect_script_template: "vpn-client.sh.j2"
    openconnect_script_name: "vpn_connect"
    openconnect_script_dest: "/usr/bin/{{ openconnect_script_name }}"
    openconnect_vpn_group: "none"
    openconnect_vpn_user: "none"
    openconnect_vpn_url: "none"
    openconnect_vpnc_script: "/etc/vpnc/vpnc-script" #this is default value for RHEL boxes, might need adjustments on playbook level for debian

Example Playbook
----------------

you can use the playbook provided with the role 

    [vmindru@zetor openconnect]$ ansible-playbook -i localhost, demo_playbook.yml  -c local -b -K                                                                                                                      
    SUDO password:                                                                                                                                                                                                     
    provide VPN group: RocketFuel                                                                                                                                                                                      
    provide VPN user: vmindru                                                                                                                                                                                          
    provide anyconnect vpn URL: https://some_fqdn           
    [vmindru@zetor openconnect]$

or create your own similar playbook

		- hosts: localhost
	  connection: local
	  vars_prompt:
	    - name: openconnect_vpn_group
	      prompt: "provide VPN group"
	      private: no
	
	    - name: openconnect_vpn_user
	      prompt: "provide VPN user"
	      private: no
	
	    - name: openconnect_vpn_url
	      prompt: "provide anyconnect vpn URL"
	      private: no
	  roles:
	  - { role: openconnect }



License
-------

GPLv2

Author Information
------------------
Veaceslav Mindru m1ndruvXgma1l.c0m
