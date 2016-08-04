# Ansible-SeedDMS-RHEL7
WIP installation format for SeedDMS using ansible

#Notes for people wanting to use this playbook
  - For proof of concept I disabled Selinux, however; this is undesirable in production and instead you will have to know the appropriate way to configure Selinux on your machines
  - This playbook assumes your database is on a different machine. If you have everything all on one machine, it's easy enough to adjust this script for a single server.
  - Make sure you have knowledge of your network as it will be necessary when making adjustment on the script.  
  - Anything in brackets in the README.md are values that depend on your setup.

#Ansible basics for CentOS7
- Install and update ansible;

           yum -y install epel-release

           yum -y update

           yum -y install ansible

- Verify the installation and version
           ansible --version
- Generate key on your Ansible machine.
  *Accept defaults and leave passphrase empty for now.
      ssh-keygen -t rsa
- Next we need to send out the key to the desired machines on the network.
      ssh-copy-id root@[10.10.2.112]
#After running the playbook
 - Point your webbrowser to your webserver with SeedDMS installed:
       "http://hostname/seeddms"

- In the "Welcome to the Installation of SeedDMS"  click on "Start installation"
https://cloud.githubusercontent.com/assets/20823757/17388417/06bcd5d8-59ca-11e6-92ce-8592d2cd9373.PNG

- In the next page, check to make sure all the information is correct. The defaults should be fine except for the "server name" bar. Put the IP address of your database instead of the default. 
https://cloud.githubusercontent.com/assets/20823757/17388432/269eb0e2-59ca-11e6-9bb1-b8a6cbea7f6a.PNG

- Check the "Create database tables" box and then click "Apply"

- In the following page, click on "Delete file ENABLE_INSTALL_TOOL if possible"
https://cloud.githubusercontent.com/assets/20823757/17388433/26aace2c-59ca-11e6-9212-8fb5cd9d77e4.PNG

- This will take you to the login page. To log in, use "admin" for both User ID and Password and click "Sign In"
https://cloud.githubusercontent.com/assets/20823757/17388434/26ab6a30-59ca-11e6-9b02-2bf34ddb3106.PNG

- Once you see the following page then congratulations! You're done. 
https://cloud.githubusercontent.com/assets/20823757/17388435/26b0587e-59ca-11e6-8af2-d7ac0c38ff45.PNG
