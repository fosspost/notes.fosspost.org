# Nginx

## [Tip] Easily Deploy Flask Applications With UWSGI & Nginx

### Description

The process of deploying Flask applications with Nginx may be so hard if it's your first time. Fortunutly, you can now do it in a few steps.

### Solution

Just run the following uwsgi command:

    uwsgi --socket :8080 --chdir /var/www/myflaskdir --module myflaskfile:app &

Which would run your **myflaskfile** app on the **8080** port and will use **/var/www/myflaskdir** as your working directory. 

Now, to make Nginx accept requests to it as a domain name, add the following to your **/etc/nginx/nginx.conf** file:

	server {

	    root /var/www/myflaskdir;
	    server_name sub.example.com;

	    location / {
		  include         uwsgi_params;
		  uwsgi_pass   0.0.0.0:8080;
	    }

		location ^~ static/  {
		    include  /etc/nginx/mime.types;
		    root /var/www/myflaskdir/;
		}

	}
	
**sub.example.com** can be any domain name you want. Make sure the **uwsgi_pass** parameter is the same as the one you are using in your uwsgi command.

Finally, reload and restart your Nginx server:

    sudo service nginx reload
    sudo service nginx restart

## [Note] Apache's .htaccess File May Not Work With Nginx

### Description

If you are transferring your websites from a web server which is running Apache to another hosting/VPS which uses Nginx, sometimes you may notice a blank white page when you try to open your new website. Nothing shows in the log files and everything seems to be working properly.

You check for MySQL, firewall, fail2ban, configuration files and everything else. But still, the problem is there: A white page showing nothing.

### Solution

The problem is caused by the apache's **.htaccess** file. It may not be fully comptabile with what nginx can understand.

Moving the hidden **.htaccess** file or removing would solve the issue. Note that you may lose redirections and other stuff you had in your original **.htaccess** file. And which could affect your work.
