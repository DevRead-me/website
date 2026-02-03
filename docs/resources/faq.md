# Frequently Asked Questions

Got questions? We've got answers! Here are the most common questions about DevRead.me.

## General Questions

### What is DevRead.me?

DevRead.me is an AI-powered web application that transforms your code and project information into professional, ready-to-deploy Docsify documentation packages in approximately 30 seconds.

Instead of spending hours writing documentation manually, DevRead.me uses advanced AI (Groq Llama 3.3 70B) to analyze your project and automatically generate comprehensive, well-structured documentation files.

### How much does it cost?

DevRead.me is **completely free** to use! There are no hidden fees, no subscriptions, and no registration required.

### Do I need to create an account?

No! DevRead.me is a web-based application that requires no account creation or login. Simply visit the website and start generating documentation immediately.

### Is my data safe?

Yes, your data is completely safe:

- **No permanent storage** - Input is processed and immediately discarded
- **No training data** - Your content is never used to train AI models
- **No tracking** - We don't track personal information
- **Secure communication** - All data transmitted via HTTPS encryption

## Technical Questions

### How fast is the documentation generation?

Complete documentation generation takes approximately **30 seconds**. This includes:

- AI analysis of your content
- Generation of 5 markdown files
- Template processing
- ZIP package creation

Actual time may vary based on input size and system load.

### What files are generated?

When you select "Full Documentation," you receive:

1. **README.md** - Project overview and quick start
2. **SETUP.md** - Detailed installation instructions
3. **API.md** - API endpoints and methods
4. **FEATURES.md** - Feature descriptions
5. **TROUBLESHOOTING.md** - Common issues and solutions

Plus configuration files for Docsify:

- `index.html` - Docsify configuration
- `_sidebar.md` - Navigation structure
- `custom.css` - Styling

### Can I use just the single README mode?

Absolutely! Choose "Single README Mode" to get only an enhanced README.md file. This is perfect for:

- Simple projects
- GitHub repositories
- Minimal setup requirements
- Quick documentation needs

### Can I edit the generated documentation?

Yes! The generated files are standard markdown and HTML. You can easily edit them:

- Edit `.md` files in any text editor
- Modify `custom.css` for styling
- Update `_sidebar.md` for navigation
- Customize `index.html` configuration

### What AI model is used?

DevRead.me uses **Groq Llama 3.3 70B Versatile** - a state-of-the-art large language model with 70 billion parameters. This model is optimized for:

- Code understanding
- Professional writing
- Technical accuracy
- Clear explanations

### How does the AI know what to write?

The AI analyzes your input and:

1. Understands your project type
2. Identifies key features and components
3. Recognizes technical patterns
4. Generates appropriate documentation
5. Structures content logically

The more detailed your input, the better the output.

## Customization Questions

### Can I change the colors?

Yes! DevRead.me includes a color picker where you can:

- Choose any custom color
- See live preview
- Apply to all documentation elements
- Use pre-selected color schemes

### Can I disable the sidebar?

Yes! Toggle the "Include Sidebar" option to:

- Create a cleaner look
- Maximize content space
- Simplify navigation
- Create single-page documentation

### Are there different design options?

Yes! Choose between:

- **V1 Design** - Clean and minimal
- **V2 Design** - Modern and enhanced

Both are fully responsive and professional.

### Can I customize the generated documentation after download?

Absolutely! The generated files are standard web technologies:

- Edit markdown files (.md)
- Modify CSS (custom.css)
- Update HTML (index.html)
- Add new pages
- Customize everything

## Deployment Questions

### Where can I host my documentation?

Your generated documentation works with any static hosting:

- ✅ GitHub Pages
- ✅ Vercel
- ✅ Netlify
- ✅ AWS S3
- ✅ Any web server
- ✅ Self-hosted

### Do I need a backend or database?

No! Generated documentation is completely static:

- No backend required
- No database needed
- No server configuration
- Works with simple file hosting

### How do I deploy to GitHub Pages?

1. Create a GitHub repository
2. Extract documentation to your repo
3. Push to GitHub
4. Go to Settings → Pages
5. Select your branch and folder
6. Save - your docs are live!

See [Deployment Guide](../documentation/deployment.md) for detailed instructions.

### How do I deploy to Vercel?

1. Push your documentation to GitHub
2. Visit vercel.com
3. Click "New Project"
4. Select your GitHub repository
5. Click "Deploy"
6. Vercel automatically deploys!

See [Deployment Guide](../documentation/deployment.md) for more details.

### How do I use a custom domain?

After deploying your documentation:

**GitHub Pages:**

1. Go to Settings → Pages
2. Under "Custom domain" add your domain
3. Update DNS records at your registrar

**Vercel:**

1. In project settings → Domains
2. Enter your domain
3. Follow DNS configuration

**Netlify:**

1. In site settings → Domain management
2. Add custom domain
3. Configure DNS records

DNS changes take 24-48 hours to propagate.

## Usage Questions

### What content should I provide?

Provide any of the following:

- Your existing README.md file
- Project description and overview
- Code snippets or examples
- Feature descriptions
- Installation instructions
- API documentation
- Setup steps

The more detailed, the better the output!

### Can I use it for non-English documentation?

The AI model works best with English content. Other languages may produce suboptimal results. We're exploring multi-language support for future versions.

### What if I'm not satisfied with the result?

You can:

1. Try again with more detailed input
2. Edit the generated files manually
3. Regenerate with different options
4. Combine generated content with manual edits

No limits on generation attempts!

### Can I generate documentation multiple times?

Yes! Generate as many times as you want, completely free. Try different:

- Content descriptions
- Color schemes
- Design versions
- Output formats

No rate limits for documentation generation (per reasonable use).

## Troubleshooting Questions

### Why is generation taking longer than 30 seconds?

- **High server load** - Wait and retry
- **Large input** - Smaller input may be faster
- **Network issues** - Check your connection
- **API limits** - May be temporarily throttled

Try again after a few minutes.

### Why is the sidebar not appearing?

- Verify the "Include Sidebar" option was enabled
- Check that `_sidebar.md` file exists in the extracted ZIP
- Clear your browser cache
- Try regenerating

### Why are images not loading?

- Check that image files are included in the ZIP
- Verify image paths in markdown
- Ensure images are in the correct folder
- Check file permissions if self-hosting

### Why are links broken?

- Use relative links in markdown
- Verify file names match exactly
- Check for typos in link paths
- Ensure files are in correct folders

See [Troubleshooting Guide](troubleshooting.md) for more help.

## Feature Questions

### Will there be more features?

Yes! Future features planned include:

- User accounts and history
- More AI models
- Custom templates
- Batch processing
- Webhook notifications
- API access
- More language support

### Can I request a feature?

Absolutely! We'd love to hear your ideas:

- [Contact us](contact.md)
- [Discord server](https://discord.gg/yKU4Q2mHj8)
- [GitHub issues](https://github.com/devread-me)

### Can I contribute to DevRead.me?

Yes! We welcome contributions:

- Bug reports
- Feature suggestions
- Code contributions
- Documentation improvements

Visit our GitHub or Discord to get involved!

## Support & Help

### I found a bug, what should I do?

1. Check [Troubleshooting Guide](troubleshooting.md)
2. Check this FAQ
3. [Contact support](contact.md)
4. [Join our Discord](https://discord.gg/yKU4Q2mHj8)

### How do I get help?

We have multiple support channels:

- 📖 [This documentation](../)
- 🐛 [Troubleshooting Guide](troubleshooting.md)
- 💬 [Contact & Support](contact.md)
- 🎮 [Discord Community](https://discord.gg/yKU4Q2mHj8)

### Where can I report issues?

Report issues on:

- [GitHub Issues](https://github.com/devread-me)
- [Discord Server](https://discord.gg/yKU4Q2mHj8)
- [Contact Form](contact.md)

---

**Didn't find your answer?** Check the [Troubleshooting Guide](troubleshooting.md) or [Contact Support](contact.md)!
