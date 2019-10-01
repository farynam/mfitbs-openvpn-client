Role Name
=========

Tasks to generate openvpn client.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

* mfitbs-openvpn-easyrsa
* mfitbs-openvpn-generic


Role Variables
--------------

###### EasyRSA host
* easy_rsa_host - host on which easyrsa will be installed.
* EASY_RSA_BIN - easyrsa script path.
* ca_cn - easyrsa CA cert base file name.
* PKI_DIR - easyrsa cert repo path

###### all
* id_type - ID type (certficate field subject-alt-name) in cert can be DNS or IP
* proto - proto for openvpm connections values:tcp,udp 
* host_pki_dir - host PKI dir (where keys, certs, ... being kept).
* dh - openvpn Diffie–Hellman file name base
* dh_len - Diffie–Hellman param length. 
* cipher - openvpn cipher.
* log_status - openvpn status log.
* log - openvpn log. 

Dependencies
------------

* mfitbs-openvpn-easyrsa
* mfitbs-openvpn-generic

Example Playbook
----------------

- name: Install client
  hosts: server, target3, target4 #server because of variables
  serial: 1 #easy rsa gets randomly messed without this
  roles:
  - role: openvpn-client
    when: inventory_hostname != server_host

License
-------

MIT

Author Information
------------------

Marcin Faryna
