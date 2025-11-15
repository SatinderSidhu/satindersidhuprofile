# Custom Domain Setup Guide

## GitHub Pages Configuration ✅
Your GitHub Pages site has been configured to use `www.satindersidhu.com`

## Squarespace DNS Configuration

Follow these steps to point your Squarespace domain to GitHub Pages:

### Step 1: Access Squarespace DNS Settings

1. Log in to your Squarespace account
2. Go to **Settings** > **Domains**
3. Click on **satindersidhu.com**
4. Click **DNS Settings** or **Advanced Settings**

### Step 2: Configure DNS Records

You need to add the following DNS records in Squarespace:

#### For www.satindersidhu.com (CNAME Record)

**Add a CNAME record:**
- **Host/Name**: `www`
- **Type**: `CNAME`
- **Value/Points to**: `satindersidhu.github.io`
- **TTL**: Automatic or 3600

#### For satindersidhu.com (Apex Domain - A Records)

**Add these 4 A records** to point the root domain to GitHub:
- **Host/Name**: `@` (or leave blank)
- **Type**: `A`
- **Value**: `185.199.108.153`

Repeat for these additional IP addresses:
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

### Step 3: Remove Conflicting Records

**Important**: Remove any existing A or CNAME records that conflict with the above, such as:
- Existing CNAME for `www` pointing to Squarespace
- Existing A records for `@` pointing to Squarespace

### Step 4: Wait for DNS Propagation

- DNS changes can take **24-72 hours** to fully propagate
- Most changes appear within **30 minutes to 2 hours**
- You can check propagation status at: https://www.whatsmydns.net/

### Step 5: Enable HTTPS on GitHub (After DNS Propagates)

1. Go to https://github.com/SatinderSidhu/satindersidhuprofile/settings/pages
2. Wait for the DNS check to pass (may show "DNS check in progress")
3. Once verified, check **Enforce HTTPS**
4. Your site will be available at https://www.satindersidhu.com

## Verification

You can verify your DNS configuration using these commands:

```bash
# Check CNAME record
dig www.satindersidhu.com CNAME

# Check A records
dig satindersidhu.com A
```

## Expected Results

After configuration:
- `www.satindersidhu.com` → Your GitHub Pages portfolio
- `satindersidhu.com` → Redirects to `www.satindersidhu.com`
- Both will use HTTPS for secure connection

## Troubleshooting

### "Domain's DNS record could not be retrieved"
- Wait longer for DNS propagation
- Verify CNAME record is correct: `satindersidhu.github.io`

### "CNAME already taken"
- Make sure you pushed the CNAME file to your repository
- Verify no one else is using this domain on GitHub

### Certificate Error
- Wait for DNS to fully propagate before enabling HTTPS
- GitHub will automatically provision an SSL certificate

## Alternative: Using Squarespace Forwarding (Quick Option)

If you don't want to wait for DNS propagation, you can use domain forwarding:

1. In Squarespace, go to **Settings** > **Domains**
2. Click on **satindersidhu.com**
3. Enable **Domain Forwarding**
4. Forward to: `https://satindersidhu.github.io/satindersidhuprofile/`
5. Enable **301 Permanent Redirect**

Note: This method will show the GitHub Pages URL in the browser address bar.

## Support Links

- [GitHub Pages Custom Domain Documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Squarespace DNS Documentation](https://support.squarespace.com/hc/en-us/articles/360002101888)
