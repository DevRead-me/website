# Customization Options

DevRead.me provides extensive customization options to make your documentation truly yours.

## Theme Customization

### Color Picker

Choose your brand color with the intuitive color picker:

- **Primary Accent Color**: Controls all primary interactive elements
- **Live Preview**: See changes in real-time
- **Professional Palettes**: Pre-selected color schemes
- **Custom Colors**: Unlimited custom color selection

#### Using the Color Picker

1. Click the color picker icon
2. Select your desired color
3. See preview of how it affects the theme
4. Apply and generate documentation

#### Color Application

Your selected color affects:

- Links and buttons
- Section headings
- Highlights and emphasis
- Navigation elements
- Sidebar accents

### Theme Examples

**Green Theme** (Default)

- Professional and modern
- Excellent readability
- Popular for tech projects

**Purple Theme**

- Creative and unique
- Great for design projects
- Distinctive branding

**Blue Theme**

- Trustworthy and stable
- Perfect for enterprise
- High contrast

**Orange Theme**

- Energetic and inviting
- Great for startups
- Warm appearance

## Navigation Customization

### Sidebar Toggle

Control whether your documentation includes a sidebar:

**Sidebar Enabled:**

- Automatic navigation menu
- Table of contents
- Easy page browsing
- Mobile-responsive

**Sidebar Disabled:**

- Cleaner, minimal look
- More content space
- Focus on content
- Suitable for simple docs

#### When to Use Each

**Enable Sidebar When:**

- Large documentation sets
- Multiple pages and sections
- Complex project structure
- Need easy navigation

**Disable Sidebar When:**

- Single page documentation
- Simple projects
- Maximizing content space
- Minimal navigation needed

### Navigation Features

When sidebar is enabled:

- **Auto-Generated TOC**: Sidebar automatically created
- **Page Hierarchy**: Proper section organization
- **Breadcrumb Navigation**: Shows current location
- **Mobile Menu**: Hamburger menu for small screens
- **Search Box**: Quick content search

## Design Variations

### V1 Design

**Clean and Minimal**

- Lightweight aesthetic
- Focus on content
- Simple, elegant layout
- Fast rendering

**Best for:**

- Technical documentation
- Minimal design preference
- Simple projects
- Maximum readability

### V2 Design

**Modern and Enhanced**

- Contemporary styling
- Rich visual elements
- Enhanced typography
- Professional appearance

**Best for:**

- Modern projects
- Enhanced branding
- Larger documentation
- Visual-first audience

## Output Format Customization

### Full Documentation Site

Complete, multi-file Docsify package:

**Includes:**

- HTML configuration (index.html)
- Multiple markdown files
- CSS styling
- Navigation structure
- Search functionality
- All assets and images

**File Structure:**

```
docs/
├── index.html
├── README.md
├── _sidebar.md
├── SETUP.md
├── API.md
├── FEATURES.md
├── TROUBLESHOOTING.md
└── css/
    └── custom.css
```

**Best for:**

- Comprehensive documentation
- Large projects
- Complex information
- Professional presentation

### Single README Mode

Enhanced README.md only:

**Includes:**

- Professional README.md
- Optimized formatting
- Full content in single file
- GitHub-ready

**File Structure:**

```
README.md
```

**Best for:**

- Simple projects
- GitHub repositories
- Quick documentation
- Minimal setup

## Responsive Design

All customization options produce fully responsive documentation:

### Desktop

- Full-width content
- Sidebar visible
- Optimal spacing
- Large typography

### Tablet

- Adjusted layout
- Sidebar toggle
- Touch-friendly buttons
- Readable font sizes

### Mobile

- Single column layout
- Hamburger menu
- Touch optimization
- Fast loading

## Content Customization Post-Generation

After generation, you can easily customize:

### Edit Colors

Edit `custom.css` to change colors:

```css
:root {
  --primary-color: #10b981; /* Change this */
  --secondary-color: #a855f7; /* And this */
}
```

### Modify Sidebar

Edit `_sidebar.md` to customize navigation:

```markdown
- [Home](/)
- [Features](features.md)
- [API](api.md)
```

### Update Content

Edit individual `.md` files to update content:

```markdown
# Updated Section Title

Updated content goes here...
```

### Customize Styles

Modify CSS files to adjust appearance:

```css
.main-content {
  max-width: 1200px; /* Change width */
  font-size: 16px; /* Change font size */
}
```

## Pre-Generation vs Post-Generation

### Pre-Generation Customization (Recommended)

Using DevRead.me interface:

- Quick and easy
- Visual preview
- No technical knowledge needed
- Saves editing time

**Options:**

- Color selection
- Sidebar toggle
- Design version
- Output format

### Post-Generation Customization (Advanced)

Manual editing of generated files:

- Complete control
- Advanced styling
- Content modifications
- Custom features

**Options:**

- Edit HTML/CSS
- Modify markdown content
- Add custom scripts
- Extend functionality

## Best Practices

### Color Selection

1. ✅ Choose colors that match your brand
2. ✅ Ensure good contrast for readability
3. ✅ Test on different backgrounds
4. ✅ Consider colorblind accessibility

### Navigation Design

1. ✅ Use sidebar for large documentation
2. ✅ Keep navigation logical and clear
3. ✅ Use descriptive section names
4. ✅ Maintain consistent structure

### Design Consistency

1. ✅ Choose one design version (V1 or V2)
2. ✅ Maintain consistent styling
3. ✅ Use approved color palette
4. ✅ Keep typography consistent

### Mobile Optimization

1. ✅ Test on mobile devices
2. ✅ Verify touch-friendly elements
3. ✅ Check responsive images
4. ✅ Ensure readable font sizes

## Customization Checklist

Before generating, consider:

- [ ] What color best represents your brand?
- [ ] Do you need a navigation sidebar?
- [ ] Do you prefer V1 (clean) or V2 (modern)?
- [ ] Single README or full documentation?
- [ ] Target audience (technical, general)?
- [ ] Mobile accessibility important?

## Quick Tips

### For Maximum Impact

- **Color**: Choose a vibrant accent color
- **Navigation**: Enable sidebar for organization
- **Design**: V2 for modern look, V1 for simplicity
- **Format**: Full site for comprehensive docs

### For Simple Documentation

- **Color**: Subtle, professional color
- **Navigation**: Sidebar optional
- **Design**: V1 for minimalism
- **Format**: Single README for simplicity

### For Enterprise Look

- **Color**: Professional blue or green
- **Navigation**: Enable sidebar
- **Design**: V2 for modern feel
- **Format**: Full documentation site

## Examples

### Tech Startup Style

- Bright orange or teal accent
- V2 design with sidebar
- Full documentation
- Modern, energetic feel

### Open Source Project

- Community color (green/blue)
- V1 or V2 with sidebar
- Full documentation
- Professional appearance

### Corporate Documentation

- Company brand color
- V2 design with sidebar
- Full documentation
- Enterprise polish

---

**Ready to customize?** Start with our [Quick Start Guide](../getting-started/quick-start.md) and let your documentation reflect your brand!
