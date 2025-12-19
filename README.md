# GBE Awards Magazine 2025 📖

An interactive digital flipbook magazine for the GBE Awards 2025, featuring a realistic page-turning experience with smooth animations and responsive design.

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://magazine.gbeaward.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 🌟 Features

- **Realistic Page Flip Animation** - Smooth page-turning effects powered by Turn.js
- **Responsive Design** - Optimized for both desktop and mobile devices
  - Double-page view on desktop (landscape)
  - Single-page view on mobile (portrait)
- **Multiple Navigation Options**
  - Previous/Next buttons
  - Keyboard arrow keys (← →)
  - Touch swipe gestures on mobile
  - Interactive page slider
- **Optimized Performance**
  - Lazy loading for images beyond the first 6 pages
  - Hardware acceleration enabled
  - Async image decoding
- **Modern UI**
  - Glassmorphism design with backdrop blur effects
  - Dark theme optimized for reading
  - Safe area support for notched devices
  - Fullscreen mode support

## 📋 Table of Contents

- [Demo](#demo)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Technical Details](#technical-details)
- [Customization](#customization)
- [Browser Compatibility](#browser-compatibility)
- [Performance Optimization](#performance-optimization)
- [Deployment](#deployment)
- [License](#license)

## 🚀 Demo

Visit the live demo at: [magazine.gbeaward.com](https://magazine.gbeaward.com)

## ⚡ Quick Start

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- Python 3.x or any other local web server (required for local development)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/gbe-magazine-2025.git
   cd gbe-magazine-2025
   ```

2. **Start a local web server**
   
   Using Python 3:
   ```bash
   python3 -m http.server 8000
   ```
   
   Or using Python 2:
   ```bash
   python -m SimpleHTTPServer 8000
   ```
   
   Or using Node.js (with `http-server`):
   ```bash
   npx http-server -p 8000
   ```

3. **Open in browser**
   
   Navigate to `http://localhost:8000` in your web browser

## 📁 Project Structure

```
gbe-magazine-2025/
├── index.html              # Redirect to flip.html
├── flip.html              # Main flipbook application
├── CNAME                  # Custom domain configuration
├── assets/
│   └── js/
│       └── turn.min.js    # Turn.js library for page flipping
└── pages/
    ├── page-01.jpg        # Magazine pages (82 total)
    ├── page-02.jpg
    ├── ...
    └── page-82.jpg
```

## 🔧 Technical Details

### Dependencies

- **jQuery 3.7.1** - DOM manipulation and event handling
- **Turn.js** - Core page-turning functionality

Both libraries are loaded via CDN for optimal performance and caching.

### Key Technologies

- **HTML5** - Semantic markup
- **CSS3** - Modern styling with CSS Grid, Flexbox, and CSS Variables
- **Vanilla JavaScript** - No framework dependencies
- **Responsive Design** - Mobile-first approach with adaptive layouts

### CSS Architecture

The application uses CSS custom properties (variables) for theming:

```css
:root {
  --bg: #0b0b0b;              /* Background color */
  --glass: rgba(0, 0, 0, 0.55); /* Glass effect */
  --border: rgba(255, 255, 255, 0.14); /* Border color */
  --text: rgba(255, 255, 255, 0.92);   /* Text color */
  --muted: rgba(255, 255, 255, 0.65);  /* Muted text */
  --radius: 14px;              /* Border radius */
}
```

### Turn.js Configuration

```javascript
$("#book").turn({
  autoCenter: true,      // Center the book in the viewport
  display: displayMode(), // 'single' or 'double' based on screen size
  gradients: true,       // Enable gradient shadows
  acceleration: true,    // Hardware acceleration
  duration: 650,         // Page turn animation duration (ms)
});
```

## 🎨 Customization

### Changing the Number of Pages

1. Update `totalPages` constant in `flip.html`:
   ```javascript
   const totalPages = 82; // Change this number
   ```

2. Update slider max value:
   ```html
   <input id="slider" type="range" min="1" max="82" value="1" />
   ```

3. Update page counter:
   ```html
   <div class="pageText" id="pageText">1 / 82</div>
   ```

### Adding Your Own Magazine Pages

1. Export your magazine pages as JPG images
2. Name them sequentially: `page-01.jpg`, `page-02.jpg`, etc.
3. Place them in the `pages/` directory
4. Recommended image dimensions:
   - Desktop (double-page): 2400x1600px total (1200x1600px per page)
   - Mobile (single-page): 1200x1600px

### Customizing Colors

Modify the CSS variables in the `:root` selector in `flip.html`:

```css
:root {
  --bg: #0b0b0b;              /* Change background */
  --text: rgba(255, 255, 255, 0.92); /* Change text color */
  /* ... other variables */
}
```

### Changing Title

Update the title in two places in `flip.html`:

```html
<title>Your Magazine Title</title>
<!-- and -->
<div class="title">Your Magazine Title</div>
```

## 🌐 Browser Compatibility

| Browser | Minimum Version | Notes |
|---------|----------------|-------|
| Chrome | 90+ | Full support |
| Firefox | 88+ | Full support |
| Safari | 14+ | Full support, iOS safe area supported |
| Edge | 90+ | Full support |
| Opera | 76+ | Full support |

### Features by Browser

- **CSS Grid & Flexbox** - All modern browsers
- **CSS Variables** - All modern browsers
- **Backdrop Filter** - Chrome 76+, Safari 14+, Firefox 103+
- **Safe Area Insets** - Safari iOS 11+ (for notched devices)
- **Fullscreen API** - All modern browsers

## ⚡ Performance Optimization

### Implemented Optimizations

1. **Lazy Loading**
   - First 6 pages load eagerly for instant viewing
   - Remaining pages load lazily to reduce initial load time

2. **Hardware Acceleration**
   - Turn.js configured with `acceleration: true`
   - CSS transforms utilize GPU rendering

3. **Image Optimization**
   - Async decoding enabled: `img.decoding = "async"`
   - Proper `object-fit: contain` prevents layout shifts

4. **Debounced Resize Handler**
   - Resize events throttled with 120ms delay
   - Prevents excessive re-calculations

5. **CDN Delivery**
   - jQuery loaded from Cloudflare CDN
   - Benefits from global caching

### Recommended Image Optimization

For best performance, optimize your JPG images:

```bash
# Using ImageMagick
convert input.jpg -quality 85 -strip output.jpg

# Using jpegoptim
jpegoptim --max=85 --strip-all *.jpg

# Using mozjpeg
cjpeg -quality 85 -optimize input.jpg > output.jpg
```

Target file size: 200-500KB per page

## 🚀 Deployment

### GitHub Pages

1. Push your code to GitHub
2. Go to repository Settings → Pages
3. Select source: `main` branch, `/` (root)
4. Add `CNAME` file with your custom domain (if applicable)
5. Configure DNS with your domain provider

### Custom Domain Setup

The repository includes a `CNAME` file configured for `magazine.gbeaward.com`. To use your own domain:

1. Update `CNAME` file with your domain
2. Add DNS records at your domain provider:
   - Type: A Record
   - Host: @ (or subdomain)
   - Value: GitHub Pages IPs (see GitHub docs)
   - Or use CNAME pointing to `username.github.io`

### Other Hosting Platforms

**Netlify:**
```bash
netlify deploy --prod
```

**Vercel:**
```bash
vercel --prod
```

**Cloudflare Pages:**
- Connect GitHub repository
- Build settings: None required (static site)
- Build output directory: `/`

## 📱 Mobile Optimization

The application automatically adapts to mobile devices:

- **Touch Gestures** - Swipe left/right to navigate
- **Single Page View** - Optimized for portrait orientation
- **Responsive Controls** - Buttons and UI elements scale appropriately
- **Safe Area Support** - Respects notches and device cutouts
- **Viewport Optimization** - Uses `viewport-fit=cover`

## 🐛 Troubleshooting

### Issue: Pages not loading locally

**Solution:** You must use a web server. Opening `flip.html` directly in a browser (`file://` protocol) won't work due to CORS restrictions.

### Issue: jQuery/Turn.js not loading

**Solution:** Check your internet connection. Libraries are loaded from CDN. For offline use, download and host them locally.

### Issue: Images not displaying

**Solution:** Verify image paths are correct and images exist in the `pages/` directory.

### Issue: Fullscreen not working

**Solution:** User gesture is required to enter fullscreen. The button must be clicked by the user (not triggered programmatically on page load).

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Turn.js](http://www.turnjs.com/) - Excellent page flip library
- [jQuery](https://jquery.com/) - Simplified DOM manipulation
- [Cloudflare](https://www.cloudflare.com/) - CDN services

## 📞 Support

For issues or questions:
- Open an issue on GitHub
- Contact: [your-email@example.com]

---

Made with ❤️ for GBE Awards 2025
