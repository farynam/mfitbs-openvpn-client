Role Name
=========

mfitbs_openvpn_client

Requirements
------------

N/A

Role Variables
--------------

###### EasyRSA host
* easy_rsa_host - host on which easyrsa will be installed.

###### all
* id_type - ID type (certficate field subject-alt-name) in cert can be DNS or IP
* proto - proto for openvpm connections values:tcp,udp 
* host_pki_dir - host PKI dir (where keys, certs, ... being kept). 
* cipher - openvpn cipher.
* log_status - openvpn status log.
* log - openvpn log. 

Dependencies
------------

* farynam.mfitbs-openvpn-easyrsa

Example Playbook
----------------

* inventory


    erh ansible_host=192.168.51.5 ansible_user=root ansible_password=qwerty ansible_ssh_common_args='-o StrictHostKeyChecking=no'

    [server]
    
    server ansible_host=192.168.51.4 ansible_user=root ansible_password=qwerty ansible_ssh_common_args='-o StrictHostKeyChecking=no'

    [client]
    
    client1 ansible_host=192.168.51.6 client_addr=10.8.0.2 client_mask=255.255.255.0 ansible_user=root ansible_password=qwerty ansible_ssh_common_args='-o StrictHostKeyChecking=no'


* playbook


    - name: Test Client
      hosts: client
      roles:
        - role: farynam.mfitbs_openvpn_client
          vars:
            server_port: 1194
            proto: tcp
            cipher: AES-256-CBC
            id_type: IP
            easy_rsa_host: erh
            host_pki_dir: /etc/pki/openvpn
      tasks:



License
-------

MIT

Author Information
------------------

Marcin Faryna
