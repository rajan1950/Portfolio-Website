# How to Run Your Portfolio Website

## Step-by-Step Instructions

### Step 1: Open Terminal/Command Prompt

- **Windows**: Press `Win + R`, type `cmd` or `powershell`, press Enter
- **Mac/Linux**: Open Terminal app

### Step 2: Navigate to Your Project Folder

```bash
cd E:\rajandobariya.com
```

### Step 3: Install Dependencies (if not already installed)

```bash
npm install
```

**Note**: If you see `node_modules` folder already exists, you can skip this step. But it's safe to run it anyway.

### Step 4: Run the Development Server

```bash
npm run dev
```

You should see output like:
```
▲ Next.js 15.x.x
- Local:        http://localhost:3000
- Ready in X.Xs
```

### Step 5: Open Your Browser

1. Open your web browser (Chrome, Firefox, Edge, etc.)
2. Go to: **http://localhost:3000**
3. You should see your portfolio website!

### Step 6: Make Changes

- Edit `data/personal-info.ts` to add your information
- The page will automatically reload when you save changes
- Keep the terminal running while developing

### Step 7: Stop the Server

When you're done:
- Press `Ctrl + C` in the terminal to stop the server

---

## Troubleshooting

### If you get "npm is not recognized":
- Install Node.js from: https://nodejs.org/
- Restart your terminal after installation

### If port 3000 is already in use:
- The terminal will show an error
- Close other applications using port 3000, or
- Run: `npm run dev -- -p 3001` (uses port 3001 instead)

### If you see errors about missing modules:
- Run: `npm install` again
- Delete `node_modules` folder and run `npm install` again

### If the page shows errors:
- Check the terminal for error messages
- Make sure all files are saved correctly
- Verify `data/personal-info.ts` has valid content

---

## Quick Commands Reference

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Check for errors
npm run lint
```

---

## Next Steps After Running

1. **Add Your Information**: Edit `data/personal-info.ts`
2. **Customize Design**: Edit `app/globals.css` or `tailwind.config.ts`
3. **Deploy**: Push to GitHub and deploy on Vercel (free!)

