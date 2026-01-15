# Configurare SMS cu Twilio pentru Supabase (5 minute)

## Pasul 1: Creează cont Twilio (GRATUIT pentru testare)

1. Mergi la: **https://www.twilio.com/try-twilio**
2. Completează formularul cu:
   - Email-ul tău
   - Parolă
   - **Selectează România** ca țară
3. Verifică email-ul și confirmă contul
4. La întrebarea "What do you want to do?" → Selectează **"Send SMS"**

## Pasul 2: Obține credențialele Twilio

După ce te loghezi în Twilio:

1. Vei vedea **Dashboard-ul** cu:
   - **Account SID** (ceva gen: ACxxxxxxxxxxxxx)
   - **Auth Token** (click pe "Show" pentru a-l vedea)
   
2. **COPIAZĂ** ambele valori (le vei folosi în pasul următor)

3. **Obține un număr de telefon Twilio**:
   - Click pe **"Get a Trial Number"** (buton roșu mare)
   - Twilio îți va da un număr gratuit pentru testare
   - Click **"Choose this Number"**
   - **COPIAZĂ** acest număr (ex: +1234567890)

## Pasul 3: Configurează în Supabase

1. Mergi la: **https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/providers**

2. Scroll jos până găsești secțiunea **"Phone"**

3. Click pe **"Enable Phone provider"** (toggle-ul să fie verde)

4. În secțiunea **"SMS Provider"**, selectează **"Twilio"**

5. Completează câmpurile:
   - **Twilio Account SID**: (lipește Account SID de la pasul 2)
   - **Twilio Auth Token**: (lipește Auth Token de la pasul 2)
   - **Twilio Message Service SID**: (lasă gol pentru acum)
   - **Twilio Phone Number**: (lipește numărul de telefon de la pasul 2)

6. Click **"Save"**

## Pasul 4: Testează

1. Mergi pe site-ul tău Expo Car Meeting
2. Înregistrează-te cu un număr de telefon românesc (ex: +40712345678)
3. Ar trebui să primești SMS cu codul de verificare!

## Note Importante:

- **Cont Trial Twilio**: Poți trimite SMS-uri DOAR la numere verificate în Twilio
- Pentru a verifica numărul tău de telefon în Twilio:
  1. Mergi la: https://console.twilio.com/us1/develop/phone-numbers/manage/verified
  2. Click **"Add a new number"**
  3. Introdu numărul tău românesc cu +40
  4. Vei primi un cod de verificare
  5. După verificare, poți primi SMS-uri pe acel număr

- **Pentru producție** (SMS-uri către orice număr):
  - Trebuie să upgradeezi contul Twilio (adaugi card)
  - Costă ~$0.0075 per SMS în România
  - Primești $15 credit gratuit la început

## Probleme comune:

**"Nu primesc SMS"**:
- Verifică că numărul tău e verificat în Twilio (vezi mai sus)
- Verifică că ai introdus corect credențialele în Supabase
- Verifică că numărul de telefon e în format internațional (+40...)

**"Error 21608"**:
- Numărul nu e verificat în Twilio Trial account
- Soluție: Verifică numărul în Twilio Console

**"Invalid phone number"**:
- Asigură-te că numărul începe cu +40 pentru România
- Format corect: +40712345678 (fără spații)
\`\`\`

\`\`\`typescript file="" isHidden
