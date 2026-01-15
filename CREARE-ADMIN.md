# Cum să creezi un cont de admin

## Pași rapizi:

1. **Deschide Supabase SQL Editor**:
   \`\`\`
   https://supabase.com/dashboard/project/wjueefhsimrogzlwxpin/sql/new
   \`\`\`

2. **Copiază și lipește acest SQL** (înlocuiește email-ul cu al tău):

\`\`\`sql
INSERT INTO admin_users (user_id)
SELECT id FROM profiles 
WHERE email = 'email-ul-tau@example.com'
ON CONFLICT (user_id) DO NOTHING;
\`\`\`

3. **Click pe "Run"**

4. **Verifică că ești admin**:
\`\`\`sql
SELECT p.email, p.full_name, au.created_at as admin_since
FROM admin_users au
JOIN profiles p ON p.id = au.user_id
WHERE p.email = 'email-ul-tau@example.com';
\`\`\`

5. **Refresh pagina** și vei vedea link-ul către "Panou Admin" în dashboard

## Exemplu:

Dacă email-ul tău este `ion@example.com`, rulează:

\`\`\`sql
INSERT INTO admin_users (user_id)
SELECT id FROM profiles 
WHERE email = 'ion@example.com'
ON CONFLICT (user_id) DO NOTHING;
\`\`\`

După ce rulezi SQL-ul, te poți loga și vei avea acces la panoul de administrare unde poți aproba mașinile trimise de utilizatori.
