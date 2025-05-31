# nginx_reverce_proxy_228
server {
    listen 80;
    server_name moodle moodle.au-team.irpo;

    location / {
        proxy_pass http://172.16.4.2:80;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
server {
    listen 80;
    server_name wiki wiki.au-team.irpo;

    location / {
        proxy_pass http://172.16.5.2:80;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
