# Security Policy

## Overview

This project is a static HTML/CSS resume with **zero JavaScript** and no backend. Security is enforced through multiple layers of defense.

## Security Features

### Content Security Policy (CSP)
- ✅ **No JavaScript execution** - `script-src 'none'`
- ✅ **Local resources only** - `default-src 'none'`
- ✅ **Self-hosted CSS** - `style-src 'self' 'unsafe-inline'`
- ✅ **No external connections** - `connect-src 'none'`
- ✅ **Clickjacking prevention** - `frame-ancestors 'none'`
- ✅ **Force HTTPS** - `upgrade-insecure-requests`

### Additional Security Headers
- **X-Frame-Options**: DENY (prevents clickjacking)
- **X-Content-Type-Options**: nosniff (prevents MIME sniffing)
- **X-XSS-Protection**: 1; mode=block (legacy XSS protection)
- **Referrer-Policy**: no-referrer (privacy protection)
- **Permissions-Policy**: Blocks all device APIs

### No External Dependencies
- ✅ No CDNs (Bootstrap, jQuery, etc.)
- ✅ No external fonts
- ✅ No analytics or tracking
- ✅ No third-party scripts
- ✅ All resources self-hosted

### Data Privacy
- 🔒 No cookies
- 🔒 No local storage
- 🔒 No session storage
- 🔒 No tracking pixels
- 🔒 No analytics
- 🔒 No form submissions

## Known Limitations

### `'unsafe-inline'` in CSP
The CSP includes `'unsafe-inline'` for `style-src` to support:
- CSS animations and keyframes
- Pseudo-element content
- CSS custom properties (variables)
- Gradient and transform effects

**Why it's safe here:**
- No user input is rendered
- No dynamic CSS generation
- All CSS is static and reviewed
- No `attr()` usage with user data
- Script execution is completely blocked

## Attack Surface Analysis

### CSS Injection
❌ **Not vulnerable** - No user input, no dynamic CSS, all content is static

### XSS (Cross-Site Scripting)
❌ **Not vulnerable** - JavaScript is completely disabled via CSP

### Clickjacking
❌ **Not vulnerable** - X-Frame-Options: DENY and frame-ancestors 'none'

### CSRF (Cross-Site Request Forgery)
❌ **Not applicable** - No forms, no state, no cookies

### Data Exfiltration
❌ **Not vulnerable** - No external connections allowed, no network requests

### Supply Chain Attacks
❌ **Not vulnerable** - No external dependencies or package managers

## Reporting Security Issues

If you discover a security vulnerability, please email:
- **Contact**: jdunn0423@gmail.com
- **Expected Response Time**: Within 48 hours

Please include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

## Security Checklist

- [x] Content Security Policy configured
- [x] All external dependencies removed
- [x] HTTPS enforced (via upgrade-insecure-requests)
- [x] Clickjacking prevention
- [x] MIME sniffing prevention
- [x] No JavaScript execution
- [x] No user input fields
- [x] No external network requests
- [x] No cookies or tracking
- [x] Static content only
- [x] Regular security audits

## Updates

This project is regularly audited for security issues. Last security review: 2025-10-30

## License

MIT License - See LICENSE file for details
