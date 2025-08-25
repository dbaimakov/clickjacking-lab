# Clickjacking Lab

This repository demonstrates a simple proof of concept (PoC) for **clickjacking**.

## How it works
The PoC uses an `<iframe>` to load a target page, then places a deceptive button on top.  
When the user thinks they are clicking the visible button, their click is actually sent to the framed page.

## Usage
1. Open `scripts/clickjacking-poc.html` in your browser.
2. Replace the `iframe src="https://example.com"` with any page you want to test (only on systems you own or are authorized to test).
3. Observe how the overlaid button hides the real action beneath it.

## Mitigation
- Use the `X-Frame-Options: DENY` or `SAMEORIGIN` header.
- Or use CSP: `Content-Security-Policy: frame-ancestors 'none';`

## Ethics
This project is for **educational purposes only**.  
Do not use against applications you do not own or have permission to test.
