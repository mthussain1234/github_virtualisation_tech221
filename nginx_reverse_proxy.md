# Nginx Reverse Proxy

## What are ports? 

Ports are communication endpoints that enable computers to send and receive data over a network.

## What is a reverse proxy? How is it different to a proxy?

A reverse proxy is a server that sits in front of one or more web servers and routes client requests to those servers. It is different from a regular proxy in that it acts on behalf of servers, rather than clients

## Make a diagram for the above point to go with your explanation

![image](https://user-images.githubusercontent.com/129314018/232845745-da2b21bf-e4d6-4199-881d-370869069105.png)

## What is Nginx's default configuration (hint - 'sites-available' directory)

Nginx's default configuration includes a 'default' file located in the '/etc/nginx/sites-available' directory.

## How do you set up a Nginx reverse proxy?

To set up an Nginx reverse proxy, you need to:

* Install Nginx on the server
* Configure a new virtual host that listens on the desired port (e.g., port 80)
* Set up the reverse proxy in the virtual host configuration, specifying the backend server(s) to forward requests to, and any necessary proxy headers.
* Start or restart the Nginx service to apply the new configuration.
