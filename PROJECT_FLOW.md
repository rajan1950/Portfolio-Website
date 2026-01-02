# Project Details + Flow Chart

This project is a **portfolio website** built with:
- **Next.js (App Router)**: pages and API routes live under `app/`
- **React**: UI components under `components/`
- **Tailwind CSS**: styling via utilities + `app/globals.css`
- **Framer Motion**: scroll animations

---

## 1) Folder & Responsibilities

### `app/`
- `app/layout.tsx`: root HTML layout, global background, imports `app/globals.css`
- `app/page.tsx`: assembles the portfolio page by rendering each section component
- `app/api/*`: server endpoints (runs on server)
  - `app/api/contact/route.ts`: receives contact form data and sends email via Resend
  - `app/api/resume/upload/route.ts`: uploads `resume.pdf` into `public/`
  - `app/api/resume/download/route.ts`: tracks resume download (currently logs only)

### `components/`
UI sections (each one maps to a page section with an `id` used by navigation scroll):
- `Navigation.tsx`: header nav + theme toggle + active section logic
- `Home.tsx`: hero section (email/phone/location cards)
- `Summary.tsx`, `Projects.tsx`, `Skills.tsx`, `Education.tsx`, `Experience.tsx`
- `ContactForm.tsx`: “Get In Touch” form which POSTs to `/api/contact`
- `Links.tsx`: social links
- `ScrollAnimation.tsx`: shared animation wrapper (Framer Motion)

### `data/`
- `data/personal-info.ts`: **single source of truth** for your portfolio content (name, email, projects, skills, etc.)

### `public/`
Static files served directly:
- `public/resume.pdf` (downloadable resume)
- `public/photo.jpg` (profile photo)

---

## 2) Main Page Render Flow

`app/page.tsx` renders one single page and stacks sections in order.

```mermaid
flowchart TD
  A[Browser requests /] --> B[Next.js App Router]
  B --> C[app/layout.tsx]
  C --> D[app/page.tsx]
  D --> E[Navigation]
  D --> F[Home]
  D --> G[Summary]
  D --> H[Projects]
  D --> I[Skills]
  D --> J[Education]
  D --> K[Experience]
  D --> L[ContactForm]
  D --> M[Links]

  N[data/personal-info.ts] --> F
  N --> G
  N --> H
  N --> I
  N --> J
  N --> K
  N --> M
```

---

## 3) Navigation & Active Section Logic

The nav is a **client component**.
- On scroll it finds which section is currently in view (`home`, `summary`, `projects`, etc.)
- On click it `scrollIntoView()` to the section
- Dark mode toggles `document.documentElement.classList` with `dark`

```mermaid
flowchart TD
  A[User scrolls page] --> B[Navigation handleScroll]
  B --> C{Near bottom?}
  C -- yes --> D[Set active: links]
  C -- no --> E[Loop sections bottom→top]
  E --> F{scrollY >= section offsetTop?}
  F -- yes --> G[Set active section]
  F -- no --> E
```

---

## 4) Contact Form → Direct Email (Get In Touch)

### What happens
- User submits form in `components/ContactForm.tsx`
- Browser sends `POST /api/contact` with JSON body
- Server validates
- Server sends an email to **CONTACT_EMAIL** using **Resend**

### Environment variables
Stored in `.env.local`:
- `RESEND_API_KEY=...`
- `CONTACT_EMAIL=rajandobariya6@gmail.com`
- `RESEND_FROM=Portfolio <onboarding@resend.dev>` (set to a verified sender for production)

```mermaid
sequenceDiagram
  participant U as User
  participant B as Browser
  participant CF as ContactForm.tsx
  participant API as /api/contact (route.ts)
  participant R as Resend API
  participant I as Inbox (CONTACT_EMAIL)

  U->>B: Fill contact form
  B->>CF: Submit
  CF->>API: POST JSON {name,email,subject,message}
  API->>API: Validate fields + email format
  API->>R: Send email (replyTo = visitor email)
  R->>I: Email delivered
  API->>CF: 200 {message: "Message sent successfully"}
  CF->>B: Show success UI
```

---

## 5) Resume Upload (Admin-style feature)

`app/api/resume/upload/route.ts` accepts a PDF upload and writes it to `public/resume.pdf`.

```mermaid
sequenceDiagram
  participant U as User
  participant B as Browser
  participant RM as ResumeManager.tsx
  participant API as /api/resume/upload
  participant FS as Server FS (public/resume.pdf)

  U->>B: Select PDF
  B->>RM: onChange(file)
  RM->>API: POST multipart/form-data (resume)
  API->>API: Validate type + size
  API->>FS: Save as public/resume.pdf
  API->>RM: 200 success
  RM->>B: Show uploaded message
```

Note: This endpoint has **no authentication** right now. If deployed publicly, anyone could upload unless you protect it.

---

## 6) Resume Download Tracking

The download button:
- Fires a tracking request to `POST /api/resume/download`
- Then downloads the file `public/resume.pdf`

```mermaid
flowchart TD
  A[User clicks Download] --> B[ResumeManager.tsx]
  B --> C[POST /api/resume/download]
  C --> D[Server logs timestamp + userAgent + referer]
  B --> E[Create <a> link to /resume.pdf]
  E --> F[Browser downloads resume.pdf]
```

---

## 7) What to change most often

- Content: `data/personal-info.ts`
- Styling: `app/globals.css` and `tailwind.config.ts`
- Contact email: `.env.local` (do NOT commit)

---

## 8) Quick Run Commands

```bash
npm install
npm run dev
```

Production:
```bash
npm run build
npm start
```
