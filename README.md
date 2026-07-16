# Ferrum Engineering LLC — Landing Page

One-page consulting landing page for Ferrum Engineering LLC.

Built with:
- Single HTML file (zero build step)
- Embedded CSS (no framework)
- Google Fonts (Inter + JetBrains Mono)
- No JavaScript dependencies

## Deploy

### Cloudflare Pages (recommended)
1. Push this folder to a new GitHub repo
2. Connect to Cloudflare Pages
3. Set build command: none
4. Set build output: `./`
5. Set custom domain: `ferrumengineeringllc.com`

### Any static host
Just serve the `index.html` file. Works with any HTTP server.

```
python3 -m http.server 8080
```

Or with nginx, just point root to this directory.
