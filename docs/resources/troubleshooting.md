# Troubleshooting Guide

Having issues? This guide covers common problems and solutions.

## Generation Issues

### Generation Takes Too Long (>60 seconds)

**Symptoms:**

- Generation stuck at loading screen
- Timeout errors
- Very slow progress

**Solutions:**

1. **Check your connection**
   - Test internet speed
   - Restart router/connection
   - Try different network

2. **Reduce input size**
   - Use shorter, more focused content
   - Remove unnecessary details
   - Try again with core information

3. **Try again later**
   - Server might be under load
   - Wait 5-10 minutes
   - Retry the generation

4. **Clear browser cache**
   - Press Ctrl+Shift+Delete (Windows)
   - Or Cmd+Shift+Delete (Mac)
   - Clear all browser data
   - Refresh page

5. **Try different browser**
   - Chrome, Firefox, Safari, Edge
   - Browser-specific issues can occur

### Generation Fails / No Error Message

**Symptoms:**

- Page shows "Error" but no message
- Generation starts then stops
- No response after clicking "Generate"

**Solutions:**

1. **Refresh the page**
   - F5 or Ctrl+R
   - Hard refresh: Ctrl+Shift+R
   - Close and reopen DevRead.me

2. **Check browser console**
   - Press F12 to open developer tools
   - Go to Console tab
   - Look for error messages
   - Note any errors for support

3. **Disable browser extensions**
   - Temporarily disable all extensions
   - Try generation again
   - Extensions can interfere with API calls

4. **Try incognito/private mode**
   - Open incognito window
   - Try generation in incognito
   - This bypasses cache issues

5. **Try different browser**
   - Use Chrome, Firefox, Safari, or Edge
   - Some browsers have compatibility issues

6. **Contact support**
   - If persists, [contact us](contact.md)
   - Include any console error messages

### "Content is too short" Error

**Symptoms:**

- Error: "Content must be at least 50 characters"
- Can't generate with short input

**Solution:**

- Provide more detailed content
- Include:
  - Project description
  - Features list
  - Installation steps
  - Usage examples
  - API information

**Minimum requirements:**

- At least 50 characters
- Clear, descriptive content
- Proper formatting helps

### Input Validation Errors

**Symptoms:**

- "Invalid input" error
- "Malformed content" message
- Generation rejected

**Solutions:**

1. **Check for special characters**
   - Avoid unusual Unicode characters
   - Use standard ASCII where possible
   - Copy-paste carefully

2. **Check for HTML/code**
   - Include code snippets properly
   - Don't paste entire files
   - Use clear structure

3. **Verify encoding**
   - Ensure UTF-8 encoding
   - Avoid binary data
   - Use plain text

4. **Simplify content**
   - Remove formatting if possible
   - Use plain markdown
   - Keep it simple

## Download & File Issues

### ZIP File Won't Download

**Symptoms:**

- Download button not responding
- Timeout during download
- File corrupted after download

**Solutions:**

1. **Try again**
   - Click download button again
   - Wait for file to save

2. **Check browser settings**
   - Allow downloads from website
   - Check download folder
   - Disable download restrictions

3. **Try different browser**
   - Use Chrome, Firefox, Safari
   - Each has different download handling

4. **Wait and retry**
   - Server might be busy
   - Try in 5 minutes
   - Less network congestion later

5. **Check disk space**
   - Ensure enough space for download
   - ~100KB ZIP file typical
   - Check disk space: Device settings

### ZIP File Corrupted

**Symptoms:**

- Can't extract ZIP file
- "Archive is damaged" error
- Files won't open after extraction

**Solutions:**

1. **Download again**
   - Try generation once more
   - Download fresh ZIP file
   - Use different browser if needed

2. **Use different extraction tool**
   - Windows: 7-Zip, WinRAR
   - Mac: Built-in or BetterZip
   - Linux: Command line (unzip)

3. **Check download wasn't interrupted**
   - Ensure full download completed
   - Check file size (50-150 KB typical)
   - Don't open while downloading

4. **Try alternative download method**
   - Save as instead of direct open
   - Right-click → Save As
   - Then extract from saved file

### Missing Files in ZIP

**Symptoms:**

- Only some files in extracted folder
- Expected files missing
- Incomplete documentation

**Solutions:**

1. **Extract all files**
   - Don't extract selectively
   - Extract entire ZIP at once
   - Check extraction completed

2. **Download again**
   - Re-generate documentation
   - Download fresh ZIP
   - Extract all files

3. **Check extraction folder**
   - Open the extraction folder
   - Files might be nested in subfolder
   - Look for "docs" or "documentation" folder

4. **Verify ZIP integrity**
   - Try extracting again
   - Use different extraction tool
   - Check file properties

## Deployment Issues

### Site Shows 404 Error

**Symptoms:**

- After deployment, page shows "404 Not Found"
- Can't access deployed documentation
- Links broken

**Solutions:**

1. **Verify files uploaded**
   - Check all files uploaded to server
   - Use FTP to verify
   - Check file permissions

2. **Check root path configuration**
   - Verify correct folder for hosting
   - Check deployment settings
   - Verify index.html in root

3. **Clear browser cache**
   - Ctrl+Shift+Delete
   - Clear all cache
   - Refresh page (Ctrl+R)

4. **Wait for deployment**
   - Vercel/Netlify take 1-2 minutes
   - GitHub Pages takes 5-10 minutes
   - Wait before troubleshooting

5. **Check URL**
   - Verify correct URL
   - Check for typos in domain
   - Try www or without www

### Styling Not Applied / CSS Not Working

**Symptoms:**

- Page loads but no styling
- Colors not applied
- Layout broken
- Content looks plain

**Solutions:**

1. **Clear browser cache**
   - Ctrl+Shift+Delete
   - Clear cache completely
   - Hard refresh: Ctrl+Shift+R

2. **Check CSS files uploaded**
   - Verify `custom.css` exists
   - Check file uploaded to server
   - Verify permissions (644)

3. **Check CSS path in HTML**
   - Open index.html
   - Verify CSS link path is correct
   - Check for typos in paths

4. **Verify file structure**
   - CSS files in correct folder
   - Paths relative to HTML
   - No missing directories

5. **Check browser console**
   - F12 → Console tab
   - Look for 404 errors
   - Check network tab for failed loads

6. **Try direct URL**
   - Access custom.css directly
   - `yourdomain.com/custom.css`
   - Should show CSS content

### Images Not Loading

**Symptoms:**

- Broken image icons
- "Image not found" errors
- Only text, no images

**Solutions:**

1. **Verify image files uploaded**
   - Check `img` or `assets` folder
   - Ensure all images present
   - Verify file names match

2. **Check image paths**
   - Open generated markdown files
   - Verify image paths are relative
   - Check for typos

3. **Set file permissions**
   - Images need 644 permissions
   - Use FTP to set permissions
   - Or command: `chmod 644 *.jpg`

4. **Check image references**
   - Image syntax: `![alt](path/image.jpg)`
   - Verify syntax correct
   - Check path exists

5. **Try without subfolders**
   - Move images to same folder
   - Update paths in markdown
   - Test if images load

### Sidebar Not Appearing

**Symptoms:**

- Navigation sidebar missing
- Can't navigate pages
- Only seeing one page

**Solutions:**

1. **Verify sidebar enabled**
   - Was "Include Sidebar" checked?
   - If not, regenerate with it enabled
   - Redeploy new version

2. **Check \_sidebar.md exists**
   - File must be in root folder
   - Verify file name exactly: `_sidebar.md`
   - Check file has content

3. **Verify Docsify config**
   - Open index.html
   - Check for sidebar configuration
   - Verify sidebar plugin loaded

4. **Check file permissions**
   - Ensure files are readable
   - Check folder permissions
   - Verify 755 for folders, 644 for files

5. **Clear cache and refresh**
   - Ctrl+Shift+Delete cache
   - Hard refresh: Ctrl+Shift+R
   - Wait 30 seconds

6. **Check browser console**
   - F12 → Console
   - Look for JavaScript errors
   - Check for failed script loads

## Local Testing Issues

### File Opening in Editor Instead of Browser

**Symptoms:**

- Clicking index.html opens in text editor
- Want to open in browser instead

**Solutions:**

1. **Windows - Right-click method**
   - Right-click index.html
   - Select "Open with"
   - Choose your browser
   - Check "Always use this app"

2. **Windows - Drag to browser**
   - Drag index.html
   - Drop on browser icon/window
   - Document opens in browser

3. **Windows - Command line**

   ```cmd
   start index.html
   ```

4. **Mac - Command line**

   ```bash
   open index.html
   ```

5. **Linux - Command line**
   ```bash
   xdg-open index.html
   ```

### Can't Start Local Server

**Symptoms:**

- Command doesn't work
- "Command not found" error
- Port already in use error

**Solutions:**

1. **Install Python (Windows/Mac/Linux)**

   ```bash
   python -m http.server 8000
   # or
   python3 -m http.server 8000
   ```

2. **Use Node.js alternative**

   ```bash
   npx http-server
   # or
   npx serve
   ```

3. **Use PHP (if installed)**

   ```bash
   php -S localhost:8000
   ```

4. **Port already in use**

   ```bash
   # Try different port
   python -m http.server 8001
   # Then visit http://localhost:8001
   ```

5. **Permission denied**
   ```bash
   # May need sudo on Linux/Mac
   sudo python -m http.server 80
   ```

### Links Lead to 404 in Local Server

**Symptoms:**

- Internal links broken
- Navigation doesn't work
- "404 Not Found" on links

**Solutions:**

1. **Use local server (not file://)**
   - Always use `http://localhost:PORT`
   - Not `file://path/to/docs`
   - File:// protocol breaks relative links

2. **Set correct port in config**
   - Verify links use relative paths
   - Check `_sidebar.md` link format
   - Should be like: `[Link](page.md)`

3. **Check file names**
   - Verify markdown files exist
   - Check spelling exactly
   - Files are case-sensitive on Linux/Mac

4. **Restart local server**
   - Stop: Ctrl+C
   - Restart: `python -m http.server 8000`
   - Try links again

## Browser Compatibility

### Page Looks Different in Different Browsers

**Symptoms:**

- Works in Chrome but not Firefox
- Different appearance in different browsers
- Styling works in one browser only

**Solutions:**

1. **Use modern browser**
   - Chrome 90+
   - Firefox 88+
   - Safari 14+
   - Edge 90+

2. **Update your browser**
   - Check for updates
   - Install latest version
   - Restart browser

3. **Disable browser extensions**
   - Extensions can break styling
   - Temporarily disable all
   - Try again
   - Re-enable one by one to find culprit

4. **Clear browser cache**
   - Ctrl+Shift+Delete
   - Clear all cache
   - Hard refresh: Ctrl+Shift+R

5. **Try incognito/private mode**
   - Open incognito window
   - Test documentation
   - See if issue persists

## Still Having Issues?

### Check These Resources

1. **[FAQ](faq.md)** - Common questions answered
2. **[Documentation](../)** - Full guides and tutorials
3. **[Contact Support](contact.md)** - Get help from us

### Getting Support

- 📧 Email: [hi@jumpstone4477.de](mailto:hi@jumpstone4477.de)
- 💬 Discord: [Join Server](https://discord.gg/yKU4Q2mHj8)
- 🐛 GitHub: [Report Issues](https://github.com/devread-me)

### When Contacting Support

Include:

- What you were trying to do
- Exact error message (if any)
- Screenshots if helpful
- Browser and OS version
- Steps to reproduce issue

This helps us help you faster!

---

**Most common issues resolved?** Great! Ready to deploy? Check [Deployment Guide](../documentation/deployment.md)
