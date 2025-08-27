# Clickjacking Lab

This repository demonstrates a proof‑of‑concept (PoC) for **clickjacking (UI redressing)**.

## How it works
The PoC uses an `<iframe>` to load a target page, then overlays a deceptive button.
When the user clicks the visible button, the action is actually sent to the hidden framed page.

## Files
- **scripts/target.html** — demo target page with a pretend sensitive action
- **scripts/clickjacking-poc.html** — attacker page that frames the target and overlays a fake button

## Usage
1. Open **`scripts/clickjacking-poc.html`** in your browser.
2. Click the visible blue button → observe the framed page’s action trigger.
3. (Optional) If your browser blocks local iframes, run a tiny server:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080/scripts/clickjacking-poc.html
```

## Testing a real site (optional, authorized only)
If you’re authorized and the site allows framing, replace the iframe source:

```html
<iframe class="victim" src="https://authorized.example.com/target" sandbox="allow-forms allow-scripts"></iframe>
```

**Most production apps should block this via:**
- `X-Frame-Options: DENY` (or `SAMEORIGIN`)
- `Content-Security-Policy: frame-ancestors 'none'` (or a strict allowlist)

## Mitigation
- Use **X-Frame-Options: DENY** (or `SAMEORIGIN`)
- Use **CSP frame-ancestors** with a strict allowlist
- Add **user‑visible confirmations** for sensitive actions
- Consider **per‑action CSRF tokens** and **SameSite** cookies

## Ethics
For **educational use only**. Do not test against systems you do not own or lack explicit permission to assess.

