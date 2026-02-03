# 🔐 Environment Setup Guide

## Setting Up Your Local Environment

### Step 1: Copy the Example File
```bash
cp .env.example .env
```

### Step 2: Configure Database Credentials

1. **Install PostgreSQL** if not already installed
2. Create a new database:
   ```sql
   CREATE DATABASE pixel_phantoms_db;
   ```
3. Update these fields in your `.env`:
   - `DB_USER`: Your PostgreSQL username (default: `postgres`)
   - `DB_PASSWORD`: Your PostgreSQL password (⚠️ use a strong password)
   - `DB_HOST`: Database host (default: `localhost`)
   - `DB_PORT`: Database port (default: `5432`)
   - `DB_NAME`: Database name (e.g., `pixel_phantoms_db`)

### Step 3: Generate JWT Secret

Generate a cryptographically secure random secret:
```bash
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```

Copy the output and paste it as your `JWT_SECRET` value.

### Step 4: Configure Email Service

For Gmail SMTP:
1. Enable 2-Factor Authentication on your Google Account
2. Go to [Google App Passwords](https://myaccount.google.com/apppasswords)
3. Generate a new App Password for "Mail"
4. Update these fields in your `.env`:
   - `EMAIL_USER`: Your Gmail address
   - `EMAIL_PASS`: The 16-character App Password (no spaces)
   - `EMAIL_FROM`: Your Gmail address (same as EMAIL_USER)

⚠️ **Never use your actual Gmail password!**

## 🚨 Critical Security Guidelines

### If Credentials Are Exposed

If you accidentally committed credentials to Git:

1. **Immediately rotate all secrets:**
   - Change database password
   - Generate new JWT secret
   - Revoke and create new email app password

2. **Remove from Git history:**
   ```bash
   # Using git filter-branch (for small repos)
   git filter-branch --force --index-filter \
     "git rm --cached --ignore-unmatch .env" \
     --prune-empty --tag-name-filter cat -- --all
   
   # Or use BFG Repo-Cleaner (recommended for large repos)
   # Download from: https://rtyley.github.io/bfg-repo-cleaner/
   bfg --delete-files .env
   git reflog expire --expire=now --all
   git gc --prune=now --aggressive
   ```

3. **Force push to remote:**
   ```bash
   git push origin --force --all
   git push origin --force --tags
   ```

4. **Notify all contributors** to re-clone the repository

### Best Practices

✅ **DO:**
- Keep `.env` in `.gitignore`
- Use `.env.example` for documentation
- Rotate secrets regularly
- Use different credentials for dev/staging/production
- Enable GitHub secret scanning
- Use environment variables in production

❌ **DON'T:**
- Commit `.env` files
- Share credentials via email/chat
- Use weak or default passwords
- Reuse passwords across services
- Store secrets in code comments

## Production Deployment

For production environments:
- Use platform-specific environment variables (Netlify, Vercel, Heroku, etc.)
- Consider using secret management services (AWS Secrets Manager, HashiCorp Vault)
- Never use `.env` files in production repositories
- Enable audit logging for secret access

## Need Help?

If you accidentally exposed credentials or need security assistance:
1. Refer to [SECURITY.md](SECURITY.md) for reporting procedures
2. Contact maintainers privately (do not create public issues)
3. Follow the incident response process

---

**Last Updated:** February 3, 2026  
**Related:** [SECURITY.md](SECURITY.md) | [CONTRIBUTING.md](CONTRIBUTING.md)
