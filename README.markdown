provisioningDO
============

Overview:
---------
This is a rakefile with several tasks to provision Debian i386/amd64 VPS with puppet client up and running on www.digitalocean.com

This script suposes:
 * The user your are running it has sudo access to run without password /usr/bin/puppet, /bin/tar
   
   **Example of a sudoers file:** (ALL : ALL) NOPASSWD: /usr/bin/puppet, /bin/tar
   
 * You have tugboat CLI installed and configured https://github.com/pearkes/tugboat
 * You are running it in the puppetmaster server, as it need access to the CA to create/clean the puppet certificates 

With few changes changes this rake file can be adapted to deploy ubuntu images too (for next release) and with some extra work to the rest of linux distributions

Variables:
----------

There are some variables than must be set in order to deploy the droplet with your specifications

**SERVER** eg: vps1.example.com

**DOMAIN** eg: example.com

**ENVIRONMENT** eg: production/test/QA # This is the puppet environment

**REGION** eg: 1 # for NY1

**SIZE** eg: 66 # default for a 512 droplet

**IDTEMPLATE**  should  be 303619 for a i386 or 308287 for a amd64 debian image 

Usage:
------

Example:

To deploy a new i386 server:

ENVIRONMENT=production REGION=1 SIZE=66 SERVER=vps1.example.com DOMAIN=example.com rake droplet_deploy

To decomission a server:

SERVER=vps1.example.com DOMAIN=example.com rake droplet_decomission

Live example:
------------
Bootstrapping a new VPS on a DigitalOcean droplet with puppet client up and running in **4m15secs**:

http://shelr.tv/records/52934c959660805c3500001b
