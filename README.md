# 🎨 blackroad-brand-official

**BlackRoad OS, Inc.**

## Description

OFFICIAL brand kit

## Features

- JetBrains Mono typography
- Official BlackRoad colors (#FF9D00 → #0066FF spectrum)
- Golden Ratio spacing (φ = 1.618)
- Responsive design
- BlackRoad OS, Inc. branding

## Deployment

This project is part of the BlackRoad empire:
- **GitHub:** https://github.com/BlackRoad-OS/blackroad-brand-official
- **Live:** https://blackroad-brand-official.pages.dev (or custom domain)
- **Infrastructure:** Cloudflare Pages + Cloudflare AI Gateway + Tailscale mesh → Raspberry Pi cluster

## Routing & OATH / OAuth

All traffic — including AI vendor API calls — routes exclusively through BlackRoad infrastructure:

```
Client → Cloudflare Pages → Cloudflare Access (OATH gate) → Tailscale mesh → BlackRoad Pi cluster
```

- **OATH/OAuth:** Cloudflare Access (zero-trust). See [`OATH.md`](OATH.md) for setup steps.
- **AI Gateway:** Cloudflare AI Gateway (`wrangler.toml` — slug `blackroad-ai-gateway`)
- **Approved AI systems:** @blackboxprogramming and @lucidia **only**
- **Blocked direct vendors:** OpenAI, Anthropic, GitHub Copilot / Codex

## Code Ownership

All changes require review by @blackboxprogramming or @lucidia (see `.github/CODEOWNERS`).
No Copilot, Codex, or other third-party AI agents are authorized to commit, review, or merge.

## Brand Compliance

✅ Uses official colors from BLACKROAD_OFFICIAL_BRAND_COLORS.md
✅ JetBrains Mono font
✅ Golden Ratio spacing
✅ Proprietary - BlackRoad OS, Inc.

## License

**PROPRIETARY - BlackRoad OS, Inc.**

All rights reserved. This code is proprietary and confidential.
Unauthorized copying, distribution, or use is strictly prohibited.

© 2026 BlackRoad OS, Inc.

## Contact

- **Company:** BlackRoad OS, Inc.
- **Email:** blackroad.systems@gmail.com
- **Primary:** amundsonalexa@gmail.com
- **Website:** https://blackroad.io

---

🎨 Built with BlackRoad tooling | Part of the BlackRoad Empire
