# Installation & Setup

## Using DevRead.me (No Installation Required)

DevRead.me is a **web-based application**, so there's nothing to install! Simply visit [DevRead.me](https://devread.me) and start generating documentation.

### Browser Requirements

- Modern web browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled
- Internet connection

## Deploying Generated Documentation Locally

Once you've generated and downloaded your documentation, you can view it locally before deploying.

### On Windows

1. **Extract the ZIP file**

   ```
   Right-click the ZIP → Extract All
   ```

2. **Open Documentation**
   - Double-click `index.html` to view in your browser

3. **Alternative: Use Local Server**
   - Install [Python](https://www.python.org/)
   - Navigate to the extracted folder in Command Prompt
   - Run: `python -m http.server 8000`
   - Visit: `http://localhost:8000`

### On macOS/Linux

1. **Extract the ZIP file**

   ```bash
   unzip documentation.zip
   cd documentation
   ```

2. **Serve Locally**

   ```bash
   python3 -m http.server 8000
   ```

   Or with Node.js:

   ```bash
   npx http-server
   ```

3. **View in Browser**
   - Visit: `http://localhost:8000`

## Setting Up for GitHub Pages

### Step 1: Create a Repository

```bash
# Create new repository on GitHub
# Clone it locally
git clone https://github.com/yourusername/your-docs.git
cd your-docs
```

### Step 2: Add Documentation Files

```bash
# Copy your generated documentation files
cp -r /path/to/downloaded/docs/* .
```

### Step 3: Configure GitHub Pages

1. Push to GitHub:

   ```bash
   git add .
   git commit -m "Add documentation"
   git push origin main
   ```

2. In GitHub repository settings:
   - Go to **Settings** → **Pages**
   - Source: Select branch and folder
   - Save

Your documentation will be live at: `https://yourusername.github.io/your-docs`

## Setting Up for Vercel

### Step 1: Prepare Repository

```bash
# Your documentation must be in a GitHub repository
# Create a `docs` folder or root with documentation files
```

### Step 2: Connect to Vercel

1. Visit [vercel.com](https://vercel.com)
2. Sign in with GitHub
3. Click "New Project"
4. Select your documentation repository
5. Configure:
   - Framework: Static
   - Build Command: (leave empty)
   - Output Directory: (leave empty or specify `docs`)
6. Click "Deploy"

Vercel will automatically deploy and provide you with a live URL.

## Setting Up for Netlify

### Step 1: Prepare Files

Extract your documentation ZIP file locally.

### Step 2: Deploy via Drag & Drop

1. Visit [netlify.com](https://netlify.com)
2. Sign in or create account
3. Drag and drop your documentation folder
4. Netlify processes and deploys instantly

### Step 2 Alternative: Connect GitHub

1. Create a GitHub repository with your documentation
2. In Netlify: Click "New site from Git"
3. Select GitHub and your repository
4. Configure build settings (usually not needed for static sites)
5. Deploy

Your documentation will have a live URL like: `https://your-site.netlify.app`

## Setting Up Custom Domain

After deployment, you can add a custom domain:

### GitHub Pages

- Settings → Pages → Custom domain
- Add DNS records to your domain registrar

### Vercel

- Project Settings → Domains
- Enter your domain and follow DNS setup

### Netlify

- Site Settings → Domain management
- Add custom domain and configure DNS

## Post-Deployment

### Verify Your Site

1. Visit your deployed documentation URL
2. Check:
   - All pages load correctly
   - Navigation works
   - Sidebar functions (if enabled)
   - Links are not broken

### Maintenance

- If you need to update documentation, regenerate with DevRead.me
- Download the new files
- Replace old files in your repository
- Commit and push changes (auto-deploys)

## Troubleshooting Installation

### Documentation shows blank page

- Check browser console for errors (F12)
- Ensure all files extracted completely
- Clear browser cache (Ctrl+Shift+Delete)

### Images not loading

- Verify image paths in generated files
- Check that images folder exists
- Ensure proper folder structure

### Sidebar not appearing

- Verify sidebar toggle was enabled during generation
- Check `_sidebar.md` file exists
- Clear browser cache

### Custom domain not working

- Wait 24-48 hours for DNS propagation
- Verify DNS records with registrar
- Check CNAME or A record settings

## Need Help?

- Check [Troubleshooting Guide](../resources/troubleshooting.md)
- Review [FAQ](../resources/faq.md)
- [Contact Support](../resources/contact.md)

---

Your documentation is now ready to serve! 🚀
