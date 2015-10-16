provisioningDO
============

Overview:
---------
This is a rakefile with several tasks to provision Debian i386/amd64 VPS with puppet client up and running on www.digitalocean.com

This script suposes:
 * The user your are running it has sudo access to run without password /usr/bin/puppet, /bin/tar
   
   **Example of a sudoers file:** user ALL=(ALL) NOPASSWD: /usr/bin/puppet, /bin/tar
   
 * You have tugboat CLI installed and configured https://github.com/pearkes/tugboat
 * You are running it in the puppetmaster server, as it need access to the CA to create/clean the puppet certificates 

Variables:
----------

There are some variables than must be set in order to deploy the droplet with your specifications

**SERVER_ROLE** eg: pentahopdi
This is a local fact that will be populated and can be used to tag servers on deployment time
facter -p server_role
server_role:
**SERVER** eg: vps1.example.com

**DOMAIN** eg: example.com

**ENVIRONMENT** eg: production/test/QA # This is the puppet environment

**REGION** eg: 9 # for AMS3

**SIZE** eg: 66 # default for a 512 droplet

**IDTEMPLATE**  should  be 12778278 for amd64 debian image 

Usage:
------

Example:

To deploy a new amd64 server:

SERVER_ROLE=pentahopdi ENVIRONMENT=production IDTEMPLATE=12778278 REGION=9 SIZE=66 SERVER=vps1.example.org DOMAIN=example.com rake droplet_deploy


To decommission a server:

SERVER_ROLE=pentahopdi ENVIRONMENT=production IDTEMPLATE=12778278 REGION=9 SIZE=66 SERVER=vps1.example.org DOMAIN=example.com rake droplet_decommission

Live example:
------------
Bootstrapping a new VPS on a DigitalOcean droplet with puppet client up and running in **4m15secs**:

https://asciinema.org/a/ex42dlm530maj5viplg6j8pr0

Website:
--------
http://www.elsotanillo.net/2013/11/bootstrapping-a-new-vps-on-a-digitalocean-droplet-with-puppet-client-up-and-running-in-4-mins-15-secs/
