```
apiVersion: v1
kind: ConfigMap
metadata:
  name: wallarm-sidecar-nginx-conf
data:
  default: |
    geo $remote_addr $wallarm_mode_real {
      default {{ .Values.wallarm.mode | quote }};
      # IP addresses and rules for US cloud scanners
      50.116.11.251 off;45.79.143.18 off;172.104.21.210 off;74.207.237.202 off;45.79.186.159 off;45.79.216.187 off;45.33.16.32 off;96.126.127.23 off;172.104.208.113 off;192.81.135.28 off;104.237.155.105 off;45.56.71.221 off;45.79.194.128 off;104.237.151.202 off;45.33.15.249 off;45.33.43.225 off;45.79.10.15 off;45.33.79.18 off;45.79.75.59 off;23.239.30.236 off;172.104.22.150 off;45.33.86.254 off;45.56.72.191 off;45.79.75.91 off;192.155.92.134 off;23.239.4.41 off;45.79.93.164 off;45.56.122.184 off;96.126.124.141 off;45.79.115.178 off;34.94.100.64 off;35.235.101.133 off;34.94.16.235 off;35.236.51.79 off;35.236.55.214 off;35.236.127.211 off;35.236.126.84 off;35.236.3.158 off;34.94.218.5 off;35.236.118.146 off;35.236.1.4 off;35.236.20.89 off;
      # IP addresses and rules for European cloud scanners
      139.162.148.184 off;139.162.151.155 off;139.162.159.244 off;139.162.151.10 off;139.162.159.137 off;39.162.157.131 off;139.162.144.202 off;139.162.130.66 off;139.162.158.79 off;139.162.156.102 off;85.90.246.120 off;172.104.128.215 off;139.162.174.26 off;139.162.182.20 off;139.162.190.22 off;139.162.168.17 off;139.162.167.19 off;139.162.170.84 off;139.162.191.89 off;139.162.176.169 off;139.162.184.225 off;139.162.185.243 off;172.104.143.34 off;139.162.178.148 off;139.162.186.136 off;139.162.163.61 off;139.162.171.141 off;139.162.179.214 off;139.162.187.138 off;139.162.164.41 off;139.162.172.35 off;139.162.180.37 off;139.162.188.246 off;172.104.139.18 off;172.104.152.28 off;139.162.177.83 off;172.104.240.115 off;172.105.64.135 off;139.162.153.16 off;172.104.241.162 off;139.162.167.48 off;172.104.233.100 off;172.104.157.26 off;172.105.65.182 off;172.104.138.5 off;172.104.150.243 off;139.162.190.165 off;139.162.166.202 off;139.162.174.220 off;139.162.182.156 off;139.162.190.86 off;139.162.167.51 off;139.162.175.71 off;172.104.152.54 off;172.104.151.59 off;172.104.128.67 off;172.104.152.96 off;139.162.145.238 off;172.104.128.103 off;172.104.139.37 off;139.162.184.33 off;139.162.186.129 off;172.104.154.128 off;172.104.146.90 off;172.104.128.44 off;85.90.246.49 off;139.162.146.245 off;139.162.171.208 off;172.104.252.112 off;139.162.132.87 off;139.162.162.71 off;172.104.229.59 off;172.104.152.244 off;172.104.250.27 off;139.162.130.123 off; 178.32.42.221 off;46.105.75.84 off;51.254.85.145 off;188.165.30.182 off;188.165.136.41 off;188.165.137.10 off;54.36.135.252 off;54.36.135.253 off;54.36.135.254 off;54.36.135.255 off;54.36.131.128 off;54.36.131.129 off;
    }
    server {
        listen 80 default_server;
        listen [::]:80 default_server ipv6only=on;
        server_name localhost;
        root /usr/share/nginx/html;
        index index.html index.htm;
        wallarm_mode $wallarm_mode_real;
        # wallarm_instance 1;
        set_real_ip_from 0.0.0.0/0;
        real_ip_header X-Forwarded-For;
        location / {
                proxy_pass http://localhost:{{ .Values.wallarm.app_container_port }};
                include proxy_params;
        }
    }
```