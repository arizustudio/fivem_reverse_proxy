<div align="center">
  <h1>FIVEM REVERSE PROXY</h1>
  <h3>Alternate connection for FIVEM Server.</h3>
  
  <a href="#install-in-ubuntu--debian">Install in Ubuntu/Debian</a> &#xa0; | &#xa0;
  <a href="#install-in-centos--alma-linux">Install in CentOS/Alma Linux</a>
</div>

# Install in Ubuntu / Debian
### Install Requirements
```
sudo apt update
sudo apt install haproxy -y
```
### Edit HAProxy configuration
```
sudo nano /etc/haproxy/haproxy.cfg
```
### Edit HAProxy configuration (change 8.8.8.8 to your main fivem server address)
```
frontend fivem_proxy
    bind *:30120
    mode tcp
    default_backend fivem_backend
backend fivem_backend
    mode tcp
    server fivem_main 8.8.8.8:30120 check
frontend fivem_proxy_voice
    bind *:30110
    mode tcp
    default_backend fivem_backend_voice
backend fivem_backend_voice
    mode tcp
    server fivem_main_voice 8.8.8.8:30110 check
```
Restart HAProxy
```
sudo systemctl restart haproxy
```
# Install in CentOS / Alma Linux
### Install Requirements
```
sudo yum install haproxy -y
```
or
```
sudo dnf install haproxy -y
```
### Enabe HAProxy
```
sudo systemctl enable haproxy
sudo systemctl start haproxy
```
### Edit HAProxy configuration
```
sudo nano /etc/haproxy/haproxy.cfg
```
### Edit HAProxy configuration (change 8.8.8.8 to your main fivem server address)
```
frontend fivem_proxy
    bind *:30120
    mode tcp
    default_backend fivem_backend
backend fivem_backend
    mode tcp
    server fivem_main 8.8.8.8:30120 check
frontend fivem_proxy_voice
    bind *:30110
    mode tcp
    default_backend fivem_backend_voice
backend fivem_backend_voice
    mode tcp
    server fivem_main_voice 8.8.8.8:30110 check
```
### Restart HAProxy
```
sudo systemctl restart haproxy
```
