# Configurare SMTP Personalizat pentru EXPOCARMEETING

## De ce ai nevoie de SMTP personalizat?

Serviciul de email implicit Supabase:
- ❌ Are rate limits (maxim câteva email-uri pe oră)
- ❌ Nu permite personalizare completă (apare "Supabase" în sender)
- ❌ Nu e pentru producție

Cu SMTP personalizat:
- ✅ Email-uri nelimitate
- ✅ Sender personalizat: "EXPOCARMEETING <noreply@expocarmeeting.ro>"
- ✅ Template-uri HTML personalizate funcționează 100%
- ✅ Profesional și de încredere

---

## Opțiunea 1: Gmail SMTP (GRATUIT - Recomandat pentru început)

### Avantaje:
- ✅ Complet gratuit
- ✅ Configurare în 5 minute
- ✅ Până la 500 email-uri/zi
- ✅ Perfect pentru testare și evenimente mici

### Pași de configurare:

#### 1. Activează "App Password" în Gmail

1. Mergi la: https://myaccount.google.com/security
2. Scroll jos până la "2-Step Verification" și activează-l (dacă nu e deja activ)
3. După activare, scroll jos și click pe "App passwords"
4. Selectează:
   - App: "Mail"
   - Device: "Other" → scrie "EXPOCARMEETING"
5. Click "Generate"
6. **Copiază parola generată** (16 caractere) - o vei folosi mai jos

#### 2. Configurează SMTP în Supabase

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/settings/auth
2. Scroll jos până la "SMTP Settings"
3. Click "Enable Custom SMTP"
4. Completează:

\`\`\`
Sender email: email-ul-tau@gmail.com
Sender name: EXPOCARMEETING

Host: smtp.gmail.com
Port: 587
Username: email-ul-tau@gmail.com
Password: [parola de 16 caractere generată mai sus]
\`\`\`

5. Click "Save"

#### 3. Testează

- Încearcă să te înregistrezi cu un email nou
- Verifică inbox-ul (și spam-ul)
- Email-ul ar trebui să vină de la "EXPOCARMEETING"

---

## Opțiunea 2: Resend (GRATUIT - Cel mai profesional)

### Avantaje:
- ✅ 3,000 email-uri/lună GRATUIT
- ✅ Cel mai ușor de configurat
- ✅ Domeniu personalizat (noreply@expocarmeeting.ro)
- ✅ Analytics și tracking

### Pași:

1. **Creează cont gratuit**: https://resend.com/signup
2. **Verifică domeniul** (sau folosește domeniul lor temporar pentru testare)
3. **Generează API Key**:
   - Dashboard → API Keys → Create API Key
   - Copiază key-ul
4. **Configurează în Supabase**:
   - Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/settings/auth
   - SMTP Settings:
     \`\`\`
     Host: smtp.resend.com
     Port: 587
     Username: resend
     Password: [API Key-ul tău]
     Sender email: noreply@expocarmeeting.ro (sau onboarding@resend.dev pentru testare)
     Sender name: EXPOCARMEETING
     \`\`\`

---

## Opțiunea 3: SendGrid (GRATUIT - 100 email-uri/zi)

### Pași:

1. Cont gratuit: https://signup.sendgrid.com/
2. Verifică email-ul
3. Settings → API Keys → Create API Key
4. Configurează în Supabase:
   \`\`\`
   Host: smtp.sendgrid.net
   Port: 587
   Username: apikey
   Password: [API Key-ul tău]
   Sender email: noreply@expocarmeeting.ro
   Sender name: EXPOCARMEETING
   \`\`\`

---

## După configurarea SMTP

### 1. Actualizează Template-urile Email

Acum că ai SMTP personalizat, template-urile HTML pe care ți le-am dat vor funcționa perfect:

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/templates
2. Pentru "Confirm signup":
   - Copiază HTML-ul din `email-templates/confirmation-email.html`
   - Lipește-l în editor
   - Save
3. Pentru "Reset Password":
   - Copiază HTML-ul din `email-templates/reset-password-email.html`
   - Lipește-l în editor
   - Save

### 2. Testează

- Înregistrează un cont nou
- Solicită resetare parolă
- Verifică că email-urile vin de la "EXPOCARMEETING" cu design-ul personalizat

---

## Recomandarea mea

**Pentru EXPOCARMEETING, recomand Gmail SMTP** pentru că:
- E gratuit 100%
- Configurare super rapidă (5 minute)
- 500 email-uri/zi sunt suficiente pentru evenimente
- Poți upgrade la Resend mai târziu dacă ai nevoie

---

## Troubleshooting

### Email-urile nu sosesc?

1. **Verifică spam/junk folder**
2. **Verifică credențialele SMTP** în Supabase Settings
3. **Pentru Gmail**: Asigură-te că ai activat 2-Step Verification și ai generat App Password
4. **Testează conexiunea**: Supabase ar trebui să arate "Connected" lângă SMTP settings

### Email-urile sosesc dar arată urât?

- Asigură-te că ai copiat COMPLET template-ul HTML (inclusiv `<!DOCTYPE html>` de la început)
- Verifică că nu ai șters accidental `{{ .ConfirmationURL }}` din template

---

## Link-uri Utile

- Supabase SMTP Settings: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/settings/auth
- Supabase Email Templates: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/templates
- Gmail App Passwords: https://myaccount.google.com/apppasswords
- Resend: https://resend.com
- SendGrid: https://sendgrid.com

---

**Succes! După configurarea SMTP, toate email-urile vor veni de la EXPOCARMEETING cu design-ul tău personalizat! 🚗💨**
