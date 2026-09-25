# Quick Setup Guide (5-10 minutes)

## Step 1: Extract Files (1 min)

```bash
unzip client-dashboard.zip
cd client-dashboard
```

## Step 2: Install Dependencies (2 min)

```bash
npm install
```

## Step 3: Local Configuration (1 min)

```bash
cp .env.example .env
```

Edit `.env`:
```
REACT_APP_GOOGLE_SHEET_ID=1hAMzQCA_3-dFu95zzQ2Vjt4MslrfvqHczZqM9GJz-IY
```

## Step 4: Run Locally (optional - test before deploy)

```bash
# Install Netlify CLI (one-time)
npm install -g netlify-cli

# Start dev server with Functions support
netlify dev

# Opens http://localhost:3000
```

Press Ctrl+C to stop.

## Step 5: Deploy to Netlify

### Option A: Netlify CLI (Fastest)

```bash
npm run build
netlify deploy --prod
```

Done! Your URL appears on screen.

### Option B: GitHub + Netlify (Recommended for Teams)

1. **Push to GitHub**
   ```bash
   git init
   git add .
   git commit -m "Add SAM Dashboard"
   git remote add origin https://github.com/YOUR_USERNAME/sam-dashboard.git
   git push -u origin main
   ```

2. **Connect to Netlify**
   - Visit [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Select GitHub → find your repo
   - Accept defaults → Click "Deploy site"
   - Wait 2-3 minutes

3. **Add Environment Variables**
   - Netlify dashboard → Site settings → Build & deploy → Environment
   - Click "Edit variables"
   - Add:
     ```
     WINDSOR_API_KEY = your-windsor-api-key-here
     REACT_APP_GOOGLE_SHEET_ID = 1hAMzQCA_3-dFu95zzQ2Vjt4MslrfvqHczZqM9GJz-IY
     ```
   - Click "Save"
   - Netlify auto-redeploys

4. **Done!** Copy your URL from the dashboard.

## Step 6: Verify It Works

1. Visit your Netlify URL
2. Should see "SAM Dashboard" header
3. Should show revenue data with 6 tabs
4. Open DevTools (F12) → Console → No errors
5. Test each tab: Overview, Clients, Trends, CSat, Resources

## That's It!

Your dashboard is live. Share the URL with your team.

---

## Troubleshooting

**"Failed to load revenue data"**
- Check browser console (F12)
- Go to Netlify → Site settings → Build & deploy → Environment
- Verify `WINDSOR_API_KEY` is set
- Redeploy after adding env vars

**Build Failed**
- Check Netlify build log
- Verify `npm install` works locally
- Ensure Node.js 14+

**Need to Update Data**

After making changes:
```bash
git add .
git commit -m "Update: description"
git push origin main
# Netlify auto-redeploys
```

---

## Next Steps

- See **README.md** for full documentation
- Customize colors in `src/styles/*.css`
- Add new metrics in `src/components/Overview.jsx`
- Check data in [Google Sheets](https://docs.google.com/spreadsheets/d/1hAMzQCA_3-dFu95zzQ2Vjt4MslrfvqHczZqM9GJz-IY/)
