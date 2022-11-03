# Virtual-Hosts

Although it is possible to add applications to your server by putting them in subdirectories ```https://mydomain/creative3```, it is actually better to give each application their own domain ```https://creative3.mydomain```.  When you do this, the react build content can be placed in the directory served by the domain and it is actually pretty easy to do.

1. First make sure that you have set up [Route53](https://github.com/BYU-CS-260/AWS-Setup/blob/main/domain.md) so that it includes subdomains by creating an A record for */mydomain.

2. Then add a section to your Caddyfile with the path to where you want the files for the subdomain to be located
```
yourdomain.net {
        # Set this path to your site's directory.
        root * /usr/share/caddy

        handle /api/* {
                reverse_proxy localhost:3000
        }
        # Enable the static file server.
        file_server

}

creative3.yourdomain.net {
        # Set this path to your site's directory.  /var/www/html is the standard place for content
        root * /var/www/html
        
        # Enable the static file server.
        file_server
}
```

3. Now restart Caddy and you should be access your domain through ```https://creative3.mydomain``` in your browser
```
sudo systemctl restart caddy 
```
