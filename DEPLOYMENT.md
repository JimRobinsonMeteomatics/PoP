# 🚀 Deploying the Weather Dashboard

Your dashboard (`index-standalone.html`) is ready to deploy. Choose your platform:

## Option 1: Vercel (Recommended - 30 seconds)

```bash
# Install Vercel CLI
npm install -g vercel

# Login (opens browser)
vercel login

# Deploy
vercel --prod
```

Done! You'll get a URL like `https://hyper-local-weather.vercel.app`

## Option 2: Netlify (Drop & Deploy)

1. Go to https://app.netlify.com/drop
2. **Drag `index-standalone.html` onto the page**
3. Your site is live instantly!

## Option 3: GitHub Pages (Keeps code in repo)

```bash
# Rename for GitHub Pages
cp index-standalone.html docs/index.html

# Commit
git add docs/index.html
git commit -m "Deploy dashboard to GitHub Pages"
git push origin claude/weather-dashboard-spec-0mzkh0

# In repo settings: GitHub Pages → Source: Branch: main/master, folder: /docs
```

## Option 4: AWS S3 + CloudFront (High scale)

```bash
# Upload to S3
aws s3 cp index-standalone.html s3://your-bucket-name/index.html --acl public-read --content-type text/html

# CloudFront makes it fast globally (optional)
```

## Testing Before Deploy

```bash
# Quick test with Python
python3 -m http.server 8000

# Or Node
npx http-server

# Open: http://localhost:8000/index-standalone.html
```

## After Deploy

1. **Share the URL** - anyone can visit it
2. **First time**: Click "Allow" for location permission
3. **Credentials**: 
   - Get free Meteomatics API key: https://www.meteomatics.com/en/api/
   - Enter username/password in the dashboard
   - It saves to browser storage (localStorage)

## What Happens When Someone Visits

1. Page loads (no build needed)
2. Browser asks for location permission
3. They enter Meteomatics credentials (one-time)
4. Dashboard shows their exact backyard weather
5. Compares to nearby points (200-300m away)
6. Shows why 90m beats 5-13km

## Performance

- **Load time**: <2 seconds
- **Browser**: Works on Chrome, Firefox, Safari, Edge
- **Mobile**: Full responsive design
- **No backend needed**: All data goes directly to Meteomatics API from browser

## Customization

Edit `index-standalone.html` to change:
- Colors: Search for `text-cyan-400`, `text-red-400`, `text-magenta-400`
- Nearby point distance: Search for `0.001` (≈110m) and `0.003` (≈330m)
- Update frequency: Search for `15 * 60 * 1000` (15-minute refresh)

---

**Next Step**: Pick Option 1-4 above and follow the deployment steps. You'll have a live URL to share with others immediately.
