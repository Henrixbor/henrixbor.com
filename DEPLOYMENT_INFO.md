# henrixbor.com - Deployment Information

## ✅ Live Site

**Current URL:** https://b07b526b.henrixbor-com.pages.dev  
**Project Name:** henrixbor-com  
**Platform:** Cloudflare Pages  
**Deployed:** 2026-02-15 15:13 UTC

---

## ✅ Custom Domain Added (henrixbor.com)

**Status:** Domain added via API (2026-02-15 15:18 UTC)  
**Domain ID:** 24f2e9e7-b444-4711-ac4f-ecbd72325866  
**Zone ID:** 1a45b32ec36641e3650c6c908da2ce42  
**SSL:** Google (auto-provisioning)

### DNS Configuration Required:

1. **Go to DNS settings:**  
   https://dash.cloudflare.com/07bab86edf479ab554292046404e4db4/henrixbor.com/dns

2. **Add CNAME record:**
   ```
   Type: CNAME
   Name: @ (or henrixbor.com)
   Target: henrixbor-com.pages.dev
   Proxy status: Proxied (ON - orange cloud)
   ```

3. **Wait for propagation:**
   - Usually 5-10 minutes
   - Check status: https://henrixbor.com

4. **Verify:**
   - Site will be live at https://henrixbor.com
   - SSL certificate auto-issued by Cloudflare

---

## Update Portfolio

### Quick update:
```bash
cd /home/bob/clawd/henrixbor-portfolio
npm run build
wrangler pages deploy dist
```

### Edit content:
```bash
# Edit the page
nano src/pages/index.astro

# Rebuild and deploy
npm run build
wrangler pages deploy dist
```

---

## Credentials

Stored in: `/home/bob/clawd/.env`

```bash
CLOUDFLARE_API_TOKEN=M6qB8H318QLXR2yvrzxPQws9DexdiqQ4xHizegsA
CLOUDFLARE_ACCOUNT_ID=07bab86edf479ab554292046404e4db4
```

**To use:**
```bash
source /home/bob/clawd/.env
wrangler pages deploy dist
```

---

## Rollback

```bash
# List deployments
wrangler pages deployment list --project-name=henrixbor-com

# Rollback to previous
wrangler pages deployment tail
```

---

## Analytics

**Cloudflare Web Analytics (free):**
1. Dashboard → henrixbor-com → Analytics
2. View traffic, bandwidth, requests

**Add Plausible (optional):**
```html
<script defer data-domain="henrixbor.com" 
  src="https://plausible.io/js/script.js"></script>
```

---

## Future Enhancements

### Add pages:
```bash
# Create new page
echo "..." > src/pages/projects.astro
npm run build && wrangler pages deploy dist
```

### Add blog:
```bash
# Add MDX support
npx astro add mdx

# Create blog posts
mkdir -p src/pages/blog
echo "..." > src/pages/blog/first-post.mdx
```

### Add contact form:
- Use Cloudflare Workers
- Or use form services (Formspree, etc.)

---

## Monitoring

**Uptime Robot (free):**
1. Sign up: https://uptimerobot.com
2. Add monitor:
   - Type: HTTP(s)
   - URL: https://henrixbor.com
   - Interval: 5 minutes
3. Get alerts via Telegram

---

## Commands Reference

```bash
# Build
npm run build

# Deploy
wrangler pages deploy dist

# Preview locally
npm run preview

# List deployments
wrangler pages deployment list

# View logs
wrangler pages deployment tail

# Delete project (careful!)
wrangler pages project delete henrixbor-com
```

---

## Support

- **Cloudflare Docs:** https://developers.cloudflare.com/pages
- **Astro Docs:** https://docs.astro.build
- **Issues:** Check `/home/bob/clawd/henrixbor-portfolio/DEPLOY.md`

---

**Status:** 🟢 LIVE
**Last updated:** 2026-02-15
