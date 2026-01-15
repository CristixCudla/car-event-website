# Configurare Expo Car Meeting

## 1. Adaugă Variabilele de Mediu

Trebuie să adaugi următoarele variabile în secțiunea **"Vars"** din sidebar-ul din stânga:

### Variabile Necesare:

1. **NEXT_PUBLIC_SUPABASE_URL**
   - Valoare: Copiază din Supabase Dashboard → Settings → API → Project URL
   - Exemplu: `https://xxxxx.supabase.co`

2. **NEXT_PUBLIC_SUPABASE_ANON_KEY**
   - Valoare: Copiază din Supabase Dashboard → Settings → API → anon/public key
   - Exemplu: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...`

### Cum să adaugi variabilele:

1. Deschide **sidebar-ul din stânga** în chat
2. Click pe **"Vars"** (secțiunea de variabile de mediu)
3. Click pe **"Add Variable"**
4. Adaugă fiecare variabilă cu numele și valoarea corespunzătoare
5. Salvează modificările

## 2. Rulează Scripturile SQL

După ce ai adăugat variabilele, rulează scripturile SQL în Supabase:

1. Mergi la [Supabase Dashboard](https://supabase.com/dashboard)
2. Selectează proiectul tău
3. Click pe **SQL Editor** din meniul lateral
4. Rulează scripturile în ordine:
   - `scripts/01-create-tables.sql`
   - `scripts/02-create-functions.sql`
   - `scripts/04-create-storage-bucket.sql`

## 3. Creează Primul Admin

După ce te înregistrezi pe site, rulează în SQL Editor:

\`\`\`sql
INSERT INTO admin_users (user_id)
SELECT id FROM profiles WHERE email = 'your-email@example.com';
\`\`\`

Înlocuiește `your-email@example.com` cu email-ul tău.

## 4. Testează Site-ul

Site-ul ar trebui să funcționeze acum! Poți:
- Să te înregistrezi ca utilizator
- Să încarci mașini pentru eveniment
- Să te loghezi ca admin și să aprobi mașinile
- Să vezi mașinile aprobate pe homepage

## Funcționalități

- **Autentificare**: Login/Signup cu email și parolă
- **Dashboard Utilizator**: Încarcă poze cu mașina ta și vezi statusul
- **Panel Admin**: Aprobă sau respinge mașinile trimise
- **Background Removal**: Îndepărtează automat fundalul din pozele aprobate (gratuit, în browser)
- **Homepage Dinamic**: Afișează automat mașinile acceptate
