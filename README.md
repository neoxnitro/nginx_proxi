# nginx_proxy
An example of using Nginx as a proxy: it allows a single server IP to host multiple services, with the proxy routing requests to the appropriate service.

N.B.  
- The example includes a docker-compose file to containerize Nginx.  
- Ports 80 (HTTP) and 443 (HTTPS) are used on the main server.  
- Let's Encrypt certificates are used for HTTPS (each domain has its own certificate).  
- Keep in mind that, in this example, the nginx_proxy ensures the encryption/decryption of the SSL layer; the service endpoints only need to use HTTP.

N.B.  
- In nginx.conf,  
- http://teastytrack_nginx and http://homesite_nginx correspond to the Docker containers' addresses (these are internal Docker addresses only accessible to containers that share the same Docker network).
