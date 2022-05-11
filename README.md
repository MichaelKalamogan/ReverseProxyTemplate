# Reverse proxy template

- This is a reverse proxy template using Nginx and Docker.
- Realise that while there are many references available on the internet, none are easy to understand or straightforward to implement. Thus I wrote one based on my own experience trying to figure this out as a new developer.

## Stepx
1) replace the server_name in nginx/conf, line 42 with the required domain.
2) docker-compose up -d
3) run the command "docker-compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot/ -d your-website.com", replacing your-website.com with your required domain.
4) Once the certificates are there, uncomment lines 1-36 in frontend.conf, replacing the server_name in line 4,7,8 with the required domain.
5) docker-compose restart
6) test if the certificate renewal works by running "docker-compose run --rm certbot renew --dry-run"


### possible issues
Sometimes the ports 443 and 80 may already be occupied. run 
a.	netstat -tulpn | grep ":80"
b.	Kill the processes that are using port 80 (and 443 if needed)
