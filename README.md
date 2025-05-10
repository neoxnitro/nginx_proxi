# nginx_proxy
An example of using Nginx as a proxy: it allows a single server IP to host multiple services, with the proxy routing requests to the appropriate service.

```markdown
## Visualization of Nginx Proxy Setup

The table below shows how the Nginx proxy routes client requests to internal services.

| Client URL                        | Nginx Proxy IP         | Protocol | Target Service       |
|-----------------------------------|------------------------|----------|----------------------|
| https://www.teastytrack.com       | 92.14.18.20 (Public)   | HTTPS    | http://teastytrack   |
| https://www.amazingsite.com       | 92.14.18.20 (Public)   | HTTPS    | http://homesite      |
| http://local-client               | 192.168.1.14 (Local)   | HTTP     | http://teastytrack   |

### Explanation
- **Clients** send HTTPS requests (or HTTP for local clients) to the Nginx proxy at the specified public or local IP address.
- The **Nginx proxy** routes these requests to the appropriate internal service (`teastytrack` or `homesite`) over HTTP.
- The Nginx proxy handles SSL termination (encryption/decryption) for HTTPS requests, allowing services to use plain HTTP internally.
```

N.B.  
- The example includes a docker-compose file to containerize Nginx.  
- Ports 80 (HTTP) and 443 (HTTPS) are used on the main server.  
- Let's Encrypt certificates are used for HTTPS (each domain has its own certificate).  
- Keep in mind that, in this example, the nginx_proxy ensures the encryption/decryption of the SSL layer; the service endpoints only need to use HTTP.

N.B.  
- In nginx.conf,  
- http://teastytrack_nginx and http://homesite_nginx correspond to the Docker containers' addresses (these are internal Docker addresses only accessible to containers that share the same Docker network).

update 10/05/24: fix let's encrypt generate/renewal ssl certificat
