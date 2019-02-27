Ansible Role: Tomcat SSL Redirect
=========

This Role installs Nginx Web Server on a PC and redirect all requests from HTTP to HTTPS. The certificate is not valid, you should get a valid one and once you have it you should paste it in:

    ansible-tomcat8-ssl-redirect/files

The you need to make some changes on 

    ansible-tomcat8-ssl-redirect/files/server.xml

and change in the following line

    <Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol" ...>

the address of the certificate and the password, like in the next lines

    keystoreFile="conf/KeyStore.jks"
    keystorePass="123456789"

for the address and the password of your certificate.

Requirements
------------

It needs no extra roles. 

Role Variables
--------------

    tomcat_service: tomcat8
    tomcat_server_root: /var/lib/tomcat8
        
    __tomcat_packages:
    	- tomcat8
    	- tomcat8-admin

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      remote_user: root
      roles:
    	- ansible-tomcat8-ssl-redirect

License
-------

BSD

Author Information
------------------

This role was created in 2019 by Jibsan Joel Rosa Toirac.
