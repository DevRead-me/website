# Configuration Guide

Learn how to configure DevRead.me for your specific needs.

## Application Configuration

### Environment Variables

DevRead.me requires certain environment variables for proper operation.

#### Required Variables

**GROQ_API_KEY**

- **Purpose**: Authentication with Groq Cloud API
- **Type**: String
- **Example**: `GROQ_API_KEY=gsk_1234567890abcdef`
- **Where to get**: [Groq Console](https://console.groq.com)

#### Optional Variables

**NEXT_PUBLIC_APP_URL**

- **Purpose**: Application base URL
- **Type**: String
- **Default**: `http://localhost:3000`
- **Example**: `NEXT_PUBLIC_APP_URL=https://devread.me`

**NODE_ENV**

- **Purpose**: Environment mode
- **Type**: String
- **Options**: `development`, `production`
- **Default**: `development`

### Setting Up Environment

#### Local Development

1. **Create .env.local file:**

   ```bash
   cp .env.example .env.local
   ```

2. **Add your Groq API Key:**

   ```
   GROQ_API_KEY=your_api_key_here
   NEXT_PUBLIC_APP_URL=http://localhost:3000
   ```

3. **Save and restart development server:**
   ```bash
   npm run dev
   ```

#### Production Deployment

1. **Add environment variables to platform:**
   - Vercel: Settings → Environment Variables
   - Netlify: Site Settings → Build & Deploy
   - Docker: ENV in Dockerfile
   - Manual: System environment variables

2. **Set NEXT_PUBLIC_APP_URL to production domain:**

   ```
   NEXT_PUBLIC_APP_URL=https://yourdomain.com
   ```

3. **Ensure NODE_ENV is set to production**

## Generation Configuration

### Default Settings

When you use DevRead.me, these are the default settings:

```json
{
  "color": "#10b981",
  "includeSidebar": true,
  "designVersion": "v2",
  "outputFormat": "full",
  "temperature": 0.7,
  "maxTokens": 2048
}
```

### Configuration Options

#### Color Configuration

```javascript
const colorOptions = {
  primary: "#10b981", // Main accent color
  secondary: "#a855f7", // Secondary accent
  background: "#050505", // Dark background
  surface: "#0f0f0f", // Card background
};
```

**How to customize:**

1. Use color picker on main page
2. Select hex color code
3. Preview applied
4. Generate with custom color

#### Design Configuration

```javascript
const designOptions = {
  version: "v2", // "v1" or "v2"
  includeSidebar: true, // true or false
  theme: "dark", // "dark" or "light"
  responsive: true, // Always true for mobile
};
```

#### Output Configuration

```javascript
const outputOptions = {
  format: "full", // "full" or "readme"
  includeAssets: true, // Include images/files
  compression: "zip", // Compression format
  validateLinks: true, // Verify internal links
};
```

#### AI Configuration

```javascript
const aiConfig = {
  model: "llama-3.3-70b-versatile",
  temperature: 0.7, // 0.0 (deterministic) to 1.0 (creative)
  maxTokens: 2048, // Maximum response length
  topP: 0.9, // Nucleus sampling
  stream: true, // Real-time response
};
```

**Parameter Explanation:**

| Parameter   | Range    | Effect                                       |
| ----------- | -------- | -------------------------------------------- |
| temperature | 0.0-1.0  | Lower = more focused, Higher = more creative |
| maxTokens   | 100-4096 | Maximum output length                        |
| topP        | 0.0-1.0  | Diversity control (higher = more variety)    |

## Template Configuration

### Customizing HTML Template

Edit the HTML template in your generated `index.html`:

```html
<head>
  <title>Your Documentation</title>
  <meta name="description" content="Your documentation description" />
  <!-- Customize meta tags here -->
</head>
```

### Customizing CSS

Edit generated `custom.css`:

```css
:root {
  --primary-color: #10b981;
  --secondary-color: #a855f7;
  --background: #050505;
  --surface: #0f0f0f;
  --text-primary: #e4e4e7;
  --text-secondary: #a1a1aa;
}

/* Override other styles here */
body {
  font-family: "Your Font", sans-serif;
}
```

### Customizing Sidebar

Edit `_sidebar.md`:

```markdown
- [Home](/)
- **Section 1**
  - [Page 1](section1/page1.md)
  - [Page 2](section1/page2.md)
- **Section 2**
  - [Page 1](section2/page1.md)
```

## Server Configuration

### Hosting Configuration

#### GitHub Pages

1. **Enable in repository settings:**
   - Settings → Pages
   - Source: Deploy from branch
   - Branch: gh-pages
   - Folder: / (root)

2. **Optional: Custom domain**
   - Add CNAME record
   - Update DNS settings

#### Vercel

1. **Connect repository:**
   - New Project → Import Git Repository
   - Select repository

2. **Configure:**
   - Framework: Other (or Next.js if applicable)
   - Build Command: `npm run build`
   - Output Directory: `out`

3. **Verify environment:**
   - Settings → Environment Variables
   - Add GROQ_API_KEY

#### Netlify

1. **Connect repository:**
   - New site from Git
   - Select repository
   - Configure build:
     - Build command: `npm run build`
     - Publish directory: `dist`

2. **Configure environment:**
   - Site settings → Build & deploy → Environment
   - Add GROQ_API_KEY

### Docker Configuration

If running in Docker:

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

ENV GROQ_API_KEY=${GROQ_API_KEY}
ENV NEXT_PUBLIC_APP_URL=${NEXT_PUBLIC_APP_URL}

RUN npm run build

EXPOSE 3000

CMD ["npm", "run", "start"]
```

**Docker run command:**

```bash
docker run -e GROQ_API_KEY=your_key -p 3000:3000 devreadme
```

## Rate Limiting Configuration

DevRead.me includes rate limiting to prevent abuse.

### Current Limits

- **10 requests/hour** per IP
- **100 requests/day** per IP

### Modifying Limits

In production deployment, adjust via environment:

```env
RATE_LIMIT_REQUESTS_PER_HOUR=10
RATE_LIMIT_REQUESTS_PER_DAY=100
```

### Disabling Rate Limiting (Not Recommended)

For development only:

```env
DISABLE_RATE_LIMITING=true
```

## Performance Configuration

### Optimization Settings

```javascript
// Next.js configuration for performance
const nextConfig = {
  compress: true,
  poweredByHeader: false,
  productionBrowserSourceMaps: false,
  images: {
    unoptimized: true,
  },
};
```

### Caching Strategy

```javascript
// Cache generated files
const cacheHeaders = {
  "Cache-Control": "public, max-age=3600",
};
```

## Security Configuration

### CORS Settings

```javascript
const corsOptions = {
  origin: ["https://devread.me", "https://www.devread.me"],
  credentials: true,
};
```

### Content Security Policy

```html
<meta
  http-equiv="Content-Security-Policy"
  content="default-src 'self'; script-src 'self' 'unsafe-inline'"
/>
```

### HTTPS Enforcement

Ensure all deployments use HTTPS:

```javascript
// Force HTTPS in production
if (process.env.NODE_ENV === "production") {
  // Redirect HTTP to HTTPS
}
```

## Monitoring & Logging

### Enable Logging

```javascript
// In API routes
console.log("Generation started", {
  timestamp: new Date(),
  contentLength: content.length,
  options: options,
});
```

### Error Tracking

```javascript
// Log errors for debugging
console.error("Generation failed", {
  error: error.message,
  code: error.code,
  timestamp: new Date(),
});
```

### Performance Monitoring

```javascript
const startTime = Date.now();
// ... generation process ...
const duration = Date.now() - startTime;
console.log(`Generation completed in ${duration}ms`);
```

## Configuration Checklist

Before production deployment:

- [ ] GROQ_API_KEY set in environment
- [ ] NEXT_PUBLIC_APP_URL configured correctly
- [ ] HTTPS enabled
- [ ] Rate limiting configured
- [ ] Error logging enabled
- [ ] Performance optimized
- [ ] Security headers set
- [ ] CORS configured
- [ ] Backups configured
- [ ] Monitoring enabled

## Troubleshooting Configuration

### API Key Not Recognized

- Verify GROQ_API_KEY is correct
- Check environment variables loaded
- Restart application after changes

### Slow Generation

- Check network latency to Groq API
- Verify API quota not exceeded
- Check server resources

### Template Not Applying

- Clear browser cache
- Verify CSS files included
- Check for conflicting styles

### Sidebar Not Appearing

- Verify `_sidebar.md` exists
- Check includeSidebar option
- Ensure markdown syntax correct

---

For more help, see [Troubleshooting Guide](troubleshooting.md) or [Contact Support](../resources/contact.md)
