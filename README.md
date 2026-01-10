# 🚀 GitHub Pages Deployment Checklist

## 📁 Files to Upload

Upload these files to your GitHub repository **root folder**:

### ✅ Required Files:
1. **index.html** - Main game file
2. **manifest.json** - PWA manifest
3. **sw.js** - Service worker
4. **404.html** - Error page (auto-redirects to home)
5. **.nojekyll** - Empty file (tells GitHub to skip Jekyll processing)
6. **logo-192.png** - App icon (192x192px)
7. **logo-512.png** - App icon (512x512px)

---

## 📝 Create .nojekyll File

### Option 1: Using GitHub Web Interface
1. Go to your repository
2. Click "Add file" → "Create new file"
3. Name it: `.nojekyll`
4. Leave it **completely empty**
5. Commit directly to main

### Option 2: Using Terminal/Command Line
```bash
touch .nojekyll
git add .nojekyll
git commit -m "Add .nojekyll for GitHub Pages"
git push
```

### Why do we need .nojekyll?
GitHub Pages uses Jekyll by default, which ignores files starting with `_` and can cause issues with service workers and manifests. The `.nojekyll` file disables Jekyll processing.

---

## 🖼️ Logo Files

Your lightning bolt logo needs to be saved as TWO files:

### logo-192.png
- Size: **192x192 pixels**
- Format: PNG with transparency
- Used for: App icon on home screen

### logo-512.png
- Size: **512x512 pixels**  
- Format: PNG with transparency
- Used for: Splash screen and high-res displays

### Quick Resize Options:
- **Online:** Use [iloveimg.com/resize-image](https://www.iloveimg.com/resize-image)
- **Photoshop:** Image → Image Size
- **Preview (Mac):** Tools → Adjust Size
- **Paint (Windows):** Resize → Pixels

---

## 📂 Your Repository Structure

```
your-repo/
├── index.html          ✅ Main game
├── manifest.json       ✅ PWA config
├── sw.js              ✅ Service worker
├── 404.html           ✅ Error page
├── .nojekyll          ✅ Empty file
├── logo-192.png       ✅ 192x192 icon
└── logo-512.png       ✅ 512x512 icon
```

---

## ⚙️ GitHub Pages Settings

1. Go to your repository
2. Click **Settings**
3. Scroll to **Pages** (left sidebar)
4. Under **Source**:
   - Branch: **main**
   - Folder: **/ (root)**
5. Click **Save**
6. Wait 1-2 minutes for deployment

Your site will be live at:
```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

---

## 🔗 Update Manifest Paths

If your repo is NOT at the root (e.g., `github.io/orion-surge/`), update manifest.json:

```json
{
  "start_url": "/orion-surge/",
  "scope": "/orion-surge/"
}
```

And update paths in index.html:
```html
<link rel="manifest" href="/orion-surge/manifest.json">
<link rel="icon" href="/orion-surge/logo-192.png">
```

And sw.js:
```javascript
const urlsToCache = [
  '/orion-surge/',
  '/orion-surge/index.html',
  '/orion-surge/manifest.json',
  '/orion-surge/logo-192.png',
  '/orion-surge/logo-512.png'
];
```

**OR** use relative paths everywhere:
```html
<link rel="manifest" href="./manifest.json">
<link rel="icon" href="./logo-192.png">
```

---

## 🧪 Testing Checklist

After deployment, test these:

### ✅ Basic Functionality
- [ ] Site loads without errors
- [ ] Game countdown works
- [ ] Can place bets
- [ ] Multiplier increases
- [ ] Can cash out
- [ ] Game crashes properly

### ✅ PWA Features
- [ ] Manifest loads (check DevTools → Application → Manifest)
- [ ] Service worker registers (check DevTools → Application → Service Workers)
- [ ] "Add to Home Screen" prompt appears (mobile)
- [ ] Icons display correctly
- [ ] Offline mode works (after first load)

### ✅ Mobile Testing
- [ ] Responsive on phone
- [ ] Touch controls work
- [ ] No horizontal scrolling
- [ ] Can install as app
- [ ] App opens in standalone mode

### ✅ Desktop Testing
- [ ] Install prompt appears in Chrome
- [ ] Game fits on screen without scrolling
- [ ] All modals work (Shop, Leaderboard, Settings)

---

## 🐛 Common Issues & Fixes

### Issue: "Failed to load manifest"
**Fix:** Check file paths. Use `/manifest.json` or `./manifest.json`

### Issue: Service worker not registering
**Fix:** 
1. Check `.nojekyll` file exists
2. Clear cache (Ctrl+Shift+Delete)
3. Hard refresh (Ctrl+Shift+R)

### Issue: Icons not showing
**Fix:**
1. Verify logo files uploaded
2. Check file names match exactly (case-sensitive)
3. Ensure files are PNG format

### Issue: 404 on any page refresh
**Fix:** This is normal! The 404.html will auto-redirect to home

### Issue: Google Sheets not connecting
**Fix:**
1. Add your Apps Script URL to index.html
2. Check CORS settings in Apps Script
3. Deploy Web App with "Anyone" access

---

## 🎉 Deployment Complete!

Once deployed:
1. Share your link: `https://yourusername.github.io/orion-surge`
2. Install on your phone
3. Test all features
4. Start promoting to friends!

---

## 📊 Monitor Your Site

### GitHub Insights
- Repository → Insights → Traffic
- See visitor stats, popular pages

### Google Sheets
- Watch USERS tab for new signups
- Monitor TOKENS tab for activity
- Track REWARDS claims

### Discord
- Get real-time notifications
- See big wins as they happen

---

## 🔄 Updating Your Site

When you make changes:
1. Edit files in GitHub (or push from local)
2. Commit changes
3. Wait ~1 minute for deployment
4. Clear cache and refresh

**Tip:** Version your cache in sw.js:
```javascript
const CACHE_NAME = 'orion-surge-v2'; // Change version number
```

---

## 📱 Custom Domain (Optional)

Want `play.oriondevcore.com` instead?

1. Buy domain (Namecheap, GoDaddy, etc.)
2. Add CNAME file to repo with your domain
3. Configure DNS:
   ```
   CNAME record: play → yourusername.github.io
   ```
4. In GitHub Settings → Pages → Custom domain

---

**You're all set! ⚡ Let's make some money! 💰**

*ORION DEV CORE - AI AMPLIFIES. I CREATE.*
