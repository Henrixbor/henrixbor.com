# Deploy henrixbor.com Portfolio

## Portfolio Built! ✅

Your portfolio is ready in: `/home/bob/clawd/henrixbor-portfolio/dist/`

Preview locally:
```bash
cd /home/bob/clawd/henrixbor-portfolio
npm run preview
# Opens at http://localhost:4321
```

---

## Deploy to Cloudflare Pages

### Option 1: Browser Login (Easiest)

```bash
# On your local machine with a browser:
wrangler login

# Then deploy:
cd /home/bob/clawd/henrixbor-portfolio
wrangler pages deploy dist --project-name=henrixbor-com
```

### Option 2: API Token (For Servers)

1. **Get Cloudflare API Token:**
   - Go to: https://dash.cloudflare.com/profile/api-tokens
   - Click "Create Token"
   - Use template: "Edit Cloudflare Workers"
   - OR custom token with permissions:
     - Account → Cloudflare Pages → Edit
   - Copy the token

2. **Set environment variable:**
   ```bash
   export CLOUDFLARE_API_TOKEN="your-token-here"
   
   # Or add to ~/.bashrc:
   echo 'export CLOUDFLARE_API_TOKEN="your-token"' >> ~/.bashrc
   source ~/.bashrc
   ```

3. **Deploy:**
   ```bash
   cd /home/bob/clawd/henrixbor-portfolio
   wrangler pages deploy dist --project-name=henrixbor-com
   ```

---

## After First Deployment

1. **Get deployment URL:**
   - Will be something like: `henrixbor-com.pages.dev`
   
2. **Configure custom domain:**
   ```bash
   # In Cloudflare dashboard:
   # Workers & Pages → henrixbor-com → Custom Domains
   # Add: henrixbor.com
   # Follow DNS setup instructions
   ```

3. **DNS Configuration (if domain elsewhere):**
   ```
   Type: CNAME
   Name: henrixbor.com (or @)
   Target: henrixbor-com.pages.dev
   ```

---

## Future Updates

Just rebuild and redeploy:
```bash
cd /home/bob/clawd/henrixbor-portfolio
npm run build
wrangler pages deploy dist
```

---

## Customize Portfolio

Edit: `/home/bob/clawd/henrixbor-portfolio/src/pages/index.astro`

Then rebuild:
```bash
npm run build
```

---

## Auto-Deploy with GitHub

1. **Push to GitHub:**
   ```bash
   cd /home/bob/clawd/henrixbor-portfolio
   git remote add origin https://github.com/openclawbob/henrixbor-com.git
   git push -u origin main
   ```

2. **Connect Cloudflare Pages:**
   - Dashboard → Workers & Pages → Create → Pages
   - Connect to Git
   - Select repository
   - Build settings:
     - Build command: `npm run build`
     - Output directory: `dist`

3. **Auto-deploys on push to main!**

---

## Need Help?

Run: `wrangler pages deploy --help`

Docs: https://developers.cloudflare.com/pages
