# Configurare Email Resetare Parolă - EXPOCARMEETING

## Problema: Nu primești email-uri de resetare parolă

### Pasul 1: Verifică Setările Email în Supabase

1. **Mergi la Authentication Settings**:
   \`\`\`
   https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/url-configuration
   \`\`\`

2. **Adaugă Redirect URLs**:
   - Scroll jos la secțiunea **"Redirect URLs"**
   - Adaugă următoarele URL-uri (apasă Enter după fiecare):
     \`\`\`
     http://localhost:3000/update-password
     https://your-production-domain.com/update-password
     \`\`\`
   - Click **"Save"**

### Pasul 2: Verifică Email Templates

1. **Mergi la Email Templates**:
   \`\`\`
   https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/templates
   \`\`\`

2. **Selectează "Reset Password"** din meniul lateral

3. **Verifică că template-ul conține**:
   \`\`\`html
   <a href="{{ .ConfirmationURL }}">Resetează Parola</a>
   \`\`\`

### Pasul 3: Verifică Email Provider

1. **Mergi la Settings → Project Settings**:
   \`\`\`
   https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/settings/general
   \`\`\`

2. **Verifică secțiunea "Email"**:
   - Dacă folosești **Supabase Email** (default):
     - Limitat la 3 email-uri/oră în development
     - Email-urile pot ajunge în Spam
   - Pentru producție, configurează un **Custom SMTP** (Gmail, SendGrid, etc.)

### Pasul 4: Testare

1. **Deschide Console-ul Browser** (F12)
2. **Mergi la** `/reset-password`
3. **Introdu email-ul** și trimite
4. **Verifică Console-ul** pentru mesaje de debug:
   \`\`\`
   [v0] Sending password reset email to: email@example.com
   [v0] Redirect URL: http://localhost:3000/update-password
   [v0] Password reset response: {...}
   \`\`\`

### Pasul 5: Verifică Email-ul

1. **Verifică Inbox-ul** - caută email de la `noreply@mail.app.supabase.io`
2. **Verifică Spam/Junk** - email-urile Supabase ajung adesea aici
3. **Așteaptă 1-2 minute** - email-urile pot întârzia

### Soluții Comune

#### Email-ul nu sosește deloc:
- Verifică că email-ul introdus există în baza de date
- Verifică limita de 3 email-uri/oră (Supabase free tier)
- Verifică că Redirect URL este whitelisted

#### Email-ul ajunge în Spam:
- Configurează Custom SMTP pentru producție
- Adaugă domeniul Supabase la whitelist

#### Link-ul din email nu funcționează:
- Verifică că URL-ul de redirect este corect whitelisted
- Verifică că pagina `/update-password` există

### Configurare Custom SMTP (Opțional - pentru producție)

Pentru email-uri mai fiabile, configurează un provider SMTP:

1. **Gmail SMTP**:
   - Host: `smtp.gmail.com`
   - Port: `587`
   - Username: email-ul tău Gmail
   - Password: App Password (nu parola normală)

2. **SendGrid** (recomandat):
   - Cont gratuit: 100 email-uri/zi
   - Mai fiabil decât Gmail
   - Mai puține șanse să ajungă în Spam

## Debugging

Dacă problema persistă, verifică Console-ul browser-ului pentru erori și trimite-mi screenshot-ul cu mesajele de debug.
