# Backend Setup Guide

## 📧 Email Service Setup

I've created API routes for your portfolio. Choose one email service:

### Option 1: Resend (Recommended) ⭐

**Best for:** Next.js projects, modern API, free tier (3,000 emails/month)

1. Sign up at [resend.com](https://resend.com)
2. Get your API key from dashboard
3. Add to `.env.local`:
```env
RESEND_API_KEY=re_your_api_key_here
CONTACT_EMAIL=rajandobariya6@gmail.com
```

4. Install Resend:
```bash
npm install resend
```

5. Uncomment and update the email code in `app/api/contact/route.ts`

---

### Option 2: EmailJS (Easiest - No Backend)

**Best for:** Quick setup, no backend code needed, free tier (200 emails/month)

1. Sign up at [emailjs.com](https://www.emailjs.com)
2. Connect your email service (Gmail, Outlook, etc.)
3. Create email template
4. Get Service ID, Template ID, and Public Key
5. Update contact form to use EmailJS client-side

**Pros:** No backend needed, works immediately
**Cons:** Less secure (API keys visible in frontend), limited customization

---

### Option 3: SendGrid

**Best for:** Enterprise, high volume (100 emails/day free)

1. Sign up at [sendgrid.com](https://sendgrid.com)
2. Create API key
3. Add to `.env.local`:
```env
SENDGRID_API_KEY=SG.your_api_key_here
CONTACT_EMAIL=rajandobariya6@gmail.com
```

4. Install SendGrid:
```bash
npm install @sendgrid/mail
```

---

### Option 4: SMTP with Nodemailer

**Best for:** Using your own email server

1. Get SMTP credentials from your email provider
2. Add to `.env.local`:
```env
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password
CONTACT_EMAIL=rajandobariya6@gmail.com
```

3. Install Nodemailer:
```bash
npm install nodemailer
```

---

## 🚀 Quick Start with Resend (Recommended)

1. **Install Resend:**
```bash
npm install resend
```

2. **Create `.env.local` file:**
```env
RESEND_API_KEY=re_your_api_key_here
CONTACT_EMAIL=rajandobariya6@gmail.com
```

3. **Update `app/api/contact/route.ts`** - I'll provide the code below

4. **Add Contact Form to your page:**
   - Import `ContactForm` component in `app/page.tsx`
   - Add `<ContactForm />` before `<Links />`

---

## 📝 Implementation Example (Resend)

Here's the complete code for `app/api/contact/route.ts` with Resend:

```typescript
import { NextRequest, NextResponse } from "next/server";
import { Resend } from "resend";

const resend = new Resend(process.env.RESEND_API_KEY);

export async function POST(request: NextRequest) {
  try {
    const body = await request.json();
    const { name, email, subject, message } = body;

    // Validation
    if (!name || !email || !subject || !message) {
      return NextResponse.json(
        { error: "All fields are required" },
        { status: 400 }
      );
    }

    // Send email
    await resend.emails.send({
      from: "Portfolio Contact <onboarding@resend.dev>", // Update this
      to: process.env.CONTACT_EMAIL!,
      subject: `Portfolio Contact: ${subject}`,
      html: `
        <h2>New Contact Form Submission</h2>
        <p><strong>Name:</strong> ${name}</p>
        <p><strong>Email:</strong> ${email}</p>
        <p><strong>Subject:</strong> ${subject}</p>
        <p><strong>Message:</strong></p>
        <p>${message.replace(/\n/g, "<br>")}</p>
        <hr>
        <p><small>Sent from your portfolio website</small></p>
      `,
      replyTo: email, // So you can reply directly
    });

    return NextResponse.json(
      { message: "Message sent successfully" },
      { status: 200 }
    );
  } catch (error) {
    console.error("Contact form error:", error);
    return NextResponse.json(
      { error: "Failed to send message. Please try again later." },
      { status: 500 }
    );
  }
}
```

---

## 📊 Adding Contact Form to Your Page

Update `app/page.tsx`:

```typescript
import ContactForm from "@/components/ContactForm";
// ... other imports

export default function Portfolio() {
  return (
    <main className="min-h-screen">
      <Navigation />
      <Home />
      <Summary />
      <Projects />
      <Skills />
      <Education />
      <Experience />
      <ContactForm /> {/* Add this */}
      <Links />
    </main>
  );
}
```

---

## 🔒 Security Notes

1. **Never commit `.env.local`** - It's already in `.gitignore`
2. **Rate Limiting** - Consider adding rate limiting to prevent spam
3. **CAPTCHA** - Add reCAPTCHA for extra spam protection (optional)
4. **Validation** - Always validate inputs on the server

---

## 📈 Next Steps (Optional)

- Add database (MongoDB, PostgreSQL) for storing messages
- Add rate limiting
- Add reCAPTCHA
- Set up email notifications
- Create admin dashboard to view messages

