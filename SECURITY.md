# Security Policy

## 🔒 Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| Main (latest) | ✅ Yes |
| Older commits | ❌ No |

We only support the latest version at [pixelphantoms.netlify.app](https://pixelphantoms.netlify.app/).

----

## 📚 Reporting a Vulnerability

**Please DO NOT create a public GitHub issue for security vulnerabilities.**

### How to Report

**Option 1: Private Email**
- 📧 Email : sayeeygosavi@gmail.com
- Subject: `[SECURITY] Brief Description`

**Option 2: GitHub Security Advisory**
1. Go to the [Security tab](https://github.com/sayeeg-11/Pixel_Phantoms/security)
2. Click "Report a vulnerability"
3. Fill out the form

### What to Include
- Clear description of the vulnerability
- Steps to reproduce
- Affected files/pages
- Potential impact
- Screenshots/code (if applicable)

---

## ⏱️ Response Timeline

- **24-48 hours:** Initial acknowledgment
- **7-14 days:** Status update
- **14-30 days:** Fix development
- **30-45 days:** Public disclosure (after fix deployed)

---

## 🎯 Severity Levels

- **🔴 Critical:** Remote code execution, data breaches, authentication bypass
- **🟠 High:** XSS, CSRF, authorization flaws
- **🟡 Medium:** Information disclosure, insecure configurations
- **🟢 Low:** Minor leaks, best practice violations

---
## ✅ Security Guidelines for Contributors

### Environment Variables & Secrets

**⚠️ CRITICAL SECURITY RULES:**

1. **Never commit `.env` files**
   - Always use `.env.example` for documentation
   - The `.env` file is excluded via `.gitignore`
   - See [ENVIRONMENT_SETUP.md](ENVIRONMENT_SETUP.md) for proper setup

2. **If you accidentally commit secrets:**
   - Immediately report to maintainers (private email, not public issue)
   - Follow the credential rotation guide in [ENVIRONMENT_SETUP.md](ENVIRONMENT_SETUP.md#if-credentials-are-exposed)
   - Remove from Git history using `git filter-branch` or BFG Repo-Cleaner
   - Change all exposed passwords/tokens immediately

3. **Credential Rotation Schedule:**
   - Database passwords: Every 90 days
   - JWT secrets: Every 180 days or after any suspected compromise
   - Email app passwords: Every 180 days
   - Production secrets: Immediately after any team member departure

### Code Security Best Practices

- Validate and sanitize all user inputs
- Use HTTPS for external resources
- Never hardcode sensitive information
- Implement proper access controls
- Keep dependencies updated
- Use `rel="noopener noreferrer"` for external links
- Enable GitHub secret scanning (maintainers)
- Use environment-specific credentials (dev/staging/prod)

---
## 📚 Additional Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/) - Most critical web security risks
- [Web Security Basics](https://developer.mozilla.org/en-US/docs/Web/Security) - MDN security guide
- [GitHub Security Best Practices](https://docs.github.com/en/code-security) - Securing your repository

---

## 📞 Contact

- 📧 Security Issues: sayeeygosavi@gmail.com
- 🐛 Bug Reports: [Create an Issue](https://github.com/sayeeg-11/Pixel_Phantoms/issues)

---

**Thank you for helping keep Pixel Phantoms safe!** 🛡️👻




