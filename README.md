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

probros portov hq
ip nat source static tcp 192.168.100.2 80 172.16.4.2 80
ip nat source static tcp 192.168.100.2 2025 172.16.4.2 2025
![image](https://github.com/user-attachments/assets/4c4a4502-d2b7-4bfe-b6ae-98e7743993c2)

probros portov br
ip nat source static tcp 192.168.150.2 8080 172.16.5.2 80
ip nat source static tcp 192.168.150.2 2025 172.16.5.2 2025
![image](https://github.com/user-attachments/assets/200c22f6-0c19-416b-af15-d2a782d3a54b)
