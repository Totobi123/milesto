# Environment Variables Setup for Netlify Deployment

This guide will help you set up the required API keys and environment variables for your Miles app to work properly on Netlify.

## Required Environment Variables

Your app needs these environment variables to function properly:

### 1. ETHERSCAN_API_KEY
**Purpose:** For checking crypto wallet balances (Ethereum and BNB Smart Chain)
**Where to get it:** https://etherscan.io/apis
**Steps:**
1. Go to https://etherscan.io/apis
2. Create a free account
3. Go to "API Keys" section
4. Create a new API key
5. Copy the API key (it looks like: `ABC123DEF456GHI789JKL012MNO345`)

### 2. FLUTTERWAVE_SECRET_KEY
**Purpose:** For Nigerian bank account verification and bank list
**Where to get it:** https://flutterwave.com
**Steps:**
1. Go to https://flutterwave.com and create a business account
2. Complete the verification process
3. Go to your dashboard → Settings → API Keys
4. Copy the **Secret Key** (starts with `FLWSECK-` followed by a long string)
5. **Important:** Use the **Live** secret key for production, or **Test** key for testing

## Setting Up Environment Variables in Netlify

### Method 1: Via Netlify Dashboard (Recommended)
1. **Login to Netlify:** Go to https://netlify.com and log in
2. **Select Your Site:** Click on your deployed site
3. **Go to Site Settings:** Click "Site settings" button
4. **Navigate to Environment Variables:** In the left sidebar, click "Environment variables"
5. **Add Variables:** Click "Add variable" and add each one:

   **Variable 1:**
   - Key: `ETHERSCAN_API_KEY`
   - Value: Your Etherscan API key (e.g., `ABC123DEF456GHI789JKL012MNO345`)

   **Variable 2:**
   - Key: `FLUTTERWAVE_SECRET_KEY`
   - Value: Your Flutterwave secret key (e.g., `FLWSECK-BB7F6C1A6C4F7A8E9D...`)

6. **Save Changes:** Click "Save" after adding each variable
7. **Redeploy:** Trigger a new deployment for changes to take effect

### Method 2: Via Netlify CLI
If you have Netlify CLI installed:

```bash
# Install Netlify CLI if you haven't
npm install -g netlify-cli

# Login to Netlify
netlify login

# Set environment variables
netlify env:set ETHERSCAN_API_KEY "your_etherscan_api_key_here"
netlify env:set FLUTTERWAVE_SECRET_KEY "your_flutterwave_secret_key_here"

# Deploy with new environment variables
netlify deploy --prod
```

## Testing Your Setup

After setting up the environment variables:

1. **Redeploy your site** (environment variables only take effect after deployment)
2. **Test the API endpoints:**
   - Crypto balance: `https://your-site.netlify.app/api/crypto/balance?address=0x742d35Cc6639C0532fEb2E7DeE656853fAC19D8B&chainid=1`
   - Bank verification: Make a POST request to `https://your-site.netlify.app/api/verify_account` with account details
   - Banks list: `https://your-site.netlify.app/api/banks`

## Security Notes

⚠️ **Important Security Guidelines:**

1. **Never share your API keys** publicly or commit them to your code repository
2. **Use test keys during development** and live keys only for production
3. **Regularly rotate your API keys** for better security
4. **Monitor your API usage** to detect any unusual activity

## Troubleshooting

### Common Issues:

**❌ "API key not found" errors:**
- Check that environment variable names are exactly: `ETHERSCAN_API_KEY` and `FLUTTERWAVE_SECRET_KEY`
- Verify you redeployed after adding environment variables
- Check Netlify dashboard to confirm variables are set

**❌ "Service unavailable" errors:**
- Verify your API keys are valid and active
- Check your Flutterwave account status
- Ensure you're using the correct key type (test vs live)

**❌ Bank verification not working:**
- Make sure your Flutterwave account is fully verified
- Check that you're using the live secret key for production
- Verify the bank codes are correct (Nigerian bank codes)

### Support
If you continue to have issues, check:
1. Your Netlify function logs for detailed error messages
2. Your API provider dashboards for usage limits or account issues
3. Contact support for your API providers if needed

## Next Steps

Once environment variables are set up:
1. Your crypto balance checking will work for Ethereum and BNB Smart Chain
2. Bank account verification will work for Nigerian banks
3. The bank list will be fetched from Flutterwave
4. All API endpoints will be available at `/api/*` routes on your Netlify domain