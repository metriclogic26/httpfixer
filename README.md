> **⚠️ This project is no longer actively maintained.**
> The live site has been taken offline.
> The code remains available under the MIT license
> for anyone who wishes to fork and self-host.

---

# HttpFixer
Paste your URL. Get the exact config to fix it.

Free, browser-based web app security and performance fixers. No login. No backend. No tracking. Everything runs in your browser.

httpfixer.dev →

## What it does
Paste your URL. HttpFixer:

- Fetches your live HTTP headers and detects your stack automatically
- Audits security headers, CORS config, CSP, caching, and PageSpeed
- Generates the exact Nginx / Cloudflare / Vercel / Express config to paste
- No generic advice — fixes are specific to your detected stack

## Tools

| Tool | What it fixes |
|---|---|
| HeadersFixer | Missing HSTS, CSP, X-Frame-Options, Referrer-Policy, Permissions-Policy, COOP, COEP |
| CORSFixer | Wrong wildcard, missing preflight handler, credentials misconfigura OAuthFixer | PKCE misconfiguration, redirect_uri mismatch, invalid_grant errors |
| CSPFixer | Generates working CSP from your page's actual resources |
| EdgeFix | Cache-Control, Vary, Age, X-Cache misconfigurations. Accidentally cached auth responses. |
| SpeedFixer | Live PageSpeed audit results → exact server config to fix each failing audit |
| WebhookFix | Stripe webhook 401 / signature verification failed → complete handler for Next.js, Express, Fastify. |

## How it works
1. Enter your URL
2. HttpFixer fetches your live headers and detects your stack from the Server: header
3. Get the exact config block for your stack with a one-click copy button

ChatGPT cannot fetch your live headers. That's the moat.

## Supported stacks
Nginx · Apache · Cloudflare · Vercel · Netlify · Express · Caddy · Next.js · FastAPI · Django · WordPress · and more via manual selection

## Architecture
No backend. No build step. No npm install.

Two Cloudflare Workers handle CORS and PSI API proxying:
- headerproxy for live header fetching
- speedfixer-proxy — Google PageSpeed Insights API proxy with rate limiting

Everything else runs client-side in vanilla HTML, CSS, and JavaScript.

## Local development
```bash
git clone https://github.com/metriclogic26/httpfixer
cd httpfixer
python3 -m http.server 8080
# open http://localhost:8080
```

No dependencies. Open the HTML files directly.

## License
MIT — use it, fork it, build on it. The moat is the live fetch, not the code.
