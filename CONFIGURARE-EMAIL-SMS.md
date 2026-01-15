# Configurare Email si SMS pentru Expo Car Meeting

## Status Actual

✅ **Email-urile functioneaza ACUM** - Supabase trimite automat email-uri de confirmare
✅ **Numarul de telefon se salveaza** in baza de date
❌ **SMS-urile NU functioneaza** - necesita configurare provider extern

## De ce nu primesti SMS?

SMS-urile in Supabase necesita un **provider extern platit** (Twilio, MessageBird, Vonage). 
Acestea NU sunt gratuite si necesita:
1. Cont la provider SMS (ex: Twilio)
2. Card de credit pentru plati
3. Configurare API keys in Supabase Dashboard

## Cum functioneaza ACUM (fara SMS):

1. Utilizatorul se inregistreaza cu email, parola, nume si telefon
2. Supabase trimite **EMAIL de confirmare** automat
3. Utilizatorul da click pe link-ul din email
4. Contul este activat si poate face login
5. Numarul de telefon este salvat in baza de date pentru viitor

## Cum sa activezi SMS (optional, costa bani):

### Pasul 1: Creaza cont Twilio (cel mai popular)

1. Mergi la: https://www.twilio.com/try-twilio
2. Inregistreaza-te (necesita card de credit)
3. Verifica-ti contul
4. Obtine:
   - Account SID
   - Auth Token
   - Numar de telefon Twilio

### Pasul 2: Configureaza in Supabase

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/providers
2. Scroll la sectiunea **Phone**
3. Activeaza "Enable Phone Sign-up"
4. Selecteaza provider: **Twilio**
5. Adauga:
   - Twilio Account SID
   - Twilio Auth Token
   - Twilio Phone Number
6. Salveaza

### Pasul 3: Activeaza SMS in cod

Dupa ce configurezi Twilio in Supabase, SMS-urile vor functiona automat.
Codul este deja pregatit sa trimita SMS-uri cand provider-ul este configurat.

## Recomandare

**Foloseste EMAIL pentru inceput** - este gratuit si functioneaza perfect.
Adauga SMS mai tarziu doar daca ai nevoie absoluta (costa ~$0.01 per SMS).

## Verificare Email Confirmations

Pentru ca email-urile sa functioneze, verifica in Supabase Dashboard:

1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/url-configuration
2. Verifica ca "Site URL" este setat corect
3. Adauga in "Redirect URLs": 
   - http://localhost:3000/dashboard
   - URL-ul tau de productie

## Testare

1. Inregistreaza-te cu un email real
2. Verifica inbox-ul (si Spam)
3. Click pe link-ul de confirmare
4. Login cu credentialele tale
