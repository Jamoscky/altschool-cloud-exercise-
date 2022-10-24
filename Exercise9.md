*Ansible playbook*
 
 ---
- name: Setup Web Server
  hosts: all
  remote_user: root

  tasks:
  - name: Install Apache Server
    apt:
     name: apache2
     state: present
  - name: Copying file
    become: true
    copy:
      src: ~/ansible/note
      dest: /var/www/html/index.html

  - name: Set timezone to Africa/Lagos
    community.general.timezone
     name:  Africa/Lagos

*Output of systemctl status Apache2*

apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2022-10-19 18:13:58 UTC; 3 days ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 18428 ExecReload=/usr/sbin/apachectl graceful (code=exited, status=0/SUCCESS)
   Main PID: 916 (apache2)
      Tasks: 6 (limit: 1131)
     Memory: 16.5M
     CGroup: /system.slice/apache2.service
             ├─  916 /usr/sbin/apache2 -k start
             ├─18444 /usr/sbin/apache2 -k start
             ├─18445 /usr/sbin/apache2 -k start
             ├─18446 /usr/sbin/apache2 -k start
             ├─18447 /usr/sbin/apache2 -k start
             └─18448 /usr/sbin/apache2 -k start

Oct 20 00:00:05 ubuntu-focal systemd[1]: Reloaded The Apache HTTP Server.
Oct 22 23:52:12 ubuntu-focal systemd[1]: Reloading The Apache HTTP Server.
Oct 22 23:52:13 ubuntu-focal apachectl[9314]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally>
Oct 22 23:52:13 ubuntu-focal systemd[1]: Reloaded The Apache HTTP Server.
Oct 22 23:59:08 ubuntu-focal systemd[1]: Reloading The Apache HTTP Server.
Oct 22 23:59:08 ubuntu-focal apachectl[17184]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globall>
Oct 22 23:59:08 ubuntu-focal systemd[1]: Reloaded The Apache HTTP Server.
Oct 23 00:00:02 ubuntu-focal systemd[1]: Reloading The Apache HTTP Server.
Oct 23 00:00:03 ubuntu-focal apachectl[18432]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globall>
Oct 23 00:00:03 ubuntu-focal systemd[1]: Reloaded The Apache HTTP Server.
~
