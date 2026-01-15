# Configurare SMS și Email pentru Expo Car Meeting

## Email Confirmation (Activat automat)

Supabase trimite automat email-uri de confirmare când un utilizator se înregistrează. Pentru a configura:

1. Mergi la **Supabase Dashboard** → **Authentication** → **Email Templates**
2. Personalizează template-ul "Confirm signup" cu mesajul tău
3. Email-ul va conține un link de confirmare automat

## SMS Verification (Necesită configurare)

Pentru a primi SMS-uri pe telefon când te înregistrezi, trebuie să configurezi un provider SMS în Supabase:

### Pași de configurare:

1. **Mergi la Supabase Dashboard**:
   - https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin

2. **Activează Phone Authentication**:
   - Click pe **Authentication** → **Providers**
   - Găsește **Phone** și activează-l

3. **Alege un SMS Provider** (recomandat: Twilio pentru început):

#### Opțiunea 1: Twilio (Cel mai popular)
   - Creează cont gratuit pe [Twilio](https://www.twilio.com/try-twilio)
   - Primești $15 credit gratuit pentru teste
   - Copiază: Account SID, Auth Token, și Phone Number
   - În Supabase, selectează **Twilio** și adaugă credențialele

#### Opțiunea 2: MessageBird
   - Creează cont pe [MessageBird](https://messagebird.com)
   - Primești credit gratuit pentru teste
   - Copiază API Key
   - În Supabase, selectează **MessageBird** și adaugă API key-ul

#### Opțiunea 3: Vonage (fost Nexmo)
   - Creează cont pe [Vonage](https://www.vonage.com)
   - Copiază API Key și API Secret
   - În Supabase, selectează **Vonage** și adaugă credențialele

4. **Testează**:
   - După configurare, încearcă să te înregistrezi cu numărul tău de telefon
   - Vei primi un SMS cu cod de 6 cifre
   - Introdu codul pentru a verifica telefonul

### Cum funcționează:

1. Utilizatorul se înregistrează cu email, parolă și telefon (opțional)
2. **Email**: Primește automat un link de confirmare
3. **Telefon** (dacă a fost adăugat): Primește SMS cu cod de 6 cifre
4. Utilizatorul confirmă email-ul (click pe link) și telefonul (introduce codul)
5. Contul este complet activat

### Note importante:

- SMS-urile costă bani după ce se termină creditul gratuit (câțiva cenți per SMS)
- Pentru testare, poți folosi doar email confirmation (gratuit)
- Formatul telefon trebuie să fie internațional: +40712345678 (pentru România)
- Twilio oferă cel mai bun raport calitate/preț pentru România

### Fără SMS Provider (doar Email):

Dacă nu vrei să configurezi SMS acum, aplicația va funcționa doar cu confirmare email:
- Utilizatorii pot lăsa câmpul telefon gol
- Vor primi doar email de confirmare
- Poți adăuga SMS mai târziu când vrei
