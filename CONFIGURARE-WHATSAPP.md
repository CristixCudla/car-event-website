# Configurare Notificari WhatsApp pentru EXPOCARMEETING

## Ce Primeste Utilizatorul:

Cand accepți/respingi o masina, utilizatorul primeste automat:
1. **Notificare in-app** (clopoțel in dashboard)
2. **Notificare WhatsApp** (mesaj direct pe telefon)

## Setup Twilio WhatsApp (15 minute):

### Pasul 1: Creează Cont Twilio

1. Mergi la: https://www.twilio.com/try-twilio
2. Înregistrează-te (gratuit - primești $15 credit)
3. Verifică email-ul și numărul de telefon

### Pasul 2: Activează WhatsApp Sandbox

1. În Twilio Console, mergi la: **Messaging** → **Try it out** → **Send a WhatsApp message**
2. Vei vedea un număr WhatsApp Twilio (ex: +1 415 523 8886)
3. Vei vedea un cod (ex: "join abc-def")
4. **Pe telefonul tău**: Trimite mesaj WhatsApp la numărul Twilio cu codul
5. Vei primi confirmare că sandbox-ul e activ

### Pasul 3: Obține Credențialele

1. În Twilio Console, mergi la: **Account** → **API keys & tokens**
2. Copiază:
   - **Account SID** (ex: ACxxxxxxxxxxxxx)
   - **Auth Token** (click "Show" pentru a-l vedea)
3. Numărul WhatsApp Twilio (din Pasul 2, format: whatsapp:+14155238886)

### Pasul 4: Adaugă în Vercel

1. Mergi la: https://vercel.com/dashboard
2. Selectează proiectul EXPOCARMEETING
3. Settings → Environment Variables
4. Adaugă:
   \`\`\`
   TWILIO_ACCOUNT_SID=ACxxxxxxxxxxxxx
   TWILIO_AUTH_TOKEN=your_auth_token_here
   TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886
   \`\`\`
5. Click "Save"
6. Redeploy aplicația

### Pasul 5: Testează

1. Asigură-te că utilizatorul are număr de telefon în profil (format: +40712345678)
2. Acceptă o mașină în admin panel
3. Utilizatorul primește mesaj WhatsApp instant!

## Costuri:

- **Sandbox (Gratuit)**: Pentru testare, max 5 numere
- **Production**: $0.005 per mesaj (1 leu = ~200 mesaje)
- **Credit gratuit**: $15 la început = ~3000 mesaje

## Limitări Sandbox:

- Max 5 numere pot primi mesaje
- Fiecare număr trebuie să trimită "join abc-def" înainte
- Pentru producție, trebuie să aplici pentru WhatsApp Business API (verificare business)

## Upgrade la Production:

Când vrei să trimiți la oricine (nu doar 5 numere):
1. Aplică pentru WhatsApp Business API în Twilio
2. Verificare business (1-2 zile)
3. Creează template-uri de mesaje (trebuie aprobate de Meta)
4. Costă ~$0.005 per mesaj

## Mesajele Trimise:

**Acceptat:**
\`\`\`
🎉 EXPOCARMEETING: Masina ta BMW M3 (2023) a fost acceptata pentru eveniment! Te asteptam!
\`\`\`

**Respins:**
\`\`\`
EXPOCARMEETING: Masina ta BMW M3 (2023) a fost respinsa. Contacteaza organizatorii pentru detalii.
\`\`\`

## Troubleshooting:

**Mesajul nu ajunge:**
- Verifică că numărul e în format internațional: +40712345678
- Verifică că utilizatorul a trimis "join abc-def" la numărul Twilio
- Verifică logs în Twilio Console → Monitor → Logs

**Eroare "not configured":**
- Verifică că ai adăugat toate 3 variabilele de mediu în Vercel
- Redeploy aplicația după ce adaugi variabilele
