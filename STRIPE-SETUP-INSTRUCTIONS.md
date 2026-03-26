# Stripe Integration Setup Instructions

## 🚀 Quick Setup Guide

### Step 1: Deploy Cloudflare Worker

1. **Go to Cloudflare Workers:** https://workers.cloudflare.com
2. **Create a new Worker** (give it a name like `mdviewer-payments`)
3. **Copy the code** from `cloudflare-worker.js` into the worker editor
4. **Set Environment Variables** in the worker settings:
   - `STRIPE_SECRET_KEY`: Your Stripe secret key (sk_test_... or sk_live_...)
   - `STRIPE_WEBHOOK_SECRET`: (Optional) Your webhook signing secret
5. **Deploy the worker**
6. **Note your worker URL** (e.g., `https://mdviewer-payments.your-username.workers.dev`)

### Step 2: Update Your Website

1. **Edit `pricing.html`** and replace the placeholder URL:
   
   Change this line (line 415):
   ```javascript
   fetch('https://mdviewer-payments.YOUR_USERNAME.workers.dev/api/create-checkout', {
   ```
   
   To your actual worker URL:
   ```javascript
   fetch('https://your-actual-worker-url.workers.dev/api/create-checkout', {
   ```

2. **Test in Stripe test mode first!**

### Step 3: Test Everything

1. **Visit your pricing page**
2. **Click a payment tier** ($1, $2, $5, or $10)
3. **You should be redirected to Stripe Checkout**
4. **Use Stripe test card:** 4242 4242 4242 4242
5. **Complete the test payment**
6. **Verify you land on the download-access page**

### Step 4: Go Live

1. **Switch Stripe to live mode** in your Stripe dashboard
2. **Update the `STRIPE_SECRET_KEY`** in Cloudflare Worker (use live key)
3. **Test with a small real payment** ($1)
4. **Monitor for any issues**

## 🔒 Security Notes

- **Never share your secret keys publicly**
- **Test mode keys start with `sk_test_`**
- **Live mode keys start with `sk_live_`**
- **Keep your webhook secret secure**

## 🎯 What This Gives You

✅ **Real Stripe payments** for your support tiers
✅ **Automatic redirects** to thank you page
✅ **Professional checkout experience**
✅ **Global payment support** (cards, digital wallets)
✅ **Secure payment processing** (PCI compliant)

## 🛠️ Your Current Setup

- **Pricing page:** ✅ Updated with real Stripe integration
- **Download page:** ✅ Updated for version 1.4.1.5
- **Cloudflare Worker:** ✅ Ready to deploy
- **Error handling:** ✅ Graceful fallbacks included

## 📋 What You Need to Provide

1. **Your Cloudflare Worker URL** (after you create it)
2. **Your Stripe secret key** (keep this secure!)

## 🆘 If You Need Help

- **Stripe Test Cards:** https://stripe.com/docs/testing#cards
- **Cloudflare Workers Docs:** https://developers.cloudflare.com/workers/
- **My Email:** Just let me know if you run into any issues!

---

**Ready?** The code is all set - you just need to:
1. Create the Cloudflare Worker
2. Add your Stripe key
3. Update the worker URL in pricing.html
4. Test and go live!
