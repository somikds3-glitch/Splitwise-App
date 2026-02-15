# SplitWise - Expense Splitting App

A collaborative expense splitting application with **real-time syncing** powered by Firebase. Split expenses with friends and groups, track balances, and settle up easily!

![SplitWise Logo](assets/images/logo.png)

## ✨ Features

- 🔥 **Real-Time Sync** - See expenses instantly across all devices (with Firebase)
- 💰 **Split Expenses** - Multiple split methods (equal, exact amounts, percentage)
- 👥 **Group Management** - Create groups for different occasions
- 👤 **Friend Management** - Add and track friends
- 📊 **Balance Tracking** - See who owes whom at a glance
- 🔄 **Debt Simplification** - Minimize number of payments needed
- 💸 **Settlement Tracking** - Record payments to update balances
- 📜 **Expense History** - View all past expenses
- 📱 **Responsive Design** - Works on desktop and mobile
- 💾 **Export/Import** - Backup and restore your data
- 📴 **Offline Support** - Works without internet (localStorage fallback)

## 🚀 Quick Start

### Option 1: With Real-Time Syncing (Recommended)

**Setup Firebase once** (~5 minutes) to enable real-time syncing where everyone sees expenses instantly:

1. **Follow the [Firebase Setup Guide](FIREBASE_SETUP.md)** to:
   - Create a free Firebase project
   - Get your Firebase configuration
   - Add it to `js/config.js`

2. **Start the local server:**
   ```bash
   cd /Users/somikdas/.gemini/antigravity/scratch/splitwise-app
   python3 -m http.server 8000
   ```

3. **Open `http://localhost:8000`** in your browser

4. ✅ Look for: **"Connected! Real-time sync enabled 🚀"**

### Option 2: Offline Mode (No Setup)

Skip Firebase setup and use localStorage only (data not shared between users):

1. **Comment out Firebase config** in `js/config.js`:
   ```javascript
   // FIREBASE: null,
   ```

2. **Start the server:**
   ```bash
   python3 -m http.server 8000
   ```

3. Open `http://localhost:8000`

4. ⚠️ You'll see: "Running in offline mode"

---

## 🔥 Firebase vs localStorage

| Feature | With Firebase 🔥 | Without Firebase 📴 |
|---------|------------------|---------------------|
| **Real-time sync** | ✅ Yes | ❌ No |
| **Shared data** | ✅ Everyone sees same expenses | ❌ Each person has separate data |
| **Setup required** | 5 min one-time setup | ✅ None |
| **Cost** | ✅ Free forever (normal use) | ✅ Free |
| **Offline support** | ✅ Yes (cached) | ✅ Yes |
| **Use case** | Collaborative expense tracking | Personal tracking only |

**Recommendation**: Use Firebase for the real Splitwise experience! 🚀

---

## 📖 Using the App

### Adding Friends
1. Go to **Friends** tab
2. Click **Add Friend**
3. Enter name and email
4. Friend appears for everyone (if using Firebase)

### Creating Groups
1. Go to **Groups** tab
2. Click **Create Group**
3. Name your group and select members
4. Group is created and synced

### Adding Expenses
1. Go to **Add Expense** tab
2. Fill in details:
   - Description (e.g., "Dinner")
   - Amount
   - Category
   - Group
   - Who paid
   - Participants
   - Split type (Equal/Exact/Percentage)
3. Expense appears **instantly** for everyone! 🎉

### Settling Up
1. Go to **Settle Up** tab
2. View simplified payment suggestions
3. When payment is made, click **Paid**
4. Balances update in real-time

---

## 🌐 Deploying to GitHub Pages

### Step 1: Make Sure Firebase is Configured

Before deploying, set up Firebase (see [Firebase Setup Guide](FIREBASE_SETUP.md)):
- ✅ Firebase config added to `config.js`
- ✅ Tested locally and seeing "Connected!" message

### Step 2: Push to GitHub

```bash
cd /Users/somikdas/.gemini/antigravity/scratch/splitwise-app
git init
git add .
git commit -m "Initial commit: SplitWise with Firebase"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/splitwise-app.git
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**, select **main** branch
4. Click **Save**
5. Your site will be live at: `https://YOUR_USERNAME.github.io/splitwise-app/`

### Step 4: Share with Friends!

Send them the URL and everyone will see the same expenses in real-time! 🎉

---

## 💾 Data Storage

### How Data Works

**With Firebase:**
- 📡 Data stored in **Firebase Firestore** (cloud database)
- 🔄 **Real-time sync** across all devices
- 💾 **Cached locally** for offline access
- 🌍 **Everyone with the URL** shares the same data

**Without Firebase:**
- 💻 Data stored in **browser's localStorage**
- 🔒 Private to your browser only
- ❌ No sync between devices or users

### Export/Import

1. **Export**: Click **💾 Export** button → Downloads JSON file
2. **Import**: Click **📂 Import** button → Select JSON file

**Use cases:**
- Backup your data
- Transfer data between devices (if not using Firebase)
- Restore deleted data

---

## 🛠️ Technology Stack

- **Frontend**: Vanilla JavaScript (ES6+)
- **Styling**: Custom CSS with modern design
- **Storage**: Firebase Firestore + localStorage fallback
- **Real-time**: Firebase real-time listeners
- **Deployment**: GitHub Pages (static hosting)

---

## 🔒 Privacy & Security

**With Firebase:**
- Data stored in your Firebase project
- Currently using test mode (anyone can read/write)
- For production: implement proper authentication & security rules
- See [Firebase Setup Guide](FIREBASE_SETUP.md) for security options

**Without Firebase:**
- Data stored in your browser only
- Complete privacy - no one else can access it

---

## 💡 Pro Tips

- 📤 **Export regularly** to keep backups
- 🔥 **Use Firebase** for the best collaborative experience
- 📴 **Works offline** - data syncs when you're back online
- 🌐 **Deploy to GitHub Pages** and share the URL with friends
- 💸 **Completely free** for normal use (Firebase free tier is generous)

---

## 🐛 Troubleshooting

### "Running in offline mode" message
- Firebase not configured in `config.js`
- Follow [Firebase Setup Guide](FIREBASE_SETUP.md) to set it up
- Or ignore this if you want offline-only mode

### Expenses not syncing between users
- Make sure Firebase is configured
- Check browser console for errors
- Verify Firestore database is created in Firebase Console

### App not loading
- Check that local server is running
- Clear browser cache and reload
- Check browser console (F12) for errors

---

## 📚 Additional Documentation

- **[Firebase Setup Guide](FIREBASE_SETUP.md)** - Detailed Firebase setup instructions
- **[Deployment Guide](DEPLOYMENT.md)** - More deployment options

---

## 📝 License

MIT License - feel free to use and modify!

---

**Enjoy splitting expenses with friends! 🎉**
