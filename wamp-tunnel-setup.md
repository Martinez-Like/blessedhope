# WAMP Server Tunneling Setup Guide

## Step 1: Configure WAMP for External Access

### Enable External Access in WAMP:
1. **Start WAMP** and ensure it's running (green icon)
2. **Left-click WAMP icon** → Apache → httpd.conf
3. **Find this line** (around line 224):
   ```
   Require local
   ```
4. **Replace with**:
   ```
   Require all granted
   ```
5. **Save and restart Apache**

### Alternative Method - Virtual Host:
1. **Left-click WAMP icon** → Apache → httpd-vhosts.conf
2. **Add this configuration**:
   ```apache
   <VirtualHost *:80>
       DocumentRoot "C:/wamp64/www/your-project-folder"
       ServerName localhost
       <Directory "C:/wamp64/www/your-project-folder">
           AllowOverride All
           Require all granted
       </Directory>
   </VirtualHost>
   ```

## Step 2: Choose Your Tunneling Method

### Method 1: ngrok (Recommended)
1. **Download** from https://ngrok.com/download
2. **Extract** to a folder (e.g., C:\ngrok)
3. **Sign up** for free account at ngrok.com
4. **Get auth token** from dashboard
5. **Open Command Prompt** and navigate to ngrok folder
6. **Authenticate**: `ngrok authtoken YOUR_TOKEN`
7. **Start tunnel**: `ngrok http 80`
8. **Copy the HTTPS URL** (e.g., https://abc123.ngrok.io)

### Method 2: LocalTunnel (No signup)
1. **Install Node.js** if not installed
2. **Install localtunnel**: `npm install -g localtunnel`
3. **Start tunnel**: `lt --port 80`
4. **Copy the URL** provided

### Method 3: Cloudflare Tunnel
1. **Download cloudflared** from Cloudflare
2. **Run**: `cloudflared tunnel --url http://localhost:80`
3. **Copy the URL** provided

## Step 3: Test Your Setup

1. **Start WAMP** (ensure green icon)
2. **Start your chosen tunnel**
3. **Visit the tunnel URL** in your browser
4. **Share the URL** with others

## Security Considerations

- **Temporary use only** - don't leave tunnels running permanently
- **Remove sensitive data** before sharing
- **Monitor access** - some tools show visitor logs
- **Stop tunnel** when done sharing

## Troubleshooting

### Common Issues:
- **404 Error**: Check if your project is in the correct www folder
- **Access Denied**: Verify WAMP configuration changes
- **Tunnel Not Working**: Restart WAMP and tunnel service
- **Database Errors**: Ensure MySQL is running in WAMP

### WAMP Project Location:
- Default: `C:\wamp64\www\your-project-name\`
- Access via: `http://localhost/your-project-name/`
- Tunnel will expose: `https://tunnel-url.com/your-project-name/`