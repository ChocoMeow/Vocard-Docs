# Using Cloudflare Proxy

## Step 1: Set Up Cloudflare
1. Add Your Domain: Log in to your Cloudflare account and add your domain if you haven't already.
2. Change DNS Settings: Ensure your A record points to your server's IP address and is proxied (orange cloud icon).

## Step 2: Enable HTTPS
1. SSL/TLS Settings: In the Cloudflare dashboard, navigate to the SSL/TLS settings.
2. Set SSL Mode: Choose "Full" or "Full (Strict)" for better security.
3. Automatic HTTPS Rewrites: Enable automatic HTTPS rewrites to help redirect HTTP traffic to HTTPS.

## Step 3: Test Your Setup
Navigate to https://yourdomain.com in your browser to verify that the HTTPS connection is working.