# Quick Start: Activează SMS în 3 Pași

## 1️⃣ Creează cont Twilio (2 minute)
- Mergi la: https://www.twilio.com/try-twilio
- Înregistrează-te (GRATUIT)
- Verifică email-ul

## 2️⃣ Obține credențialele (1 minut)
După login în Twilio Dashboard:
- Copiază **Account SID** (ex: ACxxxxx...)
- Copiază **Auth Token** (click "Show")
- Click **"Get a Trial Number"** → Copiază numărul

## 3️⃣ Configurează în Supabase (1 minut)
- Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/providers
- Activează **"Phone"** provider
- Selectează **"Twilio"**
- Lipește:
  - Account SID
  - Auth Token  
  - Phone Number
- Click **"Save"**

## ✅ Testează
- Verifică numărul tău în Twilio: https://console.twilio.com/us1/develop/phone-numbers/manage/verified
- Înregistrează-te pe site cu numărul verificat
- Primești SMS cu cod!

## 💡 Important
**Cont Trial**: SMS-uri doar către numere verificate în Twilio
**Producție**: Upgrade cont (primești $15 credit gratuit)

---

**Probleme?** Vezi ghidul complet: `CONFIGURARE-SMS-TWILIO.md`
