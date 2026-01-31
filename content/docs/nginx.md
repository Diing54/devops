---
title: "NGINX"
date: 2026-01-31
tags: []
---

*Date: 2026-01-31*
{{< tags >}}

## Intro
NGINX is a high-perfomance open-source software that acts as a websever, reverse proxy and a load balancer, efficiently handling thousands of simulataneous connections by serving static content, managing traffic and improving application speed and security.

### Key Functions of NGINX
1. A web server - Serving static content
2. A load balancer - Distributes incoming traffic across multiple backend servers
3. A reverse proxy - Acts on behalf of a backend server by receiving requests

- **Caching** is a core functionality of NGINX proxy - This means a cached file is stored on standby such that when a request is received, there is no need to hit the server, especially on frequently requested content.

*NGINX proxy is like the NAT of servers*

- NGINX can also handle SSL/TSL encryption and decryption. They can also forward encrypted data to the backend servers to be decrypted.
- NGINX proxy can be configured for compression of large images or videos to save on bandwidth and also segmentation; sending response in chunks.

### NGINX Configuration
NGINX is configured on a file named nginx.conf where a user can manually configure the working of NGINX. The following can be configured in the file ;
1. NGINX as a web server or proxy server
2. Configuring load balancing e.g. which load balancing algorithm to use
3. Caching configuration e.g. how long data can live in the cache

## References
- https://youtu.be/iInUBOVeBCc?si=GsFZqke3WK_WJSmC
