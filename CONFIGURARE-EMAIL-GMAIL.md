# Configurare Email Notifications cu Gmail

Pentru ca notificarile email sa functioneze, trebuie sa configurezi Gmail SMTP.

## Pasul 1: Genereaza App Password pentru Gmail

1. Mergi la: https://myaccount.google.com/security
2. Activeaza **2-Step Verification** (daca nu e deja activat)
3. Dupa activare, mergi la: https://myaccount.google.com/apppasswords
4. Selecteaza:
   - **App**: Mail
   - **Device**: Other (Custom name) - scrie "EXPOCARMEETING"
5. Click **Generate**
6. Vei primi un cod de 16 caractere (ex: `abcd efgh ijkl mnop`)
7. Copiaza acest cod (fara spatii)

## Pasul 2: Adauga Variabilele in v0

In v0, mergi la **Vars** (sidebar stanga) si adauga:

\`\`\`
EMAIL_USER=cudlacristi123@gmail.com
EMAIL_PASSWORD=abcdefghijklmnop
\`\`\`

(Inlocuieste cu email-ul tau si App Password-ul generat)

## Pasul 3: Testeaza

1. Inscrie o masina
2. Accepta-o din admin panel
3. Utilizatorul va primi email cu:
   - Detalii masina (marca, model, an, culoare, descriere)
   - Poza masinii
   - Template HTML frumos cu gradient header

## Notificarile Includ:

### Email Acceptare:
- Subiect: "🎉 Masina Ta A Fost Acceptata - EXPOCARMEETING"
- Continut: Detalii complete + poza + mesaj de felicitare

### Email Respingere:
- Subiect: "❌ Masina Ta A Fost Respinsa - EXPOCARMEETING"
- Continut: Detalii complete + poza + motiv respingere (daca exista)

## Limite Gmail:

- **500 email-uri/zi** pentru conturi Gmail gratuite
- Pentru evenimente mari, considera upgrade la Google Workspace sau alt serviciu email
