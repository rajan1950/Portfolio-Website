n# Installation Instructions

## New Features Added

1. **Scroll Animations** - Smooth fade-in/slide-up animations on scroll using Framer Motion
2. **Resume Download Button** - Downloadable PDF resume button in the Home section

## Step 1: Install Dependencies

Run the following command to install Framer Motion:

```bash
npm install
```

This will install `framer-motion` which is required for the scroll animations.

## Step 2: Add Your Resume PDF

1. Create a PDF file of your resume
2. Place it in the `public` folder
3. Name it `resume.pdf` (or update the path in `data/personal-info.ts`)

The resume file should be located at: `public/resume.pdf`

## Step 3: Run the Development Server

```bash
npm run dev
```

## Features Implemented

### Scroll Animations
- All sections now have smooth fade-in and slide-up animations when scrolling
- Animations trigger when sections come into view
- Each element has a slight delay for a cascading effect
- Uses Framer Motion for smooth, performant animations

### Resume Download Button
- Prominent download button in the Home section
- Gradient styling matching your portfolio theme
- Hover effects and smooth transitions
- Opens/downloads your resume PDF when clicked

## Customization

### Adjust Animation Speed
Edit `components/ScrollAnimation.tsx`:
- Change `duration: 0.6` to adjust animation speed
- Modify `delay` values in components to change timing

### Change Resume Path
Edit `data/personal-info.ts`:
```typescript
resume: "/your-resume-filename.pdf",
```

## Troubleshooting

If you see errors about framer-motion:
- Make sure you ran `npm install`
- Restart your development server
- Clear `.next` folder and rebuild

If resume download doesn't work:
- Check that the PDF file exists in the `public` folder
- Verify the filename matches in `personal-info.ts`
- Ensure the file is a valid PDF

