nginxmgr
========

Management tool for nginx

## Installation:

    cd /usr/local
    sudo git clone https://github.com/mikemackintosh/nginxmgr
    cd nginxmgr
    sudo chmod +x n*

## Usage:

#### ncreatesite

To use the utility, you would run the following command:

    splug@dev.ve.zyp.io:~$ sudo ncreatesite 
    ## Creating nginx Site for Bakery Server ##
    Domain Name: 
    www.lastexample.com lastexample.com *.lastexample.com
    Creating domain www.lastexample.com

This would create a directory in `/var/www/www.lastexample.com` and skeleton directories of `web` and `logs` within in. A template for nginx will also be placed within `/etc/nginx/sites-available` for your domain.

#### nenablesite

This utility will create a symbolic link from the `sites-available` dir to `sites-enabled` dir. 

    splug@dev.ve.zyp.io:~$ sudo nenablesite
    ## Site Enabler for Bakery Server ##
    Enable nginx site: www.lastexample.com

#### ndisablesite

This utility will delete the symbolic link from the `sites-enabled` dir. 

    splug@dev.ve.zyp.io:~$ sudo nenablesite
    ## Site Disabler for Bakery Server ##
    Disable nginx site: www.lastexample.com
    Done! Site disabled
