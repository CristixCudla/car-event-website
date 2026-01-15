# Configurare Email Notificari

Sistemul de email notificari este deja implementat, dar momentan ruleaza in "demo mode" (afiseaza in console in loc sa trimita email-uri reale).

## Pentru Email-uri Reale (Recomandat: Resend)

### Pasul 1: Creaza Cont Resend (Gratuit)

1. Mergi la: https://resend.com/signup
2. Sign up (gratuit - 100 email-uri/zi, 3000/luna)
3. Verifica email-ul

### Pasul 2: Obtine API Key

1. In Resend Dashboard, mergi la **API Keys**
2. Click **Create API Key**
3. Nume: "EXPOCARMEETING Notifications"
4. Copiaza API key-ul (incepe cu `re_...`)

### Pasul 3: Adauga in v0

In v0, mergi la **Vars** (sidebar) si adauga:

\`\`\`
RESEND_API_KEY=re_xxxxxxxxxxxxxxxxxx
\`\`\`

### Pasul 4: Actualizeaza Codul

Instaleaza Resend in proiect:
\`\`\`bash
npm install resend
\`\`\`

Apoi actualizeaza `app/api/send-email/route.ts` sa foloseasca Resend in loc de demo mode.

## Cum Functioneaza Acum

Cand accepți/respingi o masina:
1. Utilizatorul primeste notificare WhatsApp (daca are telefon)
2. Utilizatorul primeste email (la adresa din profil)
3. Utilizatorul vede notificare in dashboard (clopotel)

## Testare

Pentru a testa email-urile in demo mode:
1. Accepta o masina din admin panel
2. Verifica console-ul browser-ului (F12)
3. Vei vedea: "Email would be sent to: [email]"

Pentru email-uri reale, configureaza Resend mai sus.
