# Portfolio Website

A modern, responsive portfolio website built with Next.js, TypeScript, Tailwind CSS, and Framer Motion. Features smooth scroll animations, dark/light mode toggle, and a premium design.

## ✨ Features

- 🎨 **Modern Design** - Clean, professional UI with premium styling
- 🌓 **Dark/Light Mode** - Toggle between themes with smooth transitions
- 🎬 **Scroll Animations** - Smooth fade-in and slide-up animations using Framer Motion
- 📱 **Fully Responsive** - Optimized for mobile, tablet, and desktop
- 🎯 **Premium Navigation** - Right-aligned navigation with gradient buttons
- 📄 **Resume Download** - One-click resume download button
- 📸 **Profile Photo** - Circular profile picture display
- ⚡ **Fast Performance** - Optimized with Next.js Image component
- 🎨 **Gradient Effects** - Beautiful gradient backgrounds and buttons

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ installed
- npm or yarn package manager

### Installation

1. **Install dependencies:**
```bash
npm install
```

2. **Update your personal information:**
   - Open `data/personal-info.ts`
   - Replace all placeholder content with your actual information

3. **Add your assets:**
   - **Resume:** Place your resume PDF in `public/resume.pdf`
   - **Photo:** Place your photo in `public/photo.jpg` (or update path in `personal-info.ts`)

4. **Run the development server:**
```bash
npm run dev
```

5. **Open your browser:**
   - Navigate to [http://localhost:3000](http://localhost:3000)

## 📁 Project Structure

```
rajandobariya.com/
├── app/
│   ├── globals.css          # Global styles and animations
│   ├── layout.tsx           # Root layout with metadata
│   └── page.tsx             # Main page component
├── components/
│   ├── Home.tsx             # Hero section with photo and resume button
│   ├── Navigation.tsx       # Navigation bar with dark mode toggle
│   ├── Summary.tsx          # About/Summary section
│   ├── Projects.tsx         # Projects showcase
│   ├── Skills.tsx           # Skills and technologies
│   ├── Education.tsx        # Education history
│   ├── Experience.tsx       # Work experience & certificates
│   ├── Links.tsx            # Social media links
│   └── ScrollAnimation.tsx  # Reusable scroll animation component
├── data/
│   └── personal-info.ts     # All your personal information
├── public/
│   ├── resume.pdf           # Your resume (add your file)
│   ├── photo.jpg            # Your photo (add your file)
│   └── README.md            # Instructions for assets
└── package.json
```

## 🎨 Customization

### Personal Information

Edit `data/personal-info.ts` to update:

- **Header Section:**
  - `status` - Your availability status (e.g., "Open to Work")
  - `headline` - Your job title/role
  - `name` - Your full name
  - `photo` - Path to your photo (default: "/photo.jpg")

- **Contact Information:**
  - `email`, `linkedin`, `phone`, `location`

- **Content Sections:**
  - `summary` - Bio/about paragraphs
  - `projects` - Project details with descriptions, tech stack, links
  - `skills` - Concepts, technologies, and languages with proficiency
  - `education` - Educational background
  - `experience` - Work experience and certificates
  - `socialLinks` - Social media URLs
  - `resume` - Path to resume PDF (default: "/resume.pdf")

### Adding Projects

Add a new project to the `projects` array in `data/personal-info.ts`:

```typescript
{
  title: "Project Name",
  description: "Brief project description",
  objective: "Main objective of the project",
  features: ["Feature 1", "Feature 2", "Feature 3"],
  techStack: ["React", "TypeScript", "Tailwind CSS"],
  skills: ["Frontend Development", "UI/UX Design"],
  github: "https://github.com/username/project",
  liveDemo: "https://project-demo.com" // Optional
}
```

### Styling

Customize the design:

- **Tailwind Config:** `tailwind.config.ts` - Theme colors, breakpoints
- **Global Styles:** `app/globals.css` - Custom CSS, scrollbar styling
- **Component Styles:** Edit individual component files for specific styling

### Animation Customization

Edit `components/ScrollAnimation.tsx` to adjust:
- Animation duration (default: 0.6s)
- Animation direction (up, down, left, right)
- Viewport trigger margins

## 🎯 Features Explained

### Scroll Animations

All sections fade in and slide up smoothly when scrolling into view. Uses Framer Motion for performant animations.

### Dark/Light Mode

Toggle button in the navigation bar. Theme preference is saved in localStorage.

### Responsive Design

- **Mobile:** < 640px - Single column, compact layout
- **Tablet:** 640px - 1023px - Two columns, adjusted spacing
- **Desktop:** 1024px+ - Full multi-column layout

### Navigation

- Right-aligned premium buttons with gradient effects
- Active section highlighting
- Smooth scroll to sections
- Mobile hamburger menu

## 📦 Dependencies

- **Next.js 15** - React framework
- **React 18** - UI library
- **TypeScript** - Type safety
- **Tailwind CSS** - Utility-first CSS
- **Framer Motion** - Animation library

## 🛠️ Build for Production

```bash
npm run build
npm start
```

## 🚀 Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Import repository in [Vercel](https://vercel.com)
3. Deploy automatically

### Netlify

1. Build command: `npm run build`
2. Publish directory: `.next`
3. Push to GitHub and connect to Netlify

### Other Platforms

This Next.js app can be deployed to any platform that supports Node.js:
- AWS Amplify
- DigitalOcean App Platform
- Railway
- Render














