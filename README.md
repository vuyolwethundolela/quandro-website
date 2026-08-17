# QUANDRO – DJ & Producer Website
## Setup & Deployment Guide

---

## 📁 Folder Structure (set this up on your computer)

```
quandro-website/
├── index.html          ← your website (the file Claude gave you)
├── images/
│   └── hero.jpg        ← rename your photo to hero.jpg and put it here
└── README.md           ← this guide
```

---

## 🖼️ Adding Your Photo

1. Create a folder called `images` next to your `index.html`
2. Copy your DJ photo (the one you shared) into that folder
3. Rename it to `hero.jpg`
4. The website will automatically use it as the hero background AND the about section photo

---

## 🛠️ Tools You Need (all FREE)

### 1. VS Code (you already have this ✓)

### 2. Live Server Extension (for previewing locally)
- Open VS Code
- Click the **Extensions** icon on the left sidebar (looks like 4 squares)
- Search: `Live Server`
- Install by **Ritwick Dey**
- Right-click `index.html` → **"Open with Live Server"**
- Your website opens in your browser at `http://127.0.0.1:5500`

### 3. Node.js (needed for deployment tools)
- Download free from: https://nodejs.org (choose "LTS" version)
- Install it — this also installs `npm`

---

## 🌐 Deploying Your Website (FREE options)

### Option A: Netlify (Recommended — easiest)
1. Go to https://netlify.com and create a free account
2. Drag and drop your entire `quandro-website/` folder onto the Netlify dashboard
3. Your site goes live instantly at a URL like `quandro.netlify.app`
4. You can buy a custom domain (e.g. `quandro.co.za`) for ~R200/year

### Option B: GitHub Pages (also free)
1. Download GitHub Desktop: https://desktop.github.com
2. Create a free account at https://github.com
3. Create a new repository called `quandro-website`
4. Drag your files in
5. Go to Settings → Pages → set source to `main` branch
6. Your site will be at `yourusername.github.io/quandro-website`

---

## 💳 Setting Up Payments (Track Sales)

The website uses a placeholder checkout. To receive real payments:

### PayFast (South African — recommended)
1. Register at https://www.payfast.co.za (free account)
2. Get your **Merchant ID** and **Merchant Key**
3. Replace the `submitPayment()` function in `index.html` with a PayFast form POST:

```html
<!-- Replace the submitPayment() function body with this -->
<form action="https://www.payfast.co.za/eng/process" method="post">
  <input type="hidden" name="merchant_id" value="YOUR_MERCHANT_ID">
  <input type="hidden" name="merchant_key" value="YOUR_MERCHANT_KEY">
  <input type="hidden" name="amount" value="49.00">
  <input type="hidden" name="item_name" value="Track Download">
  <input type="hidden" name="return_url" value="https://yourdomain.com/thank-you">
  <input type="hidden" name="cancel_url" value="https://yourdomain.com">
  <button type="submit">Pay with PayFast</button>
</form>
```

---

## 📧 Setting Up the Booking Form (Free Email Submissions)

### Formspree (easiest — free for 50 submissions/month)
1. Go to https://formspree.io and create a free account
2. Create a new form — you'll get a URL like `https://formspree.io/f/abcdefgh`
3. In `index.html`, find the `submitBooking()` function and add this:

```javascript
// Add inside submitBooking() after the validation check
const formData = {
  name: document.getElementById('bFname').value + ' ' + document.getElementById('bLname').value,
  email: document.getElementById('bEmail').value,
  phone: document.getElementById('bPhone').value,
  date: document.getElementById('bDate').value,
  eventType: document.getElementById('bEventType').value,
  venue: document.getElementById('bVenue').value,
  notes: document.getElementById('bNotes').value
};
fetch('https://formspree.io/f/YOUR_FORM_ID', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(formData)
});
```

---

## 🎵 Uploading Content

All uploads happen **directly on the website** (no backend needed for local uploads):

- **Gallery photos**: Scroll to Gallery → click the upload zone → select photos
- **Mixes**: Scroll to Mixes → click upload → select MP3, WAV, or MP4 files
- **Tracks for sale**: Scroll to Music → click upload → select MP3/WAV files

> ⚠️ **Note**: Files uploaded via the website are stored in your browser temporarily.
> For permanent storage, host your files on a service like:
> - **Cloudinary** (free tier) for images/videos: https://cloudinary.com
> - **Dropbox** or **Google Drive** for audio (generate shareable links)
> - **SoundCloud** (free) for streaming mixes — embed the player code

---

## 🔗 Social Media Links

In `index.html`, find the `socials` section and update the `href="#"` with your actual links:

```html
<a class="social-btn" href="https://instagram.com/yourhandle" ...>
<a class="social-btn" href="https://facebook.com/yourpage" ...>
<a class="social-btn" href="https://soundcloud.com/yourprofile" ...>
<a class="social-btn" href="https://tiktok.com/@yourhandle" ...>
```

---

## 📞 Contact Details

In `index.html`, update these lines with your real details:

```html
<a href="mailto:bookings@quandro.co.za">bookings@quandro.co.za</a>
<a href="tel:+27000000000">+27 (0)00 000 0000</a>
```

---

## ✏️ Updating Bio Text

Find the `#about` section in `index.html` and replace the `<p>` paragraph text with your own bio.

---

## 🎨 Customising Track Prices

Find each `track-row` in the `#music` section. Change `R49` to whatever price you want per track. Also update the `onclick="openPayModal('Track Name','49')"` — change `49` to match.

---

## ✅ Quick Checklist Before Going Live

- [ ] Added hero.jpg to the images/ folder
- [ ] Updated email address
- [ ] Updated phone number
- [ ] Updated social media links
- [ ] Replaced placeholder bio with your real bio
- [ ] Set up PayFast account for payments
- [ ] Set up Formspree for booking form emails
- [ ] Deployed to Netlify or GitHub Pages
- [ ] (Optional) Bought a custom .co.za domain

---

Built for QUANDRO — Cape Town DJ & Producer 🎧
