# Virtual-Hosts

Although it is possible to add applications to your server by putting them in subdirectories ```https://mydomain/creative3```, it is actually better to give each application their own domain ```https://creative2.mydomain.  When you do this, the react build content can be placed in the directory served by the domain and it is actually pretty easy to do.

1. First make sure that you have set up Route53 so that it includes 
