# Docker Nginx

## Sample compose file entry
```
nginx: 
 image : your_nginx_image/nginx:latest 
 ports : 
     - “80:80” 
     - “443:443”
 volumes: 
     - /data/certs:/etc/nginx/certs
```
