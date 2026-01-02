# Quick Start Guide

## Step 1: Install Dependencies

Open your terminal in the project directory and run:

```bash
npm install
```

## Step 2: Add Your Personal Information

Open `data/personal-info.ts` and replace all the placeholder content with your actual information:

### Required Updates:

1. **Header Section:**
   - `status`: Your availability status (e.g., "Open to Work")
   - `headline`: Your job title/role
   - `name`: Your full name

2. **Contact Information:**
   - `email`: Your email address
   - `linkedin`: Your LinkedIn profile URL (without https://)
   - `phone`: Your phone number
   - `location`: Your city, state, country

3. **Summary:**
   - Replace the two paragraphs with your own bio/summary

4. **Projects:**
   - Update existing projects or add new ones
   - Each project needs: title, description, objective, features, techStack, skills, github, liveDemo

5. **Skills:**
   - Update `concepts` array with your skill concepts
   - Update `technologies` array with your tech stack (you can change icons)

6. **Languages:**
   - Update with languages you speak and proficiency percentages

7. **Education:**
   - Add your educational background

8. **Experience:**
   - Add your work experience and certificates

9. **Social Links:**
   - Update all your social media URLs

## Step 3: Run the Development Server

```bash
npm run dev
```

Then open [http://localhost:3000](http://localhost:3000) in your browser.

## Step 4: Customize (Optional)

- Colors: Edit `tailwind.config.ts` to change theme colors
- Styles: Edit `app/globals.css` for custom styling
- Layout: Modify components in the `components/` folder

## Step 5: Build for Production

When you're ready to deploy:

```bash
npm run build
npm start
```

## Deployment

The easiest way to deploy is using Vercel:

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Import your GitHub repository
4. Deploy!

Your portfolio will be live in minutes! 🚀

