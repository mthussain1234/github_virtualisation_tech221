# Nginx Reverse Proxy

## What are ports? 

Ports are communication endpoints that enable computers to send and receive data over a network.

## What is a reverse proxy? How is it different to a proxy?

A reverse proxy is a server that sits between the internet and a web server. It forwards client requests to the according web server and sends back the according response back to the client, whilst also hiding the web server itself from the client.

Forward proxy stands between client and internet, fowrwards client requests to the end server on the internet, and will ultimately send the response back to the client.

### Direct comparisons between forward and reverse proxy

* A reverse proxy is used to give clients indirect access to web servers, whereas a forward proxy is used to give clients indirect access to the internet.

* A reverse proxy is situated on the server's side of the network, while a forward proxy is situated on the client's side.

* Since the client must set up their browser to use the forward proxy, the client can see the forward proxy. A reverse proxy, on the other hand, is invisible to the client because the client is unaware of its existence.

* Utilising a reverse proxy can help balance the load and boost performance by distributing incoming requests among several web servers. This capability is not available through a forward proxy.

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
