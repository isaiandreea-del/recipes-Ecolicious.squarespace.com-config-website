# Ecolicious: connect to Squarespace and take payments

This guide has two parts: **A. Connect your Squarespace site and the recipe app** and **B. Sell Premium and unlock it for buyers**. Prices and plan rules change, so each section says what to double-check in your Squarespace account.

## The idea in one picture

- **Squarespace** is your main website and your shop (it takes the money).
- **The recipe app** (this folder) lives for free on **GitHub Pages**, at an address like `https://YOURNAME.github.io/ecolicious/`.
- Squarespace links to the app. After someone buys Premium, Squarespace emails them a file with a **link that unlocks Premium** on the app.

---

## Part A. Connect Squarespace and the app

### A1. Tell the app your Squarespace address
1. Open `index.html` in Notepad (or any text editor).
2. Search for `SQUARESPACE_URL`. You will find three settings near each other:

```
const SQUARESPACE_URL = "https://YOURSITE.squarespace.com";      // or your own domain
const PREMIUM_PRODUCT_URL = "https://YOURSITE.squarespace.com/premium";   // the page of your Premium product
const PREMIUM_CODES = ["ECO-7F3K9"];                              // your access codes (see Part B)
```
3. Save the file and upload it again to GitHub (Add file → Upload files → overwrite → Commit).
4. Result: the **Ecolicious logo** (top left) and the **"← Înapoi pe site"** button now open your Squarespace site. The **"Cumpără Premium"** button in the unlock window opens your Premium product page.

### A2. Link from Squarespace to the app
Pick one or more:

- **Menu item:** Pages → **+** → **Link** → paste the app address → give it a name (e.g. "Rețete") → turn on "Open in new tab" if you want people to keep your site open.
- **Button on a page:** edit the page → **+** → **Button** → paste the app address as the link.
- **Header button:** Website → Pages → Header → add a button (the option is named differently on different templates; search "header button" in Squarespace help).

This is the easiest and most reliable option and works on every plan.

### A3. (Optional) Show the app inside a Squarespace page
You can place the app *inside* a page with an iframe:

1. Edit the page → **+** → **Code** block.
2. Paste (change the address):
```
<iframe src="https://YOURNAME.github.io/ecolicious/" style="width:100%;height:1400px;border:0" title="Ecolicious"></iframe>
```
3. Save.

Notes: Squarespace only allows code blocks on a **Business-or-higher style plan** (on the current plan names this is Core and up, but check your plan). The app is tall, so an iframe is cramped on phones. For most people a normal link (A2) gives a nicer result.

### A4. (Optional) Use your own address, e.g. `recepte.yourdomain.com`
This makes the app look like part of your site. Do it **before you launch**: the app saves favourites and the Premium unlock inside the browser *per address*, so if you change the address later, people start from zero.

**In GitHub**
1. Repository → **Settings** → **Pages** → **Custom domain** → type `recepte.yourdomain.com` → Save.
2. Later, tick **Enforce HTTPS** (it appears after the DNS below is working).

**In Squarespace** (only if your domain is registered at Squarespace or connected through Nameserver Connect; otherwise do the same at the company where you bought the domain)
1. Open account.squarespace.com/domains → click your domain → **DNS**.
2. Add a record: Type **CNAME**, Host/Name **recepte**, Data/Points to **YOURNAME.github.io** (your GitHub user name, no `https://`, no folder). Keep the default TTL.
3. Enter your password when asked. Wait. Squarespace says changes can take **24 to 48 hours**.
4. Your app is then at `https://recepte.yourdomain.com`. Put that address in the links of A1 and A2.

---

## Part B. Sell Premium and unlock it

### B1. Set up payments in Squarespace
1. You need a Squarespace plan that can **sell products**. At the time of writing, all four commerce plans (Basic, Core, Plus, Advanced) can; Basic adds a ~2% transaction fee on top of the payment provider's fee. Look at **Pricing** in your Squarespace account for the real current numbers.
2. Connect a payment provider: Settings → **Payments** → connect **Stripe** and/or **PayPal** (and whatever else your country offers). Follow the on-screen verification (company/ID and IBAN).
3. Check taxes (Settings → **Taxes**) and your **Terms & conditions / refund policy** pages. For digital goods sold to consumers in the EU, the rules about the 14-day right of withdrawal and VAT apply; ask an accountant what applies to you. I am not a lawyer or an accountant.

### B2. Create the Premium product
1. Squarespace → **Products & services** → **Add product** → **Download**. (The product type cannot be changed later.)
2. Name: "Ecolicious Premium". Price: your choice. Description: list the features (nutrition values, substitutes, favourites, diet suggestions, avoiding ingredients).
3. Upload **one file**: your access file (see B3). Squarespace emails the buyer a download link automatically after checkout. The link expires after about 24 hours, and the buyer can request a new one from the same link; you can also resend it from the order in Orders.
4. Publish the product, copy its page address and paste it into `PREMIUM_PRODUCT_URL` (A1).

**Monthly or yearly instead of one-off?** A Download product is a one-time payment. If you want a subscription, check Squarespace's current options for recurring products or member areas (the availability depends on the plan), or sell "Premium for 1 year" as a one-time product and change the code every year.

### B3. The access file (what the buyer receives)
Create a small text file called `Ecolicious-Premium.txt` (Notepad → Save as):

```
Thank you for buying Ecolicious Premium!

Open this link on your phone or computer:
https://YOURNAME.github.io/ecolicious/?code=ECO-7F3K9

Premium unlocks automatically on that device.
If you use another device or browser, open the same link there.
Questions? hello@yourdomain.com
```

Upload this file in the Download product (B2). The app reads `?code=` from the link, checks it against `PREMIUM_CODES`, unlocks Premium, and then removes the code from the address bar. The person can also type the code by hand in the "Deblochează Premium" window.

### B4. Put the same code in the app
In `index.html`:
```
const PREMIUM_CODES = ["ECO-7F3K9"];
```
Use a code that is hard to guess (not `PREMIUM2026`). Save and upload to GitHub.

### B5. Test before going live
1. In Squarespace, create a **100% discount code** (Marketing → Discounts) so you can run a free test order.
2. Buy the product with that code on your own site, open the email, download the file, click the link, and confirm Premium unlocks.
3. Test on a phone too. Then delete the discount code or set an end date.

### B6. Be aware of this limit (important)
GitHub Pages is a *static* host. It cannot truly hide files, so Premium is a **soft lock**:
- Everyone who buys gets the **same code**, and a buyer could share the link. A technical visitor could also read `premium.json` directly.
- Practical ways to limit it: change the code from time to time (add the new code to `PREMIUM_CODES`, upload the new file in the product, and remove the old code). People who already unlocked stay unlocked on their device, but a leaked code stops working for new people.
- If Premium becomes a real income stream, the proper upgrade is **one unique code (or a login) per buyer**, checked by a small free service (for example Firebase or Supabase with a Stripe webhook). I can build that for you later.

### B7. What to do each time someone buys
Nothing: Squarespace sends the file automatically. If someone says they did not get the email, open the order in **Orders** and resend it.

---

## Quick checklist
- [ ] App is online on GitHub Pages
- [ ] `SQUARESPACE_URL` filled in, logo opens your site
- [ ] Link/button to the app on your Squarespace site
- [ ] Payments connected, taxes and policies set
- [ ] Download product "Ecolicious Premium" with the access file
- [ ] `PREMIUM_PRODUCT_URL` and `PREMIUM_CODES` filled in and uploaded
- [ ] Test order done on desktop and phone

## Sources used
- Squarespace: [Adding custom DNS records to your Squarespace managed domain](https://support.squarespace.com/hc/en-us/articles/360002101888-Adding-custom-DNS-records-to-your-Squarespace-managed-domain)
- [How to add an iframe to Squarespace](https://squarestyle.squarespace.com/tutorials/add-iframe-to-squarespace) (Code block, Business-tier-or-higher)
- [How to sell digital downloads on Squarespace](https://www.jpkdesignco.com/blog/how-to-sell-digital-downloads-squarespace) (Download product, emailed link, 300 MB limit, one file per product)
- [Squarespace pricing 2026 overview](https://www.websitebuilderexpert.com/website-builders/squarespace/squarespace-pricing/) (plans and fees; third-party, so confirm in your account)
