
# NGINX

sudo nginx -v			: versión ejecutada
sudo nginx -t			: view configuration in execution
sudo nginx restart		: reiniciar nginx.

### Nginx Administration
```
sudo systemctl reload nginx
sudo systemctl stop nginx
sudo systemctl start nginx
sudo systemctl status nginx
sudo systemctl enable nginx
```

### Some Linux commands
```
sudo rm
sudo rmdir
sudo mkdir
sudo nano
sudo vim
sudo vi
```

### Install Telnet to review network
```
sudo yum install telnet -y
telnet your.mysql.host 3306
telnet 98.86.63.172 3306
```

### Install nc to check your network
```
nc -zv 98.86.63.172 3306
```
