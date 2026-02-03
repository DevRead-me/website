# Deployment Guide

Complete guide to deploying your DevRead.me-generated documentation.

## Pre-Deployment Checklist

Before deploying, verify:

- [ ] Downloaded the ZIP package
- [ ] Extracted all files successfully
- [ ] Tested locally (open index.html)
- [ ] All links working correctly
- [ ] Images loading properly
- [ ] Sidebar functioning (if enabled)
- [ ] Color theme applied correctly

## Local Testing

### Windows

**Method 1: Direct File Opening**

1. Extract ZIP file
2. Right-click `index.html`
3. Select "Open with" → Your browser
4. Documentation opens locally

**Method 2: Local Server (Recommended)**

```bash
# Install Python (if not already installed)
# Download from python.org

# Navigate to extracted folder
cd path\to\docs

# Start server
python -m http.server 8000

# Open http://localhost:8000
```

### macOS/Linux

**Using Python:**

```bash
cd /path/to/docs
python3 -m http.server 8000
# Open http://localhost:8000
```

**Using Node.js:**

```bash
cd /path/to/docs
npx http-server
# Open http://localhost:8080
```

**Using PHP:**

```bash
cd /path/to/docs
php -S localhost:8000
# Open http://localhost:8000
```

### Verification Steps

1. **Home Page**
   - [ ] Loads correctly
   - [ ] Title displays
   - [ ] Navigation visible

2. **Navigation**
   - [ ] Sidebar works (if enabled)
   - [ ] Links navigate correctly
   - [ ] Back button functions

3. **Content**
   - [ ] Text displays properly
   - [ ] Code blocks formatted
   - [ ] Lists and headings correct

4. **Assets**
   - [ ] Images load
   - [ ] Styles applied
   - [ ] Colors correct
   - [ ] Fonts display

5. **Responsiveness**
   - [ ] Resize browser window
   - [ ] Check mobile view (F12)
   - [ ] Navigation adapts
   - [ ] Content readable

## GitHub Pages Deployment

### Option 1: Using Your Repository

**Step 1: Create Repository**

```bash
# Create new repo on GitHub
# Clone locally
git clone https://github.com/yourusername/repo-name.git
cd repo-name
```

**Step 2: Add Documentation**

```bash
# Option A: Documentation in root
# Extract ZIP files to root directory
# Copy index.html, README.md, etc. to root

# Option B: Documentation in /docs folder
mkdir docs
# Extract ZIP files to docs folder
```

**Step 3: Push to GitHub**

```bash
git add .
git commit -m "Add documentation"
git push origin main
```

**Step 4: Enable GitHub Pages**

1. Go to repository Settings
2. Find "Pages" section
3. Source: Select "Deploy from branch"
4. Branch: Select `main` (or `gh-pages` if using that)
5. Folder: Select `/docs` (if docs in subfolder) or `/` (root)
6. Save

**Result:**

- Your site will be available at: `https://yourusername.github.io/repo-name`

### Option 2: Using gh-pages Branch

**Step 1: Create gh-pages Branch**

```bash
git checkout --orphan gh-pages
```

**Step 2: Add Documentation Files**

```bash
# Clear old files (keep .git)
git rm -r --cached .

# Extract documentation files
# Or copy from docs folder:
cp -r ../docs-extract/* .
```

**Step 3: Commit and Push**

```bash
git add .
git commit -m "Initial documentation"
git push origin gh-pages
```

**Step 4: Configure in Settings**

- Settings → Pages
- Source: Deploy from branch
- Branch: `gh-pages`
- Folder: `/` (root)

## Vercel Deployment

### Prerequisites

- GitHub account with your repository
- Vercel account (free tier available)

### Deployment Steps

**Step 1: Create GitHub Repository**

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/yourusername/docs.git
git push -u origin main
```

**Step 2: Import to Vercel**

1. Visit [vercel.com](https://vercel.com)
2. Click "New Project"
3. Select "Import Git Repository"
4. Enter your GitHub repository URL
5. Click "Import"

**Step 3: Configure Project**

1. **Project Name**: Enter desired name
2. **Framework**: Select "Other"
3. **Build Command**: Leave empty (for static content)
4. **Output Directory**: Leave empty
5. **Environment Variables**: Add any needed (usually none)
6. Click "Deploy"

**Step 4: Wait for Deployment**

- Vercel builds and deploys automatically
- You'll receive a deployment URL
- Can take 1-2 minutes

**Result:**

- Your documentation is live!
- URL: `https://your-project.vercel.app`

### Custom Domain (Optional)

1. In Vercel Project Settings
2. Go to "Domains"
3. Add custom domain
4. Follow DNS configuration instructions
5. Wait for verification (24-48 hours)

## Netlify Deployment

### Option 1: Drag & Drop

**Simplest Method:**

1. Visit [netlify.com](https://netlify.com)
2. Sign in or create free account
3. Extract your documentation ZIP
4. Drag and drop the folder into Netlify
5. Netlify automatically deploys

**Result:**

- Live URL provided immediately
- URL: `https://random-name.netlify.app`

### Option 2: GitHub Integration

**Step 1: Push to GitHub**

```bash
git push origin main
```

**Step 2: Connect to Netlify**

1. Visit [netlify.com](https://netlify.com)
2. Click "New site from Git"
3. Select GitHub
4. Authorize Netlify
5. Select your repository

**Step 3: Configure**

1. **Build command**: Leave empty
2. **Publish directory**: `docs` (if in subfolder) or `.` (root)
3. Click "Deploy"

**Step 4: Automatic Deployments**

- Future pushes automatically deploy
- No manual steps needed

### Custom Domain

1. In Netlify site settings
2. Go to "Domain management"
3. Add custom domain
4. Configure DNS
5. Domain active within 48 hours

## Self-Hosted Deployment

### Using cPanel/Shared Hosting

1. **Extract ZIP locally**
2. **Connect via FTP/SFTP**
   - Use FTP client (FileZilla, WinSCP)
   - Connect to your hosting server
3. **Upload files**
   - Create `/public_html/docs` folder
   - Upload all documentation files
4. **Verify**
   - Visit `yourdomain.com/docs`
   - Test all pages and links

### Using VPS/Dedicated Server

**With Nginx:**

```nginx
server {
    listen 80;
    server_name docs.yourdomain.com;

    root /var/www/docs;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

**With Apache:**

```apache
<VirtualHost *:80>
    ServerName docs.yourdomain.com
    DocumentRoot /var/www/docs

    <Directory /var/www/docs>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

### Deployment Steps

1. **SSH into server**

   ```bash
   ssh user@your-server.com
   ```

2. **Create docs directory**

   ```bash
   mkdir -p /var/www/docs
   ```

3. **Upload files**

   ```bash
   scp -r docs/* user@your-server.com:/var/www/docs/
   ```

4. **Set permissions**

   ```bash
   chmod -R 755 /var/www/docs
   chown -R www-data:www-data /var/www/docs
   ```

5. **Restart web server**
   ```bash
   sudo systemctl restart nginx
   # or
   sudo systemctl restart apache2
   ```

## Docker Deployment

### Using Docker Compose

**docker-compose.yml:**

```yaml
version: "3.8"

services:
  docs:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./docs:/usr/share/nginx/html:ro
    container_name: devreadme-docs
```

**Deploy:**

```bash
docker-compose up -d
```

### Using Kubernetes

**kubernetes.yml:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: devreadme-docs
spec:
  replicas: 2
  selector:
    matchLabels:
      app: devreadme-docs
  template:
    metadata:
      labels:
        app: devreadme-docs
    spec:
      containers:
        - name: nginx
          image: nginx:alpine
          ports:
            - containerPort: 80
          volumeMounts:
            - name: docs
              mountPath: /usr/share/nginx/html
      volumes:
        - name: docs
          hostPath:
            path: /var/www/docs
```

## SSL/HTTPS Configuration

### GitHub Pages

- Automatic HTTPS with `github.io` domain
- Enable HTTPS enforcement in settings

### Vercel

- Automatic HTTPS included
- Free SSL certificate

### Netlify

- Automatic HTTPS included
- Free SSL from Let's Encrypt

### Self-Hosted

**Using Let's Encrypt:**

```bash
# Install Certbot
sudo apt install certbot python3-certbot-nginx

# Generate certificate
sudo certbot certonly --nginx -d yourdomain.com

# Auto-renew
sudo systemctl enable certbot.timer
```

**Update Nginx:**

```nginx
server {
    listen 443 ssl http2;
    server_name yourdomain.com;

    ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;

    root /var/www/docs;
    index index.html;
}

# Redirect HTTP to HTTPS
server {
    listen 80;
    server_name yourdomain.com;
    return 301 https://$server_name$request_uri;
}
```

## Performance Optimization

### Enable Caching

**Browser caching headers:**

```nginx
expires 30d;
add_header Cache-Control "public, immutable";
```

### Compression

**Gzip compression:**

```nginx
gzip on;
gzip_types text/html text/css text/javascript;
gzip_min_length 1024;
```

### CDN Setup

Consider using CDN for:

- Faster global delivery
- Automatic caching
- DDoS protection

**Providers:**

- Cloudflare (free tier available)
- Bunny CDN
- AWS CloudFront

## Post-Deployment

### Verification

- [ ] Site loads successfully
- [ ] All pages accessible
- [ ] Navigation working
- [ ] Images loading
- [ ] Styles applied
- [ ] Mobile responsive
- [ ] Links functional

### Monitoring

- Check analytics
- Monitor performance
- Track page load times
- Monitor uptime

### Updates

To update documentation:

1. Generate new version with DevRead.me
2. Download updated files
3. Replace old files
4. Commit and push (auto-deploys)

## Troubleshooting Deployment

### Site shows 404 error

- Verify files uploaded correctly
- Check root path configuration
- Ensure index.html in correct folder

### Styling not applied

- Clear browser cache (Ctrl+Shift+Delete)
- Check CSS file paths
- Verify files uploaded completely

### Images not loading

- Check image paths relative to HTML
- Ensure image files uploaded
- Verify file permissions (755)

### Sidebar not working

- Verify Docsify configured correctly
- Check \_sidebar.md exists
- Clear browser cache

### Slow loading

- Enable compression
- Check file sizes
- Use CDN for assets
- Optimize images

---

**Need more help?** Check [Troubleshooting](troubleshooting.md) or [Contact Support](../resources/contact.md)
