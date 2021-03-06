Quick HowTo
===========

Ssh to ``myserver`` with:

    ssh -L 8080:localhost:8080 myserver

run the proxy on ``myserver``:

    ./proxy -p 8080

On your computer, setup your browser to use the proxy ``localhost:8080`` (both for http and https). This will encrypt all HTTP traffic
between your computer and the server.

License
=======

MIT license. See the ``LICENSE`` file fore more details.

More Details
============

(This text and the script itself were taken from http://www.voidtrance.net/2010/01/simple-python-http-proxy/)


Some time ago my company announced that they will start capturing and logging all HTTP traffic to and from the company. While I definitely don't spend my time at work surfing the web, I don't appreciate them looking over my shoulder and checking up on everything that I visit and read on the web.

So I wrote a small application which is a very simple, rudementary HTTP proxy
server. It handles most HTTP traffic and some very simple FTP traffic (clicking
on FTP links from web pages). The code is based on Suzuki Hisao's `Tiny HTTP
Proxy <http://www.oki-osk.jp/esc/python/proxy/>`_ module. I enhanced it to make it a standalone application.

Usage Examples

Below is the script's help text which shows the accepted options and command line format:
proxy [-p port] [-l logfile] [-dh] [allowed_client_name ...]]
 
   -p       Port to bind to
   -l       Path to logfile. If not specified, STDOUT is used
   -d       Run in the background

To start the proxy server and bind it to port 22222 (the port on which it will listen and accept connections):

    proxy -p 22222

To start the proxy server, bind it to port 22222 and tell it to log all requests to the file proxy.log:

    proxy -p 22222 -l proxy.log

To start the proxy server where it only allows connections from IP 123.123.123.123:

    proxy 123.123.123.123

To start the proxy server bound to port 22222, log to file proxy.log and run the server in the background (as a daemon):

    proxy -p 22222 -l proxy.log -d
