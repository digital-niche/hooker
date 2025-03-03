# Hooker - GoHighLevel Integration

## Overview
Hooker is a **dark-themed** web application integrating **GoHighLevel (GHL)** with **Google Apps Script** and **Meta Business Login**. It logs leads, contacts, appointments, and other data into Google Sheets while enabling business authentication with Meta.

## Features
- **GoHighLevel API Integration** (Fetch leads, contacts, and opportunities)
- **Meta Business Login** (Connect Facebook/Instagram Business Assets)
- **Google Sheets Backend** (Log GHL data in real-time)
- **Custom Location-Based Themes** (Dark red default, configurable per location)

---

## 1️⃣ Getting Started
### **Clone the Repository**
If Codespaces doesn’t allow opening an empty repo, initialize it manually:
```sh
mkdir hooker
cd hooker
echo "# Hooker" >> README.md
git init
git add README.md
git commit -m "Initial commit"
git branch -M main
git remote add origin git@github.com:digital-niche/hooker.git
git push -u origin main
```

Now, open **GitHub Codespaces** from your repository.

---

## 2️⃣ Project Setup
### **Inside GitHub Codespaces, run:**
```sh
git clone git@github.com:digital-niche/hooker.git
cd hooker
npm init -y
npm install next react react-dom
```

Then install dependencies:
```sh
npm install framer-motion @shadcn/ui next-auth
```

---

## 3️⃣ Connect Google Apps Script Backend
Modify the API calls to pull data from your **Google Apps Script Web App**:

### **Example API Call to Fetch GHL Data**
Edit `fetchGhlData` function in your app:
```javascript
const fetchGhlData = () => {
  fetch('https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec')
    .then(res => res.json())
    .then(data => setGhlData(data));
};
```

Ensure your **Google Apps Script project is deployed as a web app** and allows external requests.

---

## 4️⃣ Meta Business Login Integration
Modify `handleLogin` in React to use your **Meta App Credentials**:
```javascript
const handleLogin = () => {
  window.location.href = `https://www.facebook.com/v17.0/dialog/oauth?client_id=YOUR_FB_APP_ID&redirect_uri=YOUR_REDIRECT_URL&scope=business_management,pages_read_engagement,ads_management,instagram_basic`;
};
```

---

## 5️⃣ Deploying the App
### **Push Changes to GitHub**
```sh
git add .
git commit -m "Initialized Hooker project with Next.js and APIs"
git push origin main
```

### **Start Development Server**
```sh
npm run dev
```
Go to **http://localhost:3000** to test the app.

---

## 6️⃣ Webhooks for Real-Time Sync
To sync **GoHighLevel data**, set up **webhooks**:
1. **Go to GoHighLevel** → **Settings** → **API & Webhooks**
2. Add a **Webhook Endpoint**:
   ```
   https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec
   ```
3. Set it to trigger on:
   - Contact Created
   - Appointment Scheduled
   - Opportunity Created
   - Call Logged

---

## 7️⃣ Next Steps
- ✅ **Deploy Google Apps Script Web App**
- ✅ **Set Up CI/CD for Google Apps Script Deployments**
- ✅ **Test Meta Login & GHL Sync**

For further improvements, let me know! 🚀

