+++
title = "Public website"
date = 2023-02-28

[taxonomies]
categories = ["software"]

[extra]
repo_path = "vanbuncha/zola_site"
+++

Public website with self-hosting

<!-- more -->

# Deploying My Website onto a Raspberry Pi with Apache Server using Cloudflare and SSG Zola

Hello, fellow tech enthusiasts! In this blog post, I'm excited to share my experience of deploying my website onto a Raspberry Pi with Apache server using Cloudflare and SSG Zola.

Before we get started, I should note that I'm not a web development expert. However, I love tinkering with technology and learning new things, and that's how I ended up taking on this challenge.

## Installing Apache Server

First things first, I made sure that my Raspberry Pi was up-to-date with the latest software updates. Next, I installed Apache server on the Pi by running the following command in the terminal:

    sudo apt-get install apache2

Once Apache was up and running, I tested it out by typing the IP address of the Raspberry Pi into a web browser. Lo and behold, the Apache default page was displayed!

## Configuring My Router and DNS

When I set out to host my website on a Raspberry Pi, I ran into a roadblock when I realized that my router was unable to port forward to the Pi due to my ISP's carrier-grade NAT. I knew that I needed a solution that would allow me to host my website securely and reliably without relying on port forwarding. After some research, I came across Cloudflare Tunnel, which seemed like the perfect solution.

To get started, I created an account on Cloudflare and downloaded the Cloudflare Tunnel CLI on my Raspberry Pi. I then configured the tunnel using the command line interface, specifying my local host and port number, and giving it a name.

Once the tunnel was set up, I tested it out by visiting the hostname that Cloudflare had assigned to my tunnel. To my delight, my website was now accessible from the internet through Cloudflare's servers. Even better, the tunnel was secured with TLS encryption, providing an added layer of security to my website.

Using Cloudflare Tunnel allowed me to bypass my router's inability to port forward to my Raspberry Pi, and host my website reliably and securely. The setup was relatively easy and straightforward, and I was able to get my website up and running in no time. If you're facing a similar port forwarding issue, I highly recommend giving Cloudflare Tunnel a <a href="https://pimylifeup.com/raspberry-pi-cloudflare-tunnel/">try</a>.
## Installing SSG Zola

With Apache and DNS set up, I was ready to install SSG Zola, a static site generator. I used SSG Zola to create a simple website in Markdown language. Once the site was ready, I used the zola build command to generate the static HTML files for my website.

SG Zola is a static site generator (SSG) that allows you to create fast, secure, and modern websites with ease. Unlike traditional content management systems (CMS) that require a database and server-side processing, static site generators like Zola generate static HTML, CSS, and JavaScript files that can be served directly by a web server, making them faster, more secure, and easier to host.

Zola is written in Rust, a fast and safe systems programming language, and is designed to be easy to use and highly customizable. It comes with a powerful set of features, including a built-in web server for local development, support for templates, partials, and custom shortcodes, automatic image resizing and optimization, and support for multiple content formats including Markdown, HTML, and JSON.



## Uploading My Site to the Raspberry Pi

Deploying my website to my Raspberry Pi was a simple process thanks to GitHub and a few simple command line commands. First, I created a GitHub repository for my website and pushed all of the necessary files to it. Then, on my Raspberry Pi, I opened up the command line and entered the following commands: (complied into a bash script)

bash

    sudo git clone https://github.com/vanbuncha/zola_site
    sudo mv zola_site/zola_site/public .
    sudo rm -rf html
    sudo mv public html
    sudo rm -rf zola_site
The first command clones my GitHub repository onto my Raspberry Pi. The second command moves the public folder from the zola_site directory to the current directory. The third command removes any existing html directory to avoid conflicts. The fourth command renames the public directory to html, which is the default directory for Apache to serve web pages from. The fifth and final command removes the zola_site directory to keep things tidy.

And that's it! My website was now deployed and accessible from my Raspberry Pi. Using GitHub to manage my website files made it easy to keep everything up to date, and the simple command line commands made deploying my website a breeze.

## Remote control and deployment

Accessing my Raspberry Pi on my local network was easy using SSH. I simply opened up the terminal on my computer and entered the command:

    ssh pi@192.168.1.XXX
where XXX is the IP address of my Raspberry Pi on the local network. This allowed me to connect to the Pi and access its command line interface from my computer. From there, I could run commands, manage files, and do pretty much anything else I needed to do on the Pi.

However, accessing my Raspberry Pi from a public network was a different story. Because my ISP used carrier-grade NAT, I couldn't access my Pi directly from the internet. This is where PiTunnel came in handy.

PiTunnel is a service that allows you to create a secure tunnel to your Raspberry Pi from the internet, bypassing any NAT or firewall restrictions. To set it up, I created an account on the PiTunnel website and downloaded the PiTunnel client on my Raspberry Pi. I then configured the tunnel and started the client.

With the tunnel running, I could access my Raspberry Pi from the internet by visiting the URL provided by PiTunnel. I could even use SSH to connect to the Pi and access its command line interface from anywhere in the world.

Using SSH to access my Raspberry Pi on my local network and PiTunnel to access it from the internet made managing my Pi a breeze. I could access it from anywhere, run commands, manage files, and do pretty much anything else I needed to do without any hassle.


## Conclusion

Deploying my website onto a Raspberry Pi with Apache server using Cloudflare and SSG Zola was a fun and educational experience. It allowed me to learn more about web development, Linux administration, and networking. I hope that sharing my experience will inspire others to tinker with technology and explore new horizons.

-  Webserver: Raspberry Pi 3 Model B, Raspbian, Apache/2.4.54 (Debian)
- Port forwarding: Cloudfare Tunnel
- Content: SSG Zola 

*text ai generated