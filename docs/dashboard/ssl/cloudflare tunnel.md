# Using Cloudflare Tunnel

To securely connect your Vocard Dashboard, follow these steps to create and configure a Cloudflare Tunnel using the Zero Trust platform.

## Step 1: Create a Tunnel

1. **Log in to Zero Trust**: Navigate to the [Zero Trust dashboard](https://dash.teams.cloudflare.com).

2. **Go to Networks > Tunnels**: In the sidebar, select **Networks**, then click on **Tunnels**.

3. **Create a Tunnel**:
    - Click on **Create a tunnel**.
    - Choose **Cloudflared** as the connector type and click **Next**.
    - Enter a name for your tunnel (e.g., `Vocard-Dashboard`) that reflects the resources you want to connect.
    - Select **Save tunnel**.

4. **Install Cloudflared**: 
    - Make sure the environment under **Choose an environment** matches your operating system.
    - Copy the command provided in the dashboard and paste it into your terminal. Run the command to install and start Cloudflared.
    - Once the command completes, your connector will appear in Zero Trust.

5. **Select Next**: Continue to the next step.

## Step 2: Connect an Application or Network

### 2a. Connect an Application

Before you can connect an application through your tunnel, ensure you have:

- Added your website to Cloudflare.
- Changed your domain nameservers to Cloudflare.

**To connect an application**:

1. **Add a Public Hostname**:
    - In the **Public Hostnames** tab, click **Add a public hostname**.
    - Enter a subdomain and select a domain from the dropdown.
    - Specify any subdomain or path information. Note: For multi-level subdomains, you will need to order an Advanced Certificate.

2. **Specify a Service**:
    - Enter the service URL (e.g., `https://localhost:8000`).

3. **Additional Application Settings**:
    - Add any [parameters](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/configure-tunnels/cloudflared-parameters/origin-parameters/) you would like for your tunnel configuration.

4. **Select Save Hostname**: Your application is now publicly accessible on the Internet. To manage user access, consider creating an Access application.

### 2b. Connect a Network

**To connect a private network**:

1. **In the Private Networks Tab**:
    - Add an IP address or CIDR.
    - Select **Save tunnel**.
    
## Step 3: Test Your Setup
Navigate to https://yourdomain.com in your browser to verify that the HTTPS connection is working.
