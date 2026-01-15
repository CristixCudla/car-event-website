# Configurare Google OAuth pentru EXPOCARMEETING

## Pași pentru Activarea Google Sign-In

### 1. Activează Google Provider în Supabase

**Link Direct:**
\`\`\`
https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/providers
\`\`\`

**Pași:**
1. Deschide link-ul de mai sus
2. Găsește "Google" în lista de provideri
3. Click pe toggle pentru a activa Google
4. Vei vedea două câmpuri:
   - **Client ID** (din Google Cloud Console)
   - **Client Secret** (din Google Cloud Console)

### 2. Creează Aplicație în Google Cloud Console

**Link:**
\`\`\`
https://console.cloud.google.com/apis/credentials
\`\`\`

**Pași:**
1. Mergi la Google Cloud Console
2. Creează un proiect nou sau selectează unul existent
3. Click pe "Create Credentials" → "OAuth 2.0 Client ID"
4. Selectează "Web application"
5. Adaugă **Authorized redirect URIs**:
   \`\`\`
   https://wjueefhsimrogzlwxpin.supabase.co/auth/v1/callback
   \`\`\`
6. Click "Create"
7. Copiază **Client ID** și **Client Secret**

### 3. Configurează în Supabase

1. Înapoi în Supabase (link de la pasul 1)
2. Lipește **Client ID** în câmpul corespunzător
3. Lipește **Client Secret** în câmpul corespunzător
4. Click "Save"

### 4. Testează

1. Mergi la pagina de login: `/login`
2. Click pe "Conectare cu Google"
3. Selectează contul Google
4. Vei fi redirectat automat la dashboard

## Notă Importantă

După ce utilizatorii se conectează cu Google:
- Contul lor va fi creat automat în Supabase
- Profilul va fi creat automat cu datele de la Google
- Nu mai este nevoie de confirmare email
- Utilizatorii pot accesa imediat dashboard-ul

## Troubleshooting

**Eroare: "redirect_uri_mismatch"**
- Verifică că URL-ul de redirect din Google Cloud Console este exact:
  `https://wjueefhsimrogzlwxpin.supabase.co/auth/v1/callback`

**Butonul nu funcționează:**
- Verifică că Google provider este activat în Supabase
- Verifică că Client ID și Secret sunt corecte
