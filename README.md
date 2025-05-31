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

probros portov hq:
ip nat source static tcp 192.168.100.2 80 172.16.4.2 80
ip nat source static tcp 192.168.100.2 2025 172.16.4.2 2025

![image](https://github.com/user-attachments/assets/860e7d80-cb26-43f3-bac6-d40d167709d9)


probros portov br:
ip nat source static tcp 192.168.150.2 8080 172.16.5.2 80
ip nat source static tcp 192.168.150.2 2025 172.16.5.2 2025

![image](https://github.com/user-attachments/assets/6266eacb-5584-49a0-89b5-212635e307cf)

ОТКЛЮЧИТЬ SELINUX na ISP !!!!!
nano /etc/selinux/config
SELINUX=permissive

для вики меняем в LocalSettings.php

![image](https://github.com/user-attachments/assets/78de2d75-dcb2-49ac-9972-df0162d231bd)

для мудл меняем 

![image](https://github.com/user-attachments/assets/c0a0d69f-706d-443b-ad81-0f47f2230679)
