# Configurare Sistem de Notificări

## Ce Face Sistemul:

✅ **Notificări Automate** - Când adminul acceptă/respinge o mașină, utilizatorul primește notificare instant
✅ **Push Notifications** - Notificări în bara de notificări pe telefon (Android Chrome) și desktop
✅ **Notificări în App** - Clopoțel cu badge în dashboard care arată notificări necitite
✅ **Real-time** - Notificările apar instant fără refresh

## Cum Să Activezi:

### 1. Rulează SQL Script

Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/sql/new

Copiază și rulează scriptul din `scripts/14-add-notification-system.sql`

### 2. Testează Sistemul

1. **Înscrie o mașină** ca utilizator normal
2. **Mergi în Admin Panel** și acceptă mașina
3. **Verifică Dashboard-ul** - vei vedea notificarea în clopoțel
4. **Pe telefon** - dacă ai permis notificările, vei primi push notification

### 3. Activează Push Notifications pe Telefon

**Android Chrome:**
1. Deschide site-ul pe telefon
2. Browser-ul va cere permisiune pentru notificări
3. Apasă "Allow"
4. Gata! Vei primi notificări în bara de notificări

**iOS Safari:**
- Din păcate, Safari pe iOS nu suportă Web Push Notifications încă
- Utilizatorii iOS vor primi doar notificări în app (clopoțel)

## Cum Funcționează:

1. **Admin acceptă mașina** → Trigger SQL se activează
2. **Se creează notificare** în tabelul `notifications`
3. **Real-time subscription** detectează notificarea nouă
4. **Push notification** apare pe telefon (dacă e permis)
5. **Badge** apare pe clopoțel în dashboard
6. **Click pe notificare** → se marchează ca citită

## Caracteristici:

- 📱 **Push notifications** pe Android și desktop
- 🔔 **Badge cu număr** de notificări necitite
- ✅ **Marchează ca citit** individual sau toate deodată
- 📅 **Timestamp** pentru fiecare notificare
- 🎨 **Design frumos** cu dropdown menu
- ⚡ **Real-time** - fără refresh necesar

## Securitate:

- ✅ Row Level Security - utilizatorii văd doar notificările lor
- ✅ Trigger automat - nu poate fi manipulat de utilizatori
- ✅ Validare server-side pentru toate operațiunile
