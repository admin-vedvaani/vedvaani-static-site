# Vedvaani Website

Static website hosted on Firebase Hosting.

## Quick Deploy

```bash
# Deploy changes to Firebase
firebase deploy --only hosting
```

## Setup (First Time)

```bash
# Install Firebase CLI if not already installed
npm install -g firebase-tools

# Login to Firebase
firebase login

# Deploy
firebase deploy --only hosting
```

## Custom Domain Setup

### 1. Add Custom Domain in Firebase Console

```bash
# Open Firebase Console
firebase open hosting
```

Or visit: https://console.firebase.google.com/project/vedvaani-24d6a/hosting/sites

### 2. Add Domain

1. Click **Add custom domain**
2. Enter your domain name (e.g., `vedvaani.com`)
3. Click **Continue**

### 3. Verify Domain Ownership

Firebase will provide a TXT record:

```
Type: TXT
Name: @
Value: [provided by Firebase]
```

Add this to your domain's DNS settings (via your domain registrar).

### 4. Configure DNS Records

Once verified, add the A records provided by Firebase:

```
Type: A
Name: @
Value: [IP addresses provided by Firebase]
```

For www subdomain:
```
Type: A
Name: www
Value: [IP addresses provided by Firebase]
```

### 5. Wait for SSL Provisioning

- DNS propagation: 5 minutes to 24 hours
- SSL certificate: Up to 24 hours after DNS propagation
- Status visible in Firebase Console

## Common Commands

```bash
# Deploy
firebase deploy

# Deploy hosting only
firebase deploy --only hosting

# View deployment history
firebase hosting:channel:list

# Open Firebase Console
firebase open

# Check Firebase version
firebase --version
```

## Project Info

- **Project ID**: vedvaani-24d6a
- **Public Directory**: Current directory (.)
- **SPA**: All routes redirect to index.html

## DNS Provider Examples

### Cloudflare
1. Go to DNS settings
2. Add records as specified above
3. Set Proxy status to **DNS only** (gray cloud)

### GoDaddy
1. Go to DNS Management
2. Add records with appropriate TTL
3. Wait for propagation

### Namecheap
1. Go to Advanced DNS
2. Add records as TXT/A records
3. Save changes

## Troubleshooting

**Domain not connecting?**
- Verify DNS records are correct
- Check DNS propagation: `dig yourdomain.com`
- Wait 24-48 hours for full propagation

**SSL not working?**
- Ensure DNS is fully propagated
- Wait up to 24 hours after DNS setup
- Check status in Firebase Console

**Deploy fails?**
- Ensure you're logged in: `firebase login`
- Check project ID: `firebase use`
- Verify firebase.json configuration
