nginxmgr
========

Management tool for nginx

## Installation:

Requirements includes `>= Ruby 1.9.1`, `gem install micro-optparse` and `git`.

    git clone https://github.com/mikemackintosh/nginxmgr
    cd nginxmgr
    chmod +x nginxmgr

## Usage:

Here is a copy of the usage info:

    # nginxmgr -h
    nginxmgr: by Zyp.io
        -i, --ip *                       set virtual host ip address
        -c, --create []                  create a site supplying the server name string
        -e, --enable                     enable a site supplying the server name string
        -d, --disable                    disable a site supplying the server name string
        -D, --delete                     delete a site supplying the server name string
        -h, --help                       Show this message
        -v, --version                    Print version

## To Create a Site

To use the utility, you would run the following command:

    splug@dev.ve.zyp.io:~$ sudo nginxmgr -c "www.example.com,example.com,*.example.com"
    Creating site: www.example.com
    [ Completed ] Site has been created
    Enabling site: www.example.com
    Testing nginx configuration: nginx.
    Restarting nginx: nginx.
    [ Completed ] This site has been enabled and nginx reloaded
    Thank you and have a nice day!

This would create a directory in `/var/www/www.example.com` (your site name is the first fqdn that you pass) and skeleton directories of `web` and `logs` within in. A template for nginx will also be placed within `/etc/nginx/sites-available` for your domain.

***Note:*** By default, sites that are newely created are automatically 

By default the listening IP address and port in `*:80`. You can change this by passing option `-i ip.ad.dr.ess`. 


## To Enable a Site

This utility will create a symbolic link from the `sites-available` dir to `sites-enabled`, run `configtest` on nginx, and restart nginx:

    splug@dev.ve.zyp.io:~$ sudo nginxmgr -e www.example.com
    Enabling site: www.example.com
    Testing nginx configuration: nginx.
    Restarting nginx: nginx.
    [ Completed ] This site has been enabled and nginx reloaded
    Thank you and have a nice day!

## To Disable a Site

This utility will delete the symbolic link from the `sites-enabled` dir, run `configtest` on nginx, and restart it:

    splug@dev.ve.zyp.io:~$ sudo nginxmgr -d www.example.com
    Restarting nginx: nginx.
    [ Done! ]
    Thank you and have a nice day!

## To Delete a Site

The `-D`, `--delete` switch will remove your domains configuration from nginx, restart if it is currently active, and move the directory  `/var/www/domain` to `/var/www/domain.old`

    splug@dev.ve.zyp.io:~$ sudo nginxmgr -D www.testing2.com
    The www directory for this site has been moved to: '/var/www//www.testing2.com.old'
    [ Done! ]
    Thank you and have a nice day!
    
## Errors

If you receive the following error:

    /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- micro-optparse (LoadError)
        from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
	    from /usr/bin/nginxmgr:5:in `<main>'

Make sure you execute `sudo gem install micro-optparse`. This will install the missing dependency.
