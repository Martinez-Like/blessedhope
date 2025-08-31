# Heroku Deployment for PHP Project

## Prerequisites
- Git installed
- Heroku CLI installed
- Your PHP project files

## Setup Files Needed

### 1. composer.json
```json
{
    "require": {
        "php": "^7.4.0"
    }
}
```

### 2. Procfile (no extension)
```
web: vendor/bin/heroku-php-apache2
```

### 3. .htaccess (if needed for routing)
```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php [QSA,L]
```

## Deployment Steps

1. **Initialize Git repository** (if not already done):
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Login to Heroku**:
   ```bash
   heroku login
   ```

3. **Create Heroku app**:
   ```bash
   heroku create your-app-name
   ```

4. **Deploy**:
   ```bash
   git push heroku main
   ```

5. **Open your site**:
   ```bash
   heroku open
   ```

Your site will be available at: `https://your-app-name.herokuapp.com`

## Database Setup (if using MySQL)
1. Add ClearDB MySQL addon:
   ```bash
   heroku addons:create cleardb:ignite
   ```

2. Get database URL:
   ```bash
   heroku config:get CLEARDB_DATABASE_URL
   ```

3. Update your PHP database connection to use the Heroku database URL

## Environment Variables
Set any needed environment variables:
```bash
heroku config:set VARIABLE_NAME=value
```