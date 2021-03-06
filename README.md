# Ansible-SeedDMS-RHEL7
WIP installation format for SeedDMS using ansible. Instructions in README.md

#Notes for people wanting to use this playbook
  - For proof of concept I disabled Selinux, however; this is undesirable in production and instead you will have to know the appropriate way to configure Selinux on your machines
  - This playbook assumes your database is on a different machine. If you have everything all on one machine, it's easy enough to adjust this script for a single server.
  - Make sure you have knowledge of your network as it will be necessary when making adjustment on the script.  
  - Anything in brackets in the README.md are values that depend on your setup.
  - You'll notice something funny in the haproxy.cfg.j2 file. This is an issue of me deciding on how best to tackle the balance of minimal user knowledge, and actual use. For now it's more a proof of concept. 

#Ansible basics for CentOS7
- Install and update ansible;

           yum -y install epel-release

           yum -y update

           yum -y install ansible

- Verify the installation and version

           ansible --version
           
  https://cloud.githubusercontent.com/assets/20823757/17412055/c6f4fb7c-5a48-11e6-82b9-e1a6f6635c44.PNG
  
- Generate key on your Ansible machine.
  *Accept defaults and leave passphrase empty for now.

           ssh-keygen -t rsa

  https://cloud.githubusercontent.com/assets/20823757/17412058/c95e7ffa-5a48-11e6-801a-bf2ccac1e753.PNG

- Next we need to send out the key to every webhost and database  on the network.

           ssh-copy-id root@[10.10.2.112]
  
  https://cloud.githubusercontent.com/assets/20823757/17412056/c8019ba6-5a48-11e6-826a-a432ac4928af.PNG
  
# Install and use git to download playbook
- Install git on your Ansible machine

           yum -y install git

- Download git repository into local directory

           git clone https://github.com/CelestialCruz/Ansible-SeedDMS-RHEL7.git

# Use playbook
- Head into the "Ansible-SeedDMS-RHEL7" directory

-  Edit the "hosts" files and put the IP address of your webserver under "[webservers]", database servers under "[dbservers]", Redis server under [redissvr]", and HAProxy server under "[haproxysvr]"

https://cloud.githubusercontent.com/assets/20823757/17723147/b80f3bce-6405-11e6-8455-fe3dc015ea1e.png

- Finally, run the playbook

           ansible-playbook -i hosts project.yml

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
