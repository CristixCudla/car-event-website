# Rulare Locală în Visual Studio Code

## Pasul 1: Descarcă Codul

**Opțiunea A - Download ZIP:**
1. În v0, click pe cele 3 puncte (⋮) sus-dreapta
2. Click "Download ZIP"
3. Extrage ZIP-ul într-un folder (ex: `C:\Projects\expocarmeeting`)

**Opțiunea B - GitHub (recomandat):**
1. În v0, click pe iconița GitHub sus-dreapta
2. Push to GitHub
3. Clone repository-ul local:
   \`\`\`bash
   git clone [URL-ul-repository-ului]
   \`\`\`

## Pasul 2: Deschide în VS Code

1. Deschide Visual Studio Code
2. File → Open Folder
3. Selectează folderul cu codul

## Pasul 3: Instalează Node.js (dacă nu ai)

1. Descarcă de la: https://nodejs.org/
2. Instalează versiunea LTS (Long Term Support)
3. Verifică instalarea:
   \`\`\`bash
   node --version
   npm --version
   \`\`\`

## Pasul 4: Instalează Dependențele

Deschide terminalul în VS Code (Ctrl + `) și rulează:

\`\`\`bash
npm install
\`\`\`

Așteaptă 1-2 minute până se instalează toate pachetele.

## Pasul 5: Configurează Environment Variables

Creează un fișier `.env.local` în root-ul proiectului cu următoarele valori:

\`\`\`env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=https://wjueefhsimrogzlwxpin.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=[cheia ta anon key din Supabase]

# Redirect URL pentru development
NEXT_PUBLIC_DEV_SUPABASE_REDIRECT_URL=http://localhost:3000

# Database (opțional - pentru scripturi SQL)
POSTGRES_URL=[URL-ul din Supabase]
\`\`\`

**Unde găsești cheile:**
1. Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/settings/api
2. Copiază:
   - Project URL → `NEXT_PUBLIC_SUPABASE_URL`
   - anon/public key → `NEXT_PUBLIC_SUPABASE_ANON_KEY`

## Pasul 6: Rulează Aplicația

În terminal, rulează:

\`\`\`bash
npm run dev
\`\`\`

Vei vedea:
\`\`\`
✓ Ready in 2.5s
○ Local:   http://localhost:3000
\`\`\`

## Pasul 7: Accesează Site-ul

Deschide browser-ul și mergi la: **http://localhost:3000**

## 🎉 Gata!

Site-ul rulează local pe calculatorul tău. Orice modificări în cod se vor reflecta automat în browser (hot reload).

## Comenzi Utile

\`\`\`bash
# Rulează aplicația în modul development
npm run dev

# Oprește serverul
Ctrl + C în terminal

# Construiește pentru producție
npm run build

# Rulează versiunea de producție
npm start
\`\`\`

## Partajare cu Prietenii (Opțional)

Dacă vrei ca prietenii să acceseze site-ul în timp ce rulează local:

**Opțiunea 1 - ngrok (recomandat):**
\`\`\`bash
npx ngrok http 3000
\`\`\`
Primești un link public temporar (ex: `https://abc123.ngrok.io`)

**Opțiunea 2 - localtunnel:**
\`\`\`bash
npx localtunnel --port 3000
\`\`\`

**Opțiunea 3 - Hamachi:**
1. Instalează Hamachi pe calculatorul tău și al prietenilor
2. Creează o rețea VPN
3. Prietenii accesează: `http://[IP-ul-tau-Hamachi]:3000`
4. Trebuie să configurezi firewall-ul să permită portul 3000

## Troubleshooting

**Eroare "Port 3000 is already in use":**
\`\`\`bash
# Windows
netstat -ano | findstr :3000
taskkill /PID [numărul procesului] /F

# Mac/Linux
lsof -ti:3000 | xargs kill
\`\`\`

**Eroare "Module not found":**
\`\`\`bash
rm -rf node_modules package-lock.json
npm install
\`\`\`

**Eroare Supabase connection:**
- Verifică că ai pus corect cheile în `.env.local`
- Restart serverul după modificarea `.env.local`
