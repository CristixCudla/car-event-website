# Configurare Email Personalizat EXPOCARMEETING

## Pasul 1: Accesează Setările de Email în Supabase

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/templates
2. Vei vedea lista de template-uri de email (Confirm signup, Reset password, etc.)

## Pasul 2: Personalizează Template-ul "Confirm signup"

1. Click pe **"Confirm signup"**
2. Vei vedea un editor cu template-ul curent
3. **Șterge tot** conținutul existent
4. **Copiază și lipește** conținutul din `email-templates/confirmation-email.html`
5. Click pe **"Save"**

## Pasul 3: Personalizează Template-ul "Reset Password"

1. Click pe **"Reset Password"** (în aceeași pagină de templates)
2. **Șterge tot** conținutul existent
3. **Copiază și lipește** conținutul din `email-templates/reset-password-email.html`
4. Click pe **"Save"**

## Pasul 4: Personalizează Expeditorul

În aceeași pagină, mai jos vei găsi setările pentru:

- **Sender name**: Schimbă în `EXPOCARMEETING`
- **Sender email**: Lasă default sau configurează un email personalizat (ex: `noreply@expocarmeeting.ro`)

## Pasul 5: Configurează Redirect URLs

Pentru ca email-urile de resetare parolă să funcționeze:

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/url-configuration
2. La **"Redirect URLs"**, adaugă:
   - `http://localhost:3000/update-password` (pentru development)
   - URL-ul tău de producție + `/update-password` (când publici site-ul)
3. Click pe **"Save"**

## Pasul 6: (Opțional) Configurează SMTP Personalizat

Dacă vrei ca email-urile să vină de la domeniul tău (ex: `@expocarmeeting.ro`):

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/settings/auth
2. Scroll jos la **"SMTP Settings"**
3. Activează **"Enable Custom SMTP"**
4. Completează cu datele de la provider-ul tău de email (Gmail, SendGrid, Mailgun, etc.)

### Exemplu pentru Gmail:
- **Host**: `smtp.gmail.com`
- **Port**: `587`
- **Username**: `your-email@gmail.com`
- **Password**: App Password (generează unul în setările Gmail)
- **Sender email**: `noreply@expocarmeeting.ro`
- **Sender name**: `EXPOCARMEETING`

## Pasul 7: Testează

### Testează Confirmarea Contului:
1. Creează un cont nou pe site
2. Verifică email-ul - ar trebui să primești email-ul personalizat cu logo-ul EXPOCARMEETING

### Testează Resetarea Parolei:
1. Mergi la pagina de login
2. Click pe "Ai uitat parola?"
3. Introdu email-ul tău
4. Verifică email-ul - ar trebui să primești email-ul de resetare personalizat

## Note Importante

- Template-urile folosesc variabila `{{ .ConfirmationURL }}` care este înlocuită automat de Supabase cu link-ul corect
- Dacă vrei să adaugi logo-ul ca imagine (nu text), trebuie să găzduiești imaginea online și să folosești tag-ul `<img src="URL">`
- Email-urile sunt responsive și arată bine pe mobil și desktop
- Link-urile de resetare parolă sunt valabile 1 oră din motive de securitate

## Alte Template-uri de Personalizat

Poți personaliza și alte email-uri în același mod:
- **Magic Link** - pentru login fără parolă
- **Change Email Address** - când utilizatorul își schimbă email-ul
- **Invite User** - pentru invitații de utilizatori

Folosește același design pentru consistență!

## Troubleshooting

### Nu primesc email-uri:
1. Verifică spam/junk folder
2. Verifică că Redirect URLs sunt configurate corect
3. Verifică că SMTP settings sunt corecte (dacă folosești SMTP personalizat)
4. Verifică logs în Supabase Dashboard → Logs → Auth Logs

### Email-urile arată ciudat:
1. Asigură-te că ai copiat tot HTML-ul din template
2. Verifică că nu ai șters accidental variabila `{{ .ConfirmationURL }}`
3. Testează în mai multe clienți de email (Gmail, Outlook, etc.)
