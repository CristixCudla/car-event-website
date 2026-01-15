# Fix WhatsApp Notificari - Problema cu Numarul de Telefon

## Problema

Utilizatorii nu primesc notificari WhatsApp pentru ca numarul de telefon nu este salvat in tabelul `profiles`.

## Solutie

Trebuie sa rulezi 2 scripturi SQL in Supabase:

### 1. Repara Functia de Creare Profile (pentru viitor)

Mergi la: https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/sql/new

Ruleaza:

\`\`\`sql
-- Repara functia sa copieze si numarul de telefon
CREATE OR REPLACE FUNCTION public.handle_new_user()
RETURNS TRIGGER AS $$
BEGIN
  INSERT INTO public.profiles (id, email, full_name, phone)
  VALUES (
    NEW.id,
    NEW.email,
    COALESCE(NEW.raw_user_meta_data->>'full_name', ''),
    COALESCE(NEW.raw_user_meta_data->>'phone', '')
  );
  RETURN NEW;
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;
\`\`\`

### 2. Repara Profilurile Existente (pentru utilizatorii actuali)

Ruleaza:

\`\`\`sql
-- Copiaza numerele de telefon din auth.users la profiles
UPDATE profiles
SET phone = COALESCE(
  (SELECT raw_user_meta_data->>'phone' FROM auth.users WHERE id = profiles.id),
  ''
)
WHERE phone IS NULL OR phone = '';
\`\`\`

### 3. Verifica ca a Functionat

Ruleaza:

\`\`\`sql
-- Verifica profilurile cu numere de telefon
SELECT 
  p.email,
  p.phone,
  u.raw_user_meta_data->>'phone' as phone_in_metadata
FROM profiles p
JOIN auth.users u ON u.id = p.id
WHERE p.phone IS NOT NULL AND p.phone != '';
\`\`\`

## Testare

1. Ruleaza cele 2 scripturi SQL de mai sus
2. Inscrie o masina (sau foloseste una existenta)
3. Accepta masina din admin panel
4. Utilizatorul va primi notificare WhatsApp!

## Pentru Utilizatori Noi

De acum inainte, cand un utilizator nou se inregistreaza si completeaza numarul de telefon, acesta va fi salvat automat in tabelul `profiles` si va primi notificari WhatsApp.
