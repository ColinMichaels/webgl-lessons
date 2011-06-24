Anyone that may run across this.  This is my WebGl playground while I'm learning and practicing the tutorials.  You can find all the original information from the creator at the links below.  Feel free to poke around at my changes but really this is just me playing around.    

-Colin Michaels

Some lessons in WebGL
---------------------

This repository contains a series of simple lessons in WebGL, plus some
related examples.

The folders named lesson01, lesson02, and so on are a sequential tutorial and
are best understood using the explanatory text at:

    <http://learningwebgl.com/lessons/>

The form of the first ten lessons is *very* loosely based on NeHe Productions'
well-known OpenGL tutorial, which can be found here:

    <http://nehe.gamedev.net/>

The lessons from 11 onwards are not related to the NeHe ones.

The folders named example01 etc are example code for interesting stuff outside
the scope of the tutorial, and have their own README.txt files with details.


Notes for working in Chrome
---------------------------

When experimenting with the lessons in Chrome you will need to run them from a
local web server to avoid security issues loading from a different origin.

Here are instructions on how to do that using Apache under Mac OS X; GNU/Linux
will be similar.  If you're on Windows, check out Xampp at
<http://www.apachefriends.org/en/xampp.html>


1) Add an entry for webgl-lessons.local in /etc/hosts.

This will need to be done as the root user using your preferred editor:

    $ sudo <editor> /etc/hosts

Add the following line and save the file:

    127.0.0.1       webgl-lessons.local

Tell the operating system to flush and reload the local DNS cache:

    dscacheutil -flushcache

Test to see if http://webgl-lessons.local/ is working:

    $ dscacheutil -q host -a name http://webgl-lessons.local/
    name: http://webgl-lessons.local/
    ip_address: <ip_address>

2) Add an Apache vhost configuration:

This will need to be done as the root user using your preferred editor:

    $ sudo <editor> /private/etc/apache2/extra/httpd-vhosts.conf

Add the following vhost configuration replacing <path-to-webgl-lessons> with
the actual path on your filesystem:

    <VirtualHost webgl-lessons.local:80>
       ServerName webgl-lessons
       DocumentRoot <path-to-webgl-lessons>/
       <Directory <path-to-webgl-lessons>>
         Options +Indexes +FollowSymLinks +MultiViews +Includes
         AllowOverride All
         Order allow,deny
         Allow from all
         DirectoryIndex index.html
      </Directory>
    </VirtualHost>

After making the change in the Apache vhost configuration first confirm the
syntax for the Apache configuration is still correct:

    $ apachectl configtest
    Syntax OK

If the syntax is OK then restart Apache:

    $ sudo apachectl restart

Now you can open the webgl-lessons in any local browser at this url:
<http://webgl-lessons.local/>
