# Using Nginx
## Step 1: Install Nginx
If Nginx is not installed:
```
sudo apt-get update
sudo apt-get install nginx
```
## Step 2: Configure Nginx
1. Create a Configuration File:
```
sudo nano /etc/nginx/sites-available/vocard
```
Add:
```
server {
    listen 80;
    server_name yourdomain.com;

    location / {
        proxy_pass http://localhost:PORT;  # Replace with your dashboard's port
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
2. Enable the Configuration:
```
sudo ln -s /etc/nginx/sites-available/vocard /etc/nginx/sites-enabled/
```

3. Test and Restart Nginx:
```
sudo nginx -t
sudo systemctl restart nginx
```

## Step 3: Enable HTTPS with Let’s Encrypt
1. Install Certbot:
```
sudo apt-get install certbot python3-certbot-nginx
```

2. Obtain a Certificate:
```
sudo certbot --nginx -d yourdomain.com
```

3. Auto-Renewal:
Ensure Certbot auto-renews the certificate:
```
sudo certbot renew --dry-run
```