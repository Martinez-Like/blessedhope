# Free Website Hosting Guide

## Option 1: InfinityFree (PHP Support)

### Steps:
1. Go to https://infinityfree.net
2. Click "Sign Up" and create an account
3. Verify your email address
4. Click "Create Account" in the control panel
5. Choose a subdomain (e.g., yourproject.infinityfreeapp.com)
6. Wait for account creation (can take a few minutes)

### File Upload:
1. Access File Manager from control panel
2. Navigate to `htdocs` folder
3. Upload all your PHP files:
   - index.php (main page)
   - about.php
   - contact.php
   - get-involved.php
   - news.php
   - partners.php
   - programs.php
   - test_db.php
   - assets/ folder
   - database/ folder
   - includes/ folder

### Database Setup (if needed):
1. Create MySQL database in control panel
2. Update your database connection files with new credentials
3. Import your database using phpMyAdmin

## Option 2: 000WebHost

### Steps:
1. Go to https://www.000webhost.com
2. Sign up for free account
3. Create new website
4. Choose free subdomain
5. Use File Manager to upload files to `public_html`

## Option 3: GitHub Pages + Static Conversion

If you can convert PHP to static HTML:
1. Create GitHub repository
2. Upload HTML/CSS/JS files
3. Enable GitHub Pages in repository settings
4. Access via username.github.io/repository-name

## Option 4: Heroku (with PHP buildpack)

1. Install Heroku CLI
2. Create Procfile: `web: vendor/bin/heroku-php-apache2`
3. Create composer.json with PHP version
4. Deploy via Git

## Security Notes:
- Remove any sensitive database credentials before uploading
- Use environment variables for sensitive data
- Ensure proper file permissions
- Test all functionality after deployment

## Troubleshooting:
- If PHP files download instead of executing, check file extensions
- Ensure index.php is in the root directory
- Check PHP version compatibility
- Verify database connections work with hosting provider's settings