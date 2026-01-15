<div align="center">

# 🚗 EXPO CAR MEETING

**Platform profesională pentru evenimente auto cu management complet de înscrieri și votare**

[![Next.js](https://img.shields.io/badge/Next.js-15.5.7-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.1.0-61DAFB?style=for-the-badge&logo=react)](https://reactjs.org/)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase)](https://supabase.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.1.9-06B6D4?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)

[Demo Live](https://expocarmeeting.xyz) • [Documentație](./SETUP.md) • [Report Bug](https://github.com/CudlaCristian/expo-car-meeting/issues)

</div>

---

## 📋 Cuprins

- [Despre Proiect](#-despre-proiect)
- [Features Principale](#-features-principale)
- [Tech Stack](#-tech-stack)
- [Arhitectură](#-arhitectură)
- [Instalare](#-instalare)
- [Configurare](#-configurare)
- [Structura Proiectului](#-structura-proiectului)
- [Securitate](#-securitate)
- [Deployment](#-deployment)
- [Autor](#-autor)
- [Licență](#-licență)

---

## 🎯 Despre Proiect

**EXPO CAR MEETING** este o platformă web modernă, construită pentru gestionarea profesională a evenimentelor auto. Aplicația oferă un sistem complet de înscriere mașini, aprobare de către administratori, sistem de votare pentru "Best of Show", și management de sponsori și program.

### 🌟 De ce acest proiect?

- **Design Cyberpunk/Vice City**: Interfață unică inspirată din cultura auto și estetica retro-futuristă
- **Real-time Updates**: Actualizări instant prin Supabase Realtime
- **AI Image Processing**: Îndepărtare automată a fundalului pentru fotografiile mașinilor
- **Mobile-First**: Optimizat pentru toate dispozitivele
- **Securitate Avansată**: Google reCAPTCHA v3, Row Level Security, Device Fingerprinting

---

## ✨ Features Principale

### 👥 Pentru Utilizatori
- ✅ **Autentificare Completă**: Sign up, login, email verification, password reset
- 📝 **Înscriere Mașini**: Formular detaliat cu upload multiple imagini
- 🖼️ **Galerie Personală**: Vizualizare status înscrieri (pending, approved, rejected)
- 🗳️ **Sistem Votare**: Best of Show voting cu protecție anti-fraud
- 🎫 **Support Tickets**: Chat în timp real cu administratorii
- 📱 **SMS Notifications**: Notificări la înscriere (opțional, Twilio)

### 👨‍💼 Pentru Administratori
- 🎛️ **Dashboard Complet**: Management centralizat al tuturor submisiilor
- ✂️ **AI Background Removal**: Procesare automată imagini cu @imgly/background-removal
- 🏆 **Best of Show Manager**: Activare/dezactivare votare, management candidați
- 📅 **Event Schedule**: Creare și editare program eveniment
- 💼 **Sponsors Manager**: Upload și management logo-uri sponsori
- 👥 **User Management**: Vizualizare și management utilizatori
- 💬 **Support Center**: Răspuns la ticketele utilizatorilor

### 🎨 Design & UX
- 🌈 **Gradient Animations**: Efecte vizuale spectaculoase cu pulsare și blur
- 🎭 **Cyberpunk Theme**: Neon colors, scanlines, retro-futuristic aesthetics
- 📱 **Responsive Design**: Layout optimizat pentru mobil, tabletă, desktop
- ⚡ **Loading States**: Skeleton loaders și suspense boundaries
- 🎯 **Accessible**: ARIA labels, semantic HTML, keyboard navigation

---

## 🛠️ Tech Stack

### Frontend
- **[Next.js 15.5.7](https://nextjs.org/)** - React framework cu App Router
- **[React 19.1.0](https://reactjs.org/)** - UI library
- **[TypeScript 5.0](https://www.typescriptlang.org/)** - Type safety
- **[Tailwind CSS 4.1.9](https://tailwindcss.com/)** - Utility-first CSS
- **[Framer Motion 12](https://www.framer.com/motion/)** - Animații
- **[React Three Fiber](https://docs.pmnd.rs/react-three-fiber)** - 3D graphics (pentru splash screen)
- **[Lucide React](https://lucide.dev/)** - Icon library

### Backend & Database
- **[Supabase](https://supabase.com/)** - Backend-as-a-Service
  - PostgreSQL Database
  - Authentication & Authorization
  - Real-time Subscriptions
  - Storage (imagini mașini)
  - Row Level Security (RLS)

### Integrari & APIs
- **[@imgly/background-removal](https://img.ly/showcases/cesdk/web/background-removal)** - AI background removal (gratuit, no API key)
- **[Google reCAPTCHA v3](https://www.google.com/recaptcha/)** - Bot protection
- **[Resend](https://resend.com/)** - Email notifications
- **[Twilio](https://www.twilio.com/)** - SMS notifications (opțional)

### UI Components
- **[Radix UI](https://www.radix-ui.com/)** - Headless components
- **[shadcn/ui](https://ui.shadcn.com/)** - Component library
- **[Recharts](https://recharts.org/)** - Charts pentru analytics
- **[React Hook Form](https://react-hook-form.com/)** - Form management
- **[Zod](https://zod.dev/)** - Schema validation

---

## 🏗️ Arhitectură

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
├── profiles (utilizatori + metadata)
├── admin_users (permisiuni admin)
├── car_submissions (înscrieri mașini)
├── best_of_show_votes (voturi)
├── sponsors (logo-uri sponsori)
├── event_schedule (program evenimente)
├── support_tickets (tickete support)
└── support_messages (mesaje chat)

-- Storage Buckets
└── car-images (fotografii mașini)
```

---

## 🚀 Instalare

### Prerequisite

- Node.js 18+ (recomandat 20+)
- npm sau yarn
- Cont Supabase (gratuit)
- Cont Google reCAPTCHA (gratuit)

### Quick Start

```bash
# 1. Clone repository
git clone https://github.com/CudlaCristian/expo-car-meeting.git
cd expo-car-meeting

# 2. Instalare dependențe
npm install

# 3. Configurare variabile de mediu
cp .env.example .env.local
# Editează .env.local cu credențialele tale

# 4. Rulează scripturile SQL în Supabase
# Vezi secțiunea "Configurare Database"

# 5. Start development server
npm run dev
```

Aplicația va fi disponibilă la `http://localhost:3000`

---

## ⚙️ Configurare

### 1. Supabase Setup

#### A. Creează proiect Supabase
1. Mergi pe [supabase.com](https://supabase.com)
2. Creează un proiect nou
3. Copiază `Project URL` și `anon public key`

#### B. Configurare Database
Rulează scripturile SQL în ordine din folder-ul `scripts/`:

```bash
scripts/
├── 01-create-tables.sql           # Creează tabelele principale
├── 02-create-functions.sql        # Funcții și trigger-e
├── 03-seed-admin.sql              # Instrucțiuni pentru admin
├── 04-create-storage-bucket.sql   # Bucket pentru imagini
├── 05-fix-rls-policies.sql        # RLS policies
└── ...                            # Alte scripturi
```

**Important**: Rulează scripturile în Supabase SQL Editor în ordinea numerelor!

#### C. Creează primul admin
După înregistrarea pe site, rulează în SQL Editor:

```sql
INSERT INTO admin_users (user_id)
SELECT id FROM profiles WHERE email = 'your-email@example.com';
```

### 2. Environment Variables

Creează fișierul `.env.local`:

```bash
# Supabase (obligatoriu)
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Google reCAPTCHA (obligatoriu)
NEXT_PUBLIC_RECAPTCHA_SITE_KEY=your_recaptcha_site_key
RECAPTCHA_SECRET_KEY=your_recaptcha_secret_key

# Email Notifications cu Resend (opțional)
RESEND_API_KEY=your_resend_api_key

# SMS Notifications cu Twilio (opțional)
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_WHATSAPP_NUMBER=your_twilio_whatsapp_number

# Development (opțional)
NEXT_PUBLIC_DEV_SUPABASE_REDIRECT_URL=http://localhost:3000
```

### 3. Google reCAPTCHA Setup

1. Mergi pe [google.com/recaptcha/admin](https://www.google.com/recaptcha/admin)
2. Înregistrează un site nou:
   - **Label**: EXPO CAR MEETING
   - **reCAPTCHA type**: v3
   - **Domains**: `expocarmeeting.xyz`, `localhost`
3. Copiază **Site Key** și **Secret Key** în `.env.local`

### 4. Email Setup (Opțional - Resend)

Pentru notificări email:

1. Creează cont pe [resend.com](https://resend.com)
2. Verifică domeniul `expocarmeeting.xyz`
3. Adaugă DNS records în Vercel:
   - SPF, DKIM, DMARC records
4. Generează API Key din Resend Dashboard
5. Adaugă în `.env.local`

### 5. SMS Setup (Opțional - Twilio)

Vezi ghidul detaliat: `CONFIGURARE-SMS-TWILIO.md`

Quick start:
1. Cont Twilio trial: [twilio.com/try-twilio](https://www.twilio.com/try-twilio)
2. Obține: Account SID, Auth Token, Phone Number
3. Configurează în Supabase Auth Settings
4. Adaugă credențiale în `.env.local`

---

## 📁 Structura Proiectului

```
expo-car-meeting/
│
├── app/                           # Next.js App Router
│   ├── page.tsx                   # 🏠 Homepage cu stats și Best of Show
│   ├── layout.tsx                 # Root layout cu providers
│   ├── globals.css                # Global styles (Tailwind + custom)
│   │
│   ├── login/                     # 🔐 Autentificare
│   │   └── page.tsx
│   ├── signup/                    # ✍️ Înregistrare
│   │   └── page.tsx
│   ├── reset-password/            # 🔑 Reset parolă
│   │   └── page.tsx
│   │
│   ├── dashboard/                 # 👤 Dashboard utilizator
│   │   └── page.tsx
│   ├── admin/                     # 👨‍💼 Panou admin
│   │   └── page.tsx
│   │
│   ├── masini-acceptate/          # 🚗 Galerie mașini acceptate
│   │   └── page.tsx
│   ├── program/                   # 📅 Program eveniment
│   │   └── page.tsx
│   ├── contact/                   # 📧 Contact
│   │   └── page.tsx
│   │
│   ├── support/                   # 💬 System support tickets
│   │   ├── page.tsx               # Lista tickete
│   │   ├── new/page.tsx           # Creare ticket + chat
│   │   └── [id]/page.tsx          # Detalii ticket
│   │
│   └── api/                       # API Routes
│       ├── auth/signout/          # Logout
│       ├── process-background/    # AI background removal
│       ├── verify-recaptcha/      # Verificare reCAPTCHA
│       └── notify-admins-new-ticket/ # Notificare admini
│
├── components/                    # React Components
│   ├── ui/                        # shadcn/ui components
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── dialog.tsx
│   │   └── ...
│   │
│   ├── car-submission-form.tsx    # Formular înscriere mașină
│   ├── user-submissions.tsx       # Lista mașini utilizator
│   ├── admin-submissions-list.tsx # Lista pentru admin
│   ├── background-removal-button.tsx # Buton AI processing
│   │
│   ├── best-of-show-voting.tsx    # Sistem votare
│   ├── best-of-show-manager.tsx   # Admin votare
│   ├── sponsors-manager.tsx       # Admin sponsori
│   ├── event-schedule-manager.tsx # Admin program
│   │
│   ├── user-profile-button.tsx    # Avatar + dropdown user
│   ├── navbar.tsx                 # Navigation bar
│   ├── footer.tsx                 # Footer
│   │
│   ├── unified-support-page.tsx   # Pagina support cu chat
│   ├── ticket-chat.tsx            # Chat component real-time
│   ├── create-ticket-form.tsx     # Formular creare ticket
│   │
│   ├── real-car-count.tsx         # Counter mașini real-time
│   ├── home-page-stats.tsx        # Stats homepage
│   ├── home-page-sponsors.tsx     # Sponsors homepage
│   └── hero-signup-button.tsx     # CTA button homepage
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
├── scripts/                       # SQL Scripts pentru Supabase
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
├── README.md                      # Acest fișier
├── SETUP.md                       # Ghid instalare detaliat
├── CONFIGURARE-SMS-TWILIO.md      # Ghid SMS setup
└── QUICK-START-SMS.md             # Quick start SMS
```

---

## 🔒 Securitate

### Row Level Security (RLS)

Toate tabelele au RLS activat cu policies stricte:

```sql
-- Exemplu: Users pot vedea doar propriile submisii
CREATE POLICY "Users can view own submissions"
ON car_submissions FOR SELECT
USING (auth.uid() = user_id);

-- Exemplu: Doar adminii pot aproba mașini
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
- **Device Fingerprinting**: Canvas + hardware fingerprinting pentru votare
- **Rate Limiting**: Protecție împotriva spam-ului
- **Email Verification**: Mandatory pentru activare cont

### Authentication

- **Supabase Auth**: Industry-standard authentication
- **Password Hashing**: bcrypt cu salt
- **Session Management**: JWT tokens cu refresh
- **Password Reset**: Secure token-based flow

### Data Protection

- **HTTPS Only**: SSL/TLS encryption
- **Storage Policies**: Imagini protejate prin RLS
- **Input Validation**: Zod schemas pentru toate formularele
- **SQL Injection**: Prevented prin Supabase prepared statements

---

## 🌐 Deployment

### Vercel (Recomandat)

1. **Fork repository** pe GitHub
2. **Conectează la Vercel**:
   ```bash
   vercel login
   vercel deploy
   ```
3. **Configurează environment variables** în Vercel Dashboard
4. **Deploy automatic**: Push pe `main` branch

### Environment Variables în Vercel

Adaugă în Project Settings → Environment Variables:

```
NEXT_PUBLIC_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY
NEXT_PUBLIC_RECAPTCHA_SITE_KEY
RECAPTCHA_SECRET_KEY
RESEND_API_KEY (opțional)
TWILIO_* (opțional)
```

### Custom Domain

1. Adaugă domeniul în Vercel: `expocarmeeting.xyz`
2. Configurează DNS records:
   - A record: `76.76.21.21`
   - CNAME: `cname.vercel-dns.com`
3. Așteaptă propagare DNS (24-48h)

---

## 📊 Analytics & Monitoring

- **Vercel Analytics**: Built-in pentru performance metrics
- **Supabase Logs**: Database query monitoring
- **Console Logs**: Debug logs cu prefix `[v0]`

---

## 🤝 Contributing

Contribuțiile sunt binevenite! Pentru schimbări majore:

1. Fork repository-ul
2. Creează un branch pentru feature-ul tău (`git checkout -b feature/AmazingFeature`)
3. Commit schimbările (`git commit -m 'Add some AmazingFeature'`)
4. Push pe branch (`git push origin feature/AmazingFeature`)
5. Deschide un Pull Request

---

## 🐛 Bug Reports & Feature Requests

Pentru bug-uri sau feature requests, deschide un issue pe GitHub:
[github.com/CudlaCristian/expo-car-meeting/issues](https://github.com/CudlaCristian/expo-car-meeting/issues)

---

## 📝 Licență

Acest proiect este licențiat sub **MIT License**.

---

## 👨‍💻 Autor

**Cristian Cudla**

- GitHub: [@CudlaCristian](https://github.com/CudlaCristian)
- Email: cristicudla123@gmail.com
- LinkedIn: [Cristian Cudla](https://www.linkedin.com/in/cristian-cudla/)
- Portfolio: [expocarmeeting.xyz](https://expocarmeeting.xyz)

---

## 🙏 Mulțumiri

Tehnologii și servicii folosite:

- [Next.js](https://nextjs.org/) - The React Framework
- [Supabase](https://supabase.com/) - Open Source Firebase Alternative
- [Vercel](https://vercel.com/) - Platform pentru deployment
- [Tailwind CSS](https://tailwindcss.com/) - CSS Framework
- [shadcn/ui](https://ui.shadcn.com/) - Component Library
- [img.ly](https://img.ly/) - Background Removal AI
- [Google reCAPTCHA](https://www.google.com/recaptcha/) - Bot Protection

---

## 📚 Documentație Suplimentară

- [Setup Guide](./SETUP.md) - Ghid detaliat de instalare
- [SMS Configuration](./CONFIGURARE-SMS-TWILIO.md) - Setup Twilio SMS
- [API Documentation](./docs/API.md) - API endpoints (coming soon)
- [Component Library](./docs/COMPONENTS.md) - Component docs (coming soon)

---

<div align="center">

**Dezvoltat cu ❤️ de [Cristian Cudla](https://github.com/CudlaCristian)**



</div>
