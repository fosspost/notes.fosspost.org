# Nginx

## [Note] Apache's .htaccess File May Not Work With Nginx

### Description

If you are transferring your websites from a web server which is running Apache to another hosting/VPS which uses Nginx, sometimes you may notice a blank white page when you try to open your new website. Nothing shows in the log files and everything seems to be working properly.

You check for MySQL, firewall, fail2ban, configuration files and everything else. But still, the problem is there: A white page showing nothing.

### Solution

The problem is caused by the apache's **.htaccess** file. It is may not be fully comptabile with what nginx can understand.

Moving the hidden **.htaccess** file or removing would solve the issue. Note that you may lose redirections and other stuff you had in your original **.htaccess** file. And which could affect your work.
