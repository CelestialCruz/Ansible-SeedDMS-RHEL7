# Ansible-SeedDMS-RHEL7
WIP installation format for SeedDMS using ansible

#Notes for people wanting to use this playbook
  - For proof of concept I disabled Selinux, however; this is undesirable in production and instead you will have to know the appropriate way to configure Selinux on your machines
  - This playbook assumes your database is on a different machine. If you have everything all on one machine, it's easy enough to adjust this script for a single server.

#After running the playbook
 - Point your webbrowser to your webserver with SeedDMS installed:
       "http://hostname/seeddms"
- In the page below click on "Start installation"
