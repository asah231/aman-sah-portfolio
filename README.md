# Professional Computer Engineering Portfolio + AI Assistant

A no-build, responsive portfolio with an actual Cloudflare Pages Function chatbot using Cloudflare Workers AI.

## Files
- `public/index.html` — website content (replace all placeholders)
- `public/styles.css` — responsive design
- `public/app.js` — navigation and chat UI
- `public/_routes.json` — run Pages Functions only for `/api/*`
- `functions/api/chat.js` — live Workers AI backend + portfolio knowledge

## Customized profile
- Name: **Aman Sah**
- GitHub: **https://github.com/asah231**
- Skill areas supplied: **Python, Web Development, Software Development, AI/ML**
- Projects: **Coming soon** — no sample or invented completed projects are displayed.
- Resume, email, LinkedIn, education, experience, location: **not provided** and therefore not asserted.
- The AI knowledge in `functions/api/chat.js` matches these details. It does not automatically read GitHub.

## Add your content later
1. Add projects in `public/index.html` with verified descriptions, screenshots and actual repository links.
2. Update `PORTFOLIO_KNOWLEDGE` in `functions/api/chat.js` at the same time so the assistant answers accurately.
3. Add `public/resume.pdf` when ready, and replace the "Resume coming soon" text in the experience section with a link to `/resume.pdf`.
4. Add email/LinkedIn/education/experience information only when you wish to publish it.

## Publish for free via Cloudflare Pages + GitHub
1. Create a GitHub repository (e.g. `computer-engineering-portfolio`) and push the **project contents** (the `public` and `functions` directories at repository root).
2. On the Cloudflare dashboard, choose **Workers & Pages → Create application → Pages → Connect to Git** and select your GitHub repository.
3. Use **Framework preset: None**, **Production branch: main**, **Build command: `exit 0`**, **Build output directory: `public`**. Deploy.
4. After the first deployment open your **Pages project → Settings → Bindings → Add → Workers AI**. Set the variable/binding name to **`AI`** exactly. Save and **redeploy** the site.
5. Open the generated `*.pages.dev` URL and ask the assistant a question. The chat endpoint is `/api/chat` and responds only to POST requests.

The initial HTML/CSS preview works locally by opening `public/index.html` through an HTTP server, but the live chatbot **only works when the Pages Function is deployed with the AI binding**. For a full local integration test use Wrangler with an authenticated Cloudflare account:

```bash
npx wrangler pages dev public --ai AI
```

Note: Cloudflare Workers AI usage, including local development, can count against your AI allocation and may cost money when plan limits are exceeded. Check current pricing and limits before enabling paid options.

## Security & limitations
- The assistant does not require exposing any API key in browser JavaScript. The AI binding stays server-side.
- Simple message/body length limits, origin checks and context restrictions are included. For public or high-traffic sites, additionally configure Cloudflare WAF / rate limits and bot protection to avoid abuse and quota exhaustion.
- Current assistant answers use a manually edited knowledge context, **not** automatically indexed GitHub repositories or PDFs. You can extend this to retrieval-augmented generation later.
- Projects and unprovided resume/contact details are explicitly marked as unavailable. A working backend is supplied but cannot be verified against your Cloudflare account until you deploy and configure the binding.

## Sources
- Cloudflare Pages Git integration: https://developers.cloudflare.com/pages/get-started/git-integration/
- Static HTML deployment: https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- Pages Workers AI binding: https://developers.cloudflare.com/pages/functions/bindings/
- Pages Function route selection: https://developers.cloudflare.com/pages/functions/routing/
