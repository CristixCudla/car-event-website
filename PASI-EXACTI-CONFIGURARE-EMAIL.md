# Pași EXACȚI pentru a schimba email-urile de la Supabase la EXPOCARMEETING

## ⚠️ IMPORTANT: Trebuie să faci acești pași MANUAL în Supabase Dashboard!

### Pasul 1: Deschide Email Templates

**Link direct**: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/auth/templates

### Pasul 2: Schimbă Sender Name (Numele expeditorului)

1. În partea de sus a paginii, vezi "Sender email" și "Sender name"
2. La **"Sender name"**, șterge "Supabase" și scrie: **EXPOCARMEETING**
3. Click **"Save"**

### Pasul 3: Configurează Email-ul de Confirmare

1. În lista de template-uri, click pe **"Confirm signup"**
2. Șterge tot conținutul din câmpul mare de text
3. Copiază și lipește acest HTML:

\`\`\`html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Confirmă-ți Contul - EXPOCARMEETING</title>
</head>
<body style="margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif; background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);">
  <table width="100%" cellpadding="0" cellspacing="0" style="background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%); padding: 40px 20px;">
    <tr>
      <td align="center">
        <table width="600" cellpadding="0" cellspacing="0" style="background: #0f0f23; border-radius: 16px; overflow: hidden; box-shadow: 0 20px 60px rgba(0,0,0,0.5);">
          
          <!-- Header cu Logo -->
          <tr>
            <td style="background: linear-gradient(135deg, #ec4899 0%, #06b6d4 100%); padding: 40px; text-align: center;">
              <h1 style="margin: 0; font-size: 42px; font-weight: 900; background: linear-gradient(135deg, #ffffff 0%, #e0e0e0 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; letter-spacing: -1px;">
                EXPO CAR MEETING
              </h1>
              <p style="margin: 10px 0 0 0; color: rgba(255,255,255,0.9); font-size: 14px; font-weight: 500; letter-spacing: 2px;">
                BY EXPOTEAM
              </p>
            </td>
          </tr>

          <!-- Content -->
          <tr>
            <td style="padding: 50px 40px;">
              <h2 style="margin: 0 0 20px 0; color: #ffffff; font-size: 28px; font-weight: 700;">
                Bine ai venit! 🎉
              </h2>
              
              <p style="margin: 0 0 25px 0; color: rgba(255,255,255,0.8); font-size: 16px; line-height: 1.6;">
                Mulțumim că te-ai alăturat comunității <strong style="background: linear-gradient(135deg, #ec4899 0%, #06b6d4 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">EXPOCARMEETING</strong>!
              </p>

              <p style="margin: 0 0 30px 0; color: rgba(255,255,255,0.8); font-size: 16px; line-height: 1.6;">
                Pentru a-ți activa contul și a începe să participi la cele mai tari evenimente auto, te rugăm să confirmi adresa de email apăsând butonul de mai jos:
              </p>

              <!-- Buton CTA -->
              <table width="100%" cellpadding="0" cellspacing="0">
                <tr>
                  <td align="center" style="padding: 20px 0;">
                    <a href="{{ .ConfirmationURL }}" style="display: inline-block; background: linear-gradient(135deg, #ec4899 0%, #06b6d4 100%); color: #ffffff; text-decoration: none; padding: 18px 50px; border-radius: 12px; font-weight: 700; font-size: 16px; letter-spacing: 0.5px; box-shadow: 0 10px 30px rgba(236, 72, 153, 0.4); transition: transform 0.2s;">
                      CONFIRMĂ CONTUL
                    </a>
                  </td>
                </tr>
              </table>

              <p style="margin: 30px 0 0 0; color: rgba(255,255,255,0.6); font-size: 14px; line-height: 1.6;">
                Dacă nu ai creat acest cont, poți ignora acest email în siguranță.
              </p>

              <p style="margin: 20px 0 0 0; color: rgba(255,255,255,0.6); font-size: 13px; line-height: 1.6;">
                Link-ul de confirmare este valabil 24 de ore. Dacă butonul nu funcționează, copiază și lipește acest link în browser:<br>
                <span style="color: #06b6d4; word-break: break-all;">{{ .ConfirmationURL }}</span>
              </p>
            </td>
          </tr>

          <!-- Footer -->
          <tr>
            <td style="background: rgba(255,255,255,0.03); padding: 30px 40px; border-top: 1px solid rgba(255,255,255,0.1);">
              <p style="margin: 0 0 10px 0; color: rgba(255,255,255,0.5); font-size: 13px; text-align: center;">
                © 2025 EXPOCARMEETING by EXPOTEAM. Toate drepturile rezervate.
              </p>
              <p style="margin: 0; color: rgba(255,255,255,0.4); font-size: 12px; text-align: center;">
                Celebrarea Supremă Auto
              </p>
            </td>
          </tr>

        </table>
      </td>
    </tr>
  </table>
</body>
</html>
\`\`\`

4. Click **"Save"** în dreapta sus

### Pasul 4: Configurează Email-ul de Resetare Parolă

1. În lista de template-uri, click pe **"Reset password"**
2. Șterge tot conținutul din câmpul mare de text
3. Copiază și lipește acest HTML:

\`\`\`html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Resetare Parolă - EXPOCARMEETING</title>
</head>
<body style="margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif; background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);">
  <table width="100%" cellpadding="0" cellspacing="0" style="background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%); padding: 40px 20px;">
    <tr>
      <td align="center">
        <table width="600" cellpadding="0" cellspacing="0" style="background: #0f0f23; border-radius: 16px; overflow: hidden; box-shadow: 0 20px 60px rgba(0,0,0,0.5);">
          
          <!-- Header cu Logo -->
          <tr>
            <td style="background: linear-gradient(135deg, #ec4899 0%, #06b6d4 100%); padding: 40px; text-align: center;">
              <h1 style="margin: 0; font-size: 42px; font-weight: 900; background: linear-gradient(135deg, #ffffff 0%, #e0e0e0 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; letter-spacing: -1px;">
                EXPO CAR MEETING
              </h1>
              <p style="margin: 10px 0 0 0; color: rgba(255,255,255,0.9); font-size: 14px; font-weight: 500; letter-spacing: 2px;">
                BY EXPOTEAM
              </p>
            </td>
          </tr>

          <!-- Content -->
          <tr>
            <td style="padding: 50px 40px;">
              <h2 style="margin: 0 0 20px 0; color: #ffffff; font-size: 28px; font-weight: 700;">
                Resetare Parolă 🔐
              </h2>
              
              <p style="margin: 0 0 25px 0; color: rgba(255,255,255,0.8); font-size: 16px; line-height: 1.6;">
                Am primit o solicitare de resetare a parolei pentru contul tău <strong style="background: linear-gradient(135deg, #ec4899 0%, #06b6d4 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">EXPOCARMEETING</strong>.
              </p>

              <p style="margin: 0 0 30px 0; color: rgba(255,255,255,0.8); font-size: 16px; line-height: 1.6;">
                Pentru a-ți seta o parolă nouă, apasă butonul de mai jos:
              </p>

              <!-- Buton CTA -->
              <table width="100%" cellpadding="0" cellspacing="0">
                <tr>
                  <td align="center" style="padding: 20px 0;">
                    <a href="{{ .ConfirmationURL }}" style="display: inline-block; background: linear-gradient(135deg, #ec4899 0%, #06b6d4 100%); color: #ffffff; text-decoration: none; padding: 18px 50px; border-radius: 12px; font-weight: 700; font-size: 16px; letter-spacing: 0.5px; box-shadow: 0 10px 30px rgba(236, 72, 153, 0.4);">
                      RESETEAZĂ PAROLA
                    </a>
                  </td>
                </tr>
              </table>

              <!-- Security Notice -->
              <table width="100%" cellpadding="0" cellspacing="0" style="margin-top: 30px; background: rgba(236, 72, 153, 0.1); border-left: 4px solid #ec4899; border-radius: 8px;">
                <tr>
                  <td style="padding: 20px;">
                    <p style="margin: 0; color: rgba(255,255,255,0.9); font-size: 14px; line-height: 1.6;">
                      <strong>⚠️ Notă de securitate:</strong><br>
                      Dacă nu ai solicitat resetarea parolei, ignoră acest email. Parola ta va rămâne neschimbată.
                    </p>
                  </td>
                </tr>
              </table>

              <p style="margin: 30px 0 0 0; color: rgba(255,255,255,0.6); font-size: 13px; line-height: 1.6;">
                Link-ul de resetare este valabil 1 oră. Dacă butonul nu funcționează, copiază și lipește acest link în browser:<br>
                <span style="color: #06b6d4; word-break: break-all;">{{ .ConfirmationURL }}</span>
              </p>
            </td>
          </tr>

          <!-- Footer -->
          <tr>
            <td style="background: rgba(255,255,255,0.03); padding: 30px 40px; border-top: 1px solid rgba(255,255,255,0.1);">
              <p style="margin: 0 0 10px 0; color: rgba(255,255,255,0.5); font-size: 13px; text-align: center;">
                © 2025 EXPOCARMEETING by EXPOTEAM. Toate drepturile rezervate.
              </p>
              <p style="margin: 0; color: rgba(255,255,255,0.4); font-size: 12px; text-align: center;">
                Celebrarea Supremă Auto
              </p>
            </td>
          </tr>

        </table>
      </td>
    </tr>
  </table>
</body>
</html>
\`\`\`

4. Click **"Save"** în dreapta sus

### Pasul 5: Testează

1. Încearcă să te înregistrezi cu un email nou SAU
2. Încearcă funcția "Ai uitat parola?"
3. Verifică inbox-ul - acum email-ul va veni de la **EXPOCARMEETING** cu design-ul personalizat!

---

## ✅ Checklist Final

- [ ] Am schimbat "Sender name" la EXPOCARMEETING
- [ ] Am salvat template-ul "Confirm signup"
- [ ] Am salvat template-ul "Reset password"
- [ ] Am testat și primesc email-uri cu branding EXPOCARMEETING

**Dacă ai probleme, verifică că ai dat Save după fiecare modificare!**
