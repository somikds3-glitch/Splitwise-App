# Firebase Setup Guide 🔥

Follow these steps to enable **real-time syncing** for your Splitwise app!

## ⏱️ Time Required: ~5 minutes

---

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **"Add project"** or **"Create a project"**
3. Enter a project name: `splitwise-app` (or any name you prefer)
4. Click **Continue**
5. Disable Google Analytics (not needed for this app)
6. Click **Create project**
7. Wait for project creation, then click **Continue**

---

## Step 2: Set Up Firestore Database

1. In the Firebase Console, click **"Firestore Database"** in the left sidebar
2. Click **"Create database"**
3. Select **"Start in test mode"** (allows read/write for testing)
   - ⚠️ **Security warning**: Test mode is open to anyone! For production, implement proper security rules.
4. Choose a Firestore location (select closest to your users)
   - Example: `us-central1` or `asia-south1`
5. Click **"Enable"**
6. Wait for the database to be created

---

## Step 3: Get Your Firebase Configuration

1. In Firebase Console, click the **⚙️ gear icon** → **Project settings**
2. Scroll down to **"Your apps"** section
3. Click the **web icon** `</>` (it says "Add app")
4. Enter an app nickname: `Splitwise Web App`
5. **Don't** check "Also set up Firebase Hosting"
6. Click **"Register app"**
7. You'll see a code snippet with your config. It looks like:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyC...", 
  authDomain: "splitwise-app-xxxxx.firebaseapp.com",
  projectId: "splitwise-app-xxxxx",
  storageBucket: "splitwise-app-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

8. **Copy these values** (you'll need them in the next step)

---

## Step 4: Add Config to Your App

1. Open `js/config.js` in your code editor
2. Find the `FIREBASE` object (around line 10)
3. Replace the placeholder values with your actual Firebase config:

**Before:**
```javascript
FIREBASE: {
    apiKey: "YOUR_API_KEY_HERE",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
},
```

**After (with your values):**
```javascript
FIREBASE: {
    apiKey: "AIzaSyC...",
    authDomain: "splitwise-app-xxxxx.firebaseapp.com",
    projectId: "splitwise-app-xxxxx",
    storageBucket: "splitwise-app-xxxxx.appspot.com",
    messagingSenderId: "123456789",
    appId: "1:123456789:web:abcdef"
},
```

4. **Save the file**

---

## Step 5: Test the Setup

1. Start your local server:
   ```bash
   cd /Users/somikdas/.gemini/antigravity/scratch/splitwise-app
   python3 -m http.server 8000
   ```

2. Open `http://localhost:8000` in your browser

3. Check for success message:
   - ✅ You should see: **"Connected! Real-time sync enabled 🚀"**
   - ❌ If you see: "Running in offline mode..." → Check your config values

4. Open browser console (F12) to check for errors

---

## Step 6: Test Real-Time Syncing

### Test with Two Browser Windows:

1. **Open Chrome**: Go to `http://localhost:8000`
2. **Open Firefox** (or Chrome Incognito): Go to `http://localhost:8000`
3. In **Chrome**: Add a friend
4. Check **Firefox**: The friend should appear **instantly!** 🎉
5. In **Firefox**: Add an expense
6. Check **Chrome**: The expense should appear **instantly!** 🎉

If data syncs between browsers, **congratulations!** Firebase is working! 🚀

---

## 🌐 For GitHub Pages Deployment

When you deploy to GitHub Pages, **no changes needed!** The Firebase config works the same way.

Just make sure:
- ✅ Your Firebase config is in `config.js` **before** you push to GitHub
- ✅ Firebase security rules allow access (test mode is fine for personal use)

---

## 🔒 Security Rules (Optional - For Production)

By default, you're in **test mode** (anyone can read/write). For better security:

1. Go to **Firestore Database** in Firebase Console
2. Click **"Rules"** tab
3. Replace with these rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      // Allow read/write for now (can add auth later)
      allow read, write: if true;
    }
  }
}
```

For production apps with sensitive data, implement proper authentication!

---

## 💡 Tips

- **Free tier limits**: 50K reads/day, 20K writes/day (plenty for personal use)
- **Offline support**: App works even without internet (uses localStorage cache)
- **Export backups**: Click Export button regularly to save data
- **Multiple apps**: Can use same Firebase project for multiple apps

---

## 🐛 Troubleshooting

### "Running in offline mode" message
- Check that `config.js` has correct Firebase values
- Ensure no typos in the config
- Check browser console for detailed errors

### Data not syncing between browsers
- Make sure both browsers have internet
- Check Firestore rules allow read/write
- Open browser console and look for Firebase errors

### "Firebase not configured" error
- Verify `config.js` has `FIREBASE` object with all fields filled
- Check you saved the file after editing

---

## ✅ Success Checklist

- [ ] Firebase project created
- [ ] Firestore database enabled in test mode
- [ ] Firebase config copied to `config.js`
- [ ] App shows "Connected! Real-time sync enabled" message
- [ ] Data syncs between two browser windows
- [ ] Ready to share with friends! 🎉

---

**That's it! Your Splitwise app now has real-time syncing! 🚀**
