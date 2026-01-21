<div align="center">

# 🚗 EXPO CAR MEETING

**Professional platform for car events with complete registration and voting management**

[![Next.js](https://img.shields.io/badge/Next.js-15.5.7-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.1.0-61DAFB?style=for-the-badge&logo=react)](https://reactjs.org/)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase)](https://supabase.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.1.9-06B6D4?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)

[Live Demo](https://expocarmeeting.xyz) • [Documentation](./SETUP.md) • [Report Bug](https://github.com/CudlaCristian/expo-car-meeting/issues)

</div>

---

## 📋 Table of Contents

- [About Project](#-about-project)
- [Main Features](#-main-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Project Structure](#-project-structure)
- [Security](#-security)
- [Deployment](#-deployment)
- [Author](#-author)
- [License](#-license)

---

## 🎯 About Project

**EXPO CAR MEETING** is a modern web platform built for professional management of car events. The application provides a complete system for car registration, admin approval, "Best of Show" voting system, and sponsor and schedule management.

### 🌟 Why This Project?

- **Cyberpunk/Vice City Design**: Unique interface inspired by car culture and retro-futuristic aesthetics
- **Real-time Updates**: Instant updates through Supabase Realtime
- **AI Image Processing**: Automatic background removal for car photos
- **Mobile-First**: Optimized for all devices
- **Advanced Security**: Google reCAPTCHA v3, Row Level Security, Device Fingerprinting

---

## ✨ Main Features

### 👥 For Users
- ✅ **Complete Authentication**: Sign up, login, email verification, password reset
- 📝 **Car Registration**: Detailed form with multiple image uploads
- 🖼️ **Personal Gallery**: View registration status (pending, approved, rejected)
- 🗳️ **Voting System**: Best of Show voting with anti-fraud protection
- 🎫 **Support Tickets**: Real-time chat with administrators
- 📱 **SMS Notifications**: Registration notifications (optional, Twilio)

### 👨‍💼 For Administrators
- 🎛️ **Complete Dashboard**: Centralized management of all submissions
- ✂️ **AI Background Removal**: Automatic image processing with @imgly/background-removal
- 🏆 **Best of Show Manager**: Enable/disable voting, manage candidates
- 📅 **Event Schedule**: Create and edit event program
- 💼 **Sponsors Manager**: Upload and manage sponsor logos
- 👥 **User Management**: View and manage users
- 💬 **Support Center**: Respond to user support tickets

### 🎨 Design & UX
- 🌈 **Gradient Animations**: Spectacular visual effects with pulsing and blur
- 🎭 **Cyberpunk Theme**: Neon colors, scanlines, retro-futuristic aesthetics
- 📱 **Responsive Design**: Layout optimized for mobile, tablet, desktop
- ⚡ **Loading States**: Skeleton loaders and suspense boundaries
- 🎯 **Accessible**: ARIA labels, semantic HTML, keyboard navigation

---

## 🛠️ Tech Stack

### Frontend
- **[Next.js 15.5.7](https://nextjs.org/)** - React framework with App Router
- **[React 19.1.0](https://reactjs.org/)** - UI library
- **[TypeScript 5.0](https://www.typescriptlang.org/)** - Type safety
- **[Tailwind CSS 4.1.9](https://tailwindcss.com/)** - Utility-first CSS
- **[Framer Motion 12](https://www.framer.com/motion/)** - Animations
- **[React Three Fiber](https://docs.pmnd.rs/react-three-fiber)** - 3D graphics (for splash screen)
- **[Lucide React](https://lucide.dev/)** - Icon library

### Backend & Database
- **[Supabase](https://supabase.com/)** - Backend-as-a-Service
  - PostgreSQL Database
  - Authentication & Authorization
  - Real-time Subscriptions
  - Storage (car images)
  - Row Level Security (RLS)

### Integrations & APIs
- **[@imgly/background-removal](https://img.ly/showcases/cesdk/web/background-removal)** - AI background removal (free, no API key)
- **[Google reCAPTCHA v3](https://www.google.com/recaptcha/)** - Bot protection
- **[Resend](https://resend.com/)** - Email notifications
- **[Twilio](https://www.twilio.com/)** - SMS notifications (optional)

### UI Components
- **[Radix UI](https://www.radix-ui.com/)** - Headless components
- **[shadcn/ui](https://ui.shadcn.com/)** - Component library
- **[Recharts](https://recharts.org/)** - Charts for analytics
- **[React Hook Form](https://react-hook-form.com/)** - Form management
- **[Zod](https://zod.dev/)** - Schema validation

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        FRONTEND (Next.js)                    │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │   Pages    │  │ Components │  │    Hooks   │            │
│  │ (App Dir)  │  │  (React)   │  │  (Custom)  │            │
│  └────────────┘  └────────────┘  └────────────┘            │
│         │               │                │                   │
└─────────┼───────────────┼────────────────┼───────────────────┘
          │               │                │
          ▼               ▼                ▼
┌─────────────────────────────────────────────────────────────┐
│                   MIDDLEWARE LAYER                           │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │    Auth    │  │  API Route │  │  Supabase  │            │
│  │   Guard    │  │  Handlers  │  │   Client   │            │
│  └────────────┘  └────────────┘  └────────────┘            │
└─────────────────────────────────────────────────────────────┘
          │               │                │
          ▼               ▼                ▼
┌─────────────────────────────────────────────────────────────┐
│                   BACKEND (Supabase)                         │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │ PostgreSQL │  │    Auth    │  │  Storage   │            │
│  │     DB     │  │  Service   │  │   Bucket   │            │
│  └────────────┘  └────────────┘  └────────────┘            │
│         │               │                │                   │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │    RLS     │  │  Realtime  │  │  Functions │            │
│  │  Policies  │  │Subscriptns │  │ (Triggers) │            │
│  └────────────┘  └────────────┘  └────────────┘            │
└─────────────────────────────────────────────────────────────┘
          │               │                │
          ▼               ▼                ▼
┌─────────────────────────────────────────────────────────────┐
│                  EXTERNAL SERVICES                           │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │  reCAPTCHA │  │   Resend   │  │   Twilio   │            │
│  │   (Google) │  │   (Email)  │  │    (SMS)   │            │
│  └────────────┘  └────────────┘  └────────────┘            │
└─────────────────────────────────────────────────────────────┘
```

### Database Schema

```sql
-- Core Tables
├── profiles (users + metadata)
├── admin_users (admin permissions)
├── car_submissions (car registrations)
├── best_of_show_votes (votes)
├── sponsors (sponsor logos)
├── event_schedule (event program)
├── support_tickets (support tickets)
└── support_messages (chat messages)

-- Storage Buckets
└── car-images (car photos)
```

---

## 🚀 Installation

### Prerequisites

- Node.js 18+ (recommended 20+)
- npm or yarn
- Supabase account (free)
- Google reCAPTCHA account (free)

### Quick Start

```bash
# 1. Clone repository
git clone https://github.com/CudlaCristian/expo-car-meeting.git
cd expo-car-meeting

# 2. Install dependencies
npm install

# 3. Configure environment variables
cp .env.example .env.local
# Edit .env.local with your credentials

# 4. Run SQL scripts in Supabase
# See "Database Configuration" section

# 5. Start development server
npm run dev
```

Application will be available at `http://localhost:3000`

---

## ⚙️ Configuration

### 1. Supabase Setup

#### A. Create Supabase project
1. Go to [supabase.com](https://supabase.com)
2. Create a new project
3. Copy `Project URL` and `anon public key`

#### B. Database Configuration
Run SQL scripts in order from `scripts/` folder in Supabase SQL Editor:

```bash
scripts/
├── 01-create-tables.sql           # Create main tables
├── 02-create-functions.sql        # Functions and triggers
├── 03-seed-admin.sql              # Admin instructions
├── 04-create-storage-bucket.sql   # Bucket for images
├── 05-fix-rls-policies.sql        # RLS policies
└── ...                            # Other scripts
```

**Important**: Run scripts in Supabase SQL Editor in numerical order!

#### C. Create first admin
After registering on the site, run in SQL Editor:

```sql
INSERT INTO admin_users (user_id)
SELECT id FROM profiles WHERE email = 'your-email@example.com';
```

### 2. Environment Variables

Create `.env.local` file:

```bash
# Supabase (required)
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Google reCAPTCHA (required)
NEXT_PUBLIC_RECAPTCHA_SITE_KEY=your_recaptcha_site_key
RECAPTCHA_SECRET_KEY=your_recaptcha_secret_key

# Email Notifications with Resend (optional)
RESEND_API_KEY=your_resend_api_key

# SMS Notifications with Twilio (optional)
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_WHATSAPP_NUMBER=your_twilio_whatsapp_number

# Development (optional)
NEXT_PUBLIC_DEV_SUPABASE_REDIRECT_URL=http://localhost:3000
```

### 3. Google reCAPTCHA Setup

1. Go to [google.com/recaptcha/admin](https://www.google.com/recaptcha/admin)
2. Register a new site:
   - **Label**: EXPO CAR MEETING
   - **reCAPTCHA type**: v3
   - **Domains**: `expocarmeeting.xyz`, `localhost`
3. Copy **Site Key** and **Secret Key** to `.env.local`

### 4. Email Setup (Optional - Resend)

For email notifications:

1. Create account on [resend.com](https://resend.com)
2. Verify domain `expocarmeeting.xyz`
3. Add DNS records in Vercel:
   - SPF, DKIM, DMARC records
4. Generate API Key from Resend Dashboard
5. Add to `.env.local`

### 5. SMS Setup (Optional - Twilio)

See detailed guide: `CONFIGURARE-SMS-TWILIO.md`

Quick start:
1. Twilio trial account: [twilio.com/try-twilio](https://www.twilio.com/try-twilio)
2. Get: Account SID, Auth Token, Phone Number
3. Configure in Supabase Auth Settings
4. Add credentials to `.env.local`

---

## 📁 Project Structure

```
expo-car-meeting/
│
├── app/                           # Next.js App Router
│   ├── page.tsx                   # 🏠 Homepage with stats and Best of Show
│   ├── layout.tsx                 # Root layout with providers
│   ├── globals.css                # Global styles (Tailwind + custom)
│   │
│   ├── login/                     # 🔐 Authentication
│   │   └── page.tsx
│   ├── signup/                    # ✍️ Registration
│   │   └── page.tsx
│   ├── reset-password/            # 🔑 Password reset
│   │   └── page.tsx
│   │
│   ├── dashboard/                 # 👤 User dashboard
│   │   └── page.tsx
│   ├── admin/                     # 👨‍💼 Admin panel
│   │   └── page.tsx
│   │
│   ├── masini-acceptate/          # 🚗 Approved cars gallery
│   │   └── page.tsx
│   ├── program/                   # 📅 Event program
│   │   └── page.tsx
│   ├── contact/                   # 📧 Contact
│   │   └── page.tsx
│   │
│   ├── support/                   # 💬 Support tickets system
│   │   ├── page.tsx               # Ticket list
│   │   ├── new/page.tsx           # Create ticket + chat
│   │   └── [id]/page.tsx          # Ticket details
│   │
│   └── api/                       # API Routes
│       ├── auth/signout/          # Logout
│       ├── process-background/    # AI background removal
│       ├── verify-recaptcha/      # Verify reCAPTCHA
│       └── notify-admins-new-ticket/ # Notify admins
│
├── components/                    # React Components
│   ├── ui/                        # shadcn/ui components
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── dialog.tsx
│   │   └── ...
│   │
│   ├── car-submission-form.tsx    # Car registration form
│   ├── user-submissions.tsx       # User's cars list
│   ├── admin-submissions-list.tsx # Admin submissions list
│   ├── background-removal-button.tsx # AI processing button
│   │
│   ├── best-of-show-voting.tsx    # Voting system
│   ├── best-of-show-manager.tsx   # Admin voting
│   ├── sponsors-manager.tsx       # Admin sponsors
│   ├── event-schedule-manager.tsx # Admin program
│   │
│   ├── user-profile-button.tsx    # Avatar + dropdown
│   ├── navbar.tsx                 # Navigation bar
│   ├── footer.tsx                 # Footer
│   │
│   ├── unified-support-page.tsx   # Support page with chat
│   ├── ticket-chat.tsx            # Real-time chat
│   ├── create-ticket-form.tsx     # Create ticket form
│   │
│   ├── real-car-count.tsx         # Real-time car counter
│   ├── home-page-stats.tsx        # Homepage stats
│   ├── home-page-sponsors.tsx     # Homepage sponsors
│   └── hero-signup-button.tsx     # CTA button
│
├── lib/                           # Utilities & Helpers
│   ├── supabase/
│   │   ├── client.ts              # Supabase browser client
│   │   ├── server.ts              # Supabase server client
│   │   ├── middleware.ts          # Middleware helper
│   │   └── config.ts              # Supabase configuration
│   │
│   ├── device-fingerprint.ts      # Device identification
│   ├── background-removal.ts      # AI image processing logic
│   └── utils.ts                   # Utility functions (cn, etc.)
│
├── hooks/                         # Custom React Hooks
│   ├── use-mobile.tsx             # Mobile detection
│   └── use-toast.ts               # Toast notifications
│
├── scripts/                       # SQL Scripts for Supabase
│   ├── 01-create-tables.sql
│   ├── 02-create-functions.sql
│   ├── 03-seed-admin.sql
│   ├── ...
│   └── 23-add-device-fingerprint.sql
│
├── middleware.ts                  # Next.js middleware (auth guard)
├── next.config.mjs                # Next.js configuration
├── tailwind.config.ts             # Tailwind configuration
├── tsconfig.json                  # TypeScript configuration
├── package.json                   # Dependencies
│
├── README.md                      # This file
├── SETUP.md                       # Detailed installation guide
├── CONFIGURARE-SMS-TWILIO.md      # SMS setup guide
└── QUICK-START-SMS.md             # SMS quick start
```

---

## 🔒 Security

### Row Level Security (RLS)

All tables have RLS enabled with strict policies:

```sql
-- Example: Users can only see their own submissions
CREATE POLICY "Users can view own submissions"
ON car_submissions FOR SELECT
USING (auth.uid() = user_id);

-- Example: Only admins can approve cars
CREATE POLICY "Only admins can update status"
ON car_submissions FOR UPDATE
USING (
  EXISTS (
    SELECT 1 FROM admin_users 
    WHERE user_id = auth.uid()
  )
);
```

### Bot Protection

- **Google reCAPTCHA v3**: Score-based validation (minimum 0.5)
- **Device Fingerprinting**: Canvas + hardware fingerprinting for voting
- **Rate Limiting**: Protection against spam
- **Email Verification**: Mandatory for account activation

### Authentication

- **Supabase Auth**: Industry-standard authentication
- **Password Hashing**: bcrypt with salt
- **Session Management**: JWT tokens with refresh
- **Password Reset**: Secure token-based flow

### Data Protection

- **HTTPS Only**: SSL/TLS encryption
- **Storage Policies**: Images protected via RLS
- **Input Validation**: Zod schemas for all forms
- **SQL Injection**: Prevented via Supabase prepared statements

---

## 🌐 Deployment

### Vercel (Recommended)

1. **Fork repository** on GitHub
2. **Connect to Vercel**:
   ```bash
   vercel login
   vercel deploy
   ```
3. **Configure environment variables** in Vercel Dashboard
4. **Automatic deployment**: Push to `main` branch

### Environment Variables in Vercel

Add in Project Settings → Environment Variables:

```
NEXT_PUBLIC_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY
NEXT_PUBLIC_RECAPTCHA_SITE_KEY
RECAPTCHA_SECRET_KEY
RESEND_API_KEY (optional)
TWILIO_* (optional)
```

### Custom Domain

1. Add domain in Vercel: `expocarmeeting.xyz`
2. Configure DNS records:
   - A record: `76.76.21.21`
   - CNAME: `cname.vercel-dns.com`
3. Wait for DNS propagation (24-48h)

---

## 📊 Analytics & Monitoring

- **Vercel Analytics**: Built-in performance metrics
- **Supabase Logs**: Database query monitoring
- **Console Logs**: Debug logs with `[v0]` prefix

---

## 🤝 Contributing

Contributions are welcome! For major changes:

1. Fork the repository
2. Create a branch for your feature (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 🐛 Bug Reports & Feature Requests

For bugs or feature requests, open an issue on GitHub:
[github.com/CudlaCristian/expo-car-meeting/issues](https://github.com/CudlaCristian/expo-car-meeting/issues)

---

## 📝 License

This project is licensed under the **MIT License**.

---

## 👨‍💻 Author

**Cristian Cudla**

- GitHub: [@CudlaCristian](https://github.com/CudlaCristian)
- Email: cristicudla123@gmail.com
- LinkedIn: [Cristian Cudla](https://www.linkedin.com/in/cristian-cudla/)
- Portfolio: [expocarmeeting.xyz](https://expocarmeeting.xyz)

---

## 🙏 Acknowledgments

Technologies and services used:

- [Next.js](https://nextjs.org/) - The React Framework
- [Supabase](https://supabase.com/) - Open Source Firebase Alternative
- [Vercel](https://vercel.com/) - Deployment Platform
- [Tailwind CSS](https://tailwindcss.com/) - CSS Framework
- [shadcn/ui](https://ui.shadcn.com/) - Component Library
- [img.ly](https://img.ly/) - Background Removal AI
- [Google reCAPTCHA](https://www.google.com/recaptcha/) - Bot Protection

---

## 📚 Additional Documentation

- [Setup Guide](./SETUP.md) - Detailed installation guide
- [SMS Configuration](./CONFIGURARE-SMS-TWILIO.md) - Twilio SMS setup
- [API Documentation](./docs/API.md) - API endpoints (coming soon)
- [Component Library](./docs/COMPONENTS.md) - Component docs (coming soon)

---

<div align="center">

**Developed with ❤️ by [Cristian Cudla](https://github.com/CudlaCristian)**

⭐ **Star** this repository if you liked the project!

</div>
