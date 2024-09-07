# Third Branch: Installations
### Takes Parameters:
- Hosts from the hosts file (File exists on every branch with a playbook)
- Port(The port NGINX will be operating on)
- index file(The basic HTML file that will be displayed by nginx)
- server(Hostname of the server that will host the html file)
- title(Text that will be displayed in the HTML file)
- Ansible Credentials - Used for the ansible playbook
### steps:
- Installation of Nginx on both Rocky and Debian hosts and starting the service
- Removing existing NGINX configuration file, and index.html file in /var/www/html (If exists)
- Copying new NGINX conf and html file using jinja templates
- restarting NGINX
