# Como instalar o app Projetos de Engenharia

Você mesmo instala o app, em contas **suas**, e os seus dados ficam só com você.

> **Manual completo, com todos os detalhes:** [Manual-de-Instalacao.pdf](Manual-de-Instalacao.pdf). Este resumo é a versão curta.

**O que você precisa:**
- uns 20 minutos;
- um computador com Windows 10 ou 11 (de preferência o do escritório);
- um e-mail da empresa;
- um cartão de crédito. O servidor custa cerca de **US$ 7 por mês**, cobrados pelo Render; o banco de dados tem plano grátis.

O app tem duas partes, e o instalador monta as duas:

- **Online:** abre em qualquer lugar (celular, obra, 4G). Fica no **Render**, com os dados no **Supabase**.
- **No computador do escritório:** mais rápido na rede interna. Usa os mesmos dados do online.

---

## 1. Criar as contas

1. **Supabase** (https://supabase.com): crie a conta, confirme o e-mail e crie a organização com o plano **Free**. Não precisa criar projeto.
2. **Render** (https://render.com): crie a conta e cadastre o cartão em **Billing**.

## 2. Gerar as duas chaves de acesso

1. **Supabase:** https://supabase.com/dashboard/account/tokens → **Generate new token** → copie (começa com `sbp_`).
2. **Render:** https://dashboard.render.com/u/settings#api-keys → **Create API Key** → copie (começa com `rnd_`).

As chaves são secretas: cole só no instalador. Ele não guarda nenhuma delas.

## 3. Rodar o instalador

1. Rode o **Instalar-ProjetosEngenharia.exe**. Se o Windows mostrar "O Windows protegeu o computador", clique em **Mais informações → Executar assim mesmo**.
2. Escolha **Primeira instalação: criar o app online e o banco de dados agora**.
3. Preencha:
   - o nome da empresa;
   - as 2 chaves;
   - o usuário e a senha do **gestor** do app.
4. Clique em **Criar e instalar** e espere de 5 a 10 minutos. O instalador:
   - cria o banco de dados no Supabase;
   - põe o app no ar no Render;
   - cria o seu usuário gestor.
5. **Último passo:** o instalador abre a página do seu app no Render. Copie o **Deploy Hook** (em Settings) e cole no instalador. É isso que ativa o botão de atualizar.
6. Confirme o nome e a pasta e clique em **Instalar**. No fim ficam **dois atalhos** na Área de Trabalho:
   - **(online)** abre o app de qualquer lugar;
   - **(local)** abre o app deste computador.
7. **Apague as 2 chaves** nos sites (Supabase: Access Tokens; Render: API Keys). Elas não servem mais.

Se der erro no meio (cartão, internet), corrija e rode o instalador de novo. Ele **continua de onde parou**, sem criar nada duas vezes.

## 4. Primeiro uso

1. Entre no app com o usuário gestor.
2. Em **Gestão → 🏢 Empresa**, cadastre o nome, o logo e os dados do carimbo das pranchas.
3. Em **Gestão → 👥 Usuários**, cadastre a sua equipe. Tenha pelo menos 2 gestores.
4. Nas **🗄️ Bases de dados** de Muros e de Revestimentos, confira os preços e os materiais da empresa.
5. Em **Gestão → ⚙️ Sistema**, mande os endereços para a equipe pelo WhatsApp.

## 5. Atualizações

Quando sair uma versão nova, o card **Gestão** do menu mostra **🆕 Atualização disponível**.

1. Clique no aviso. Ele abre **Gestão → ⚙️ Sistema**, com a lista do que mudou.
2. Clique em **⬇️ Atualizar o online**. O app fica fora do ar por 1 a 3 minutos e volta na versão nova. Os seus dados não são afetados.
3. No app local, vá em **Gestão → ⚙️ Sistema → ⬇️ Atualizar este computador**.

Se no lugar do botão aparecer **🔗 Ativar o botão de atualizar**, cole ali o Deploy Hook do Render (Settings → Deploy Hook).

## 6. App em outro computador (opcional)

1. No app online, abra **Gestão → ⚙️ Sistema** e clique em **🔑 Gerar código de instalação**. O código vale 48 horas.
2. No outro computador, rode o instalador e escolha **O app online da empresa já existe: instalar só neste computador**.
3. Informe o endereço do app online e o código.

---

Não pode usar o instalador (por exemplo, sem Windows)? O apêndice do manual em PDF explica a instalação manual, pelo navegador.

*O app é licenciado para uso da sua empresa. Não é permitido copiar, revender ou redistribuir o app nem o seu código.*
