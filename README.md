# Como instalar o app Projetos de Engenharia

Você mesmo instala o app, em contas **suas**, e os seus dados ficam só com você.

**O que você precisa:**
- uns 30 minutos;
- um e-mail da empresa;
- um cartão de crédito. O servidor custa cerca de **US$ 7 por mês**, cobrados pelo Render; o banco de dados tem plano grátis.

O app tem duas partes:

- **Online:** abre em qualquer lugar (celular, obra, 4G). Fica no **Render**, com os dados no **Supabase**.
- **No computador do escritório (opcional):** mais rápido na rede interna. Usa os mesmos dados do online.

---

## 1. Banco de dados e arquivos (Supabase, grátis)

1. Entre em https://supabase.com e crie uma conta (*Start your project*).
2. Clique em **New project**:
   - **Name:** o nome da sua empresa.
   - **Database Password:** crie uma senha forte e **anote**. Você vai usar no passo 3.
   - **Region:** **East US (North Virginia)**, a mesma região do servidor do passo 2, para o app ficar rápido.
   - Clique em **Create new project** e espere uns 2 minutos.
3. No topo do projeto, clique em **Connect**:
   - escolha **Transaction pooler** (é a que funciona com o Render);
   - copie o endereço que começa com `postgresql://`;
   - troque `[YOUR-PASSWORD]` pela senha que você anotou.
   - Esse é o valor **DATABASE_URL**.
4. Em **Project Settings → API Keys**, copie:
   - a **Project URL** (ex.: `https://abcdxyz.supabase.co`), que é o valor **SUPABASE_URL**;
   - a chave **service_role**, que é o valor **SUPABASE_KEY**. Ela fica em *Legacy API Keys*, se aparecer essa aba; nas versões novas é a chave *secret*.
   - Essa chave é secreta: não mande por WhatsApp nem e-mail.

A pasta de arquivos (PDFs, modelos 3D) é criada sozinha pelo app, e não precisa mexer em mais nada no Supabase.

> O plano grátis do Supabase **pausa o banco se ficar 1 semana sem uso**. Usando o app no dia a dia, isso não acontece. Para ter **backup diário automático**, use o plano **Pro** (US$ 25/mês).

## 2. O app online (Render, cerca de US$ 7/mês)

1. Entre em https://render.com e crie uma conta. Em **Billing**, cadastre o cartão.
2. Clique em **New → Web Service** e escolha **Existing Image**.
3. Em **Image URL**, cole: `ghcr.io/projetosequipepremium-commits/projetos-engenharia:latest` e clique em **Connect**.
4. Preencha:
   - **Name:** o nome da sua empresa, sem espaços (ex.: `construtora-silva`). Ele vira o endereço do app: `https://construtora-silva.onrender.com`.
   - **Region:** **Virginia (US East)**.
   - **Instance Type:** **Starter**. O *Free* "dorme" quando fica sem uso e demora quase 1 minuto para abrir.
5. Em **Environment Variables**, adicione as 3 que você copiou do Supabase:

| Nome (NAME) | Valor (VALUE) |
|---|---|
| `DATABASE_URL` | o endereço `postgresql://...` (passo 1.3) |
| `SUPABASE_URL` | a Project URL (passo 1.4) |
| `SUPABASE_KEY` | a chave service_role (passo 1.4) |

6. Clique em **Deploy Web Service** e espere aparecer **Live** (uns 5 minutos).
7. **Ative o botão de atualizar:**
   1. no Render, abra **Settings → Deploy Hook** e copie o endereço;
   2. vá em **Environment → Edit → + Add Environment Variable**: nome `RENDER_DEPLOY_HOOK_URL`, valor o endereço copiado;
   3. clique em **Save, rebuild, and deploy**.

## 3. Primeiro acesso

1. Abra o endereço do seu app (ex.: `https://construtora-silva.onrender.com`).
2. Aparece a tela **Primeiro acesso**: crie o usuário **gestor** (usuário e senha). **Faça isso logo depois de instalar**, porque o primeiro a acessar vira o gestor.
3. Em **Gestão → 🏢 Empresa**, cadastre o nome da empresa, o logo e os dados do carimbo das pranchas.
4. Em **Gestão → 👥 Usuários**, cadastre a sua equipe.
5. Em **Muros e Terraplanagem → 🗄️ Base de dados**, confira os preços e padrões da sua empresa.

## 4. Atualizações

Quando sair uma versão nova, o card **Gestão** do menu mostra **🆕 Atualização disponível**.

1. Clique no aviso. Ele abre **Gestão → ⚙️ Sistema**, com a lista do que mudou.
2. Clique em **⬇️ Atualizar o online**. O app fica fora do ar por 1 a 3 minutos e volta na versão nova. Os seus dados não são afetados.

## 5. App no computador do escritório (opcional)

1. No app online, abra **Gestão → ⚙️ Sistema**:
   - clique em **⬇️ Baixar o instalador**;
   - clique em **🔑 Gerar código de instalação**. O código vale 48 horas e serve para vários computadores.
2. No computador do escritório, rode o **Instalar-ProjetosEngenharia.exe**. Se o Windows mostrar "O Windows protegeu o computador", clique em **Mais informações → Executar assim mesmo**.
3. Informe o **endereço do app online** e o **código**. Depois confirme o nome da empresa e a pasta.
4. O instalador cria dois atalhos na Área de Trabalho: **(local)**, para este computador, e **(online)**, para o endereço do Render.
   - O app local sobe junto com o Windows.
   - Os outros computadores da rede entram pelo endereço que aparece em **Gestão → ⚙️ Sistema**.
5. **Para atualizar:** primeiro atualize o online. Depois, no app local, vá em **Gestão → ⚙️ Sistema → ⬇️ Atualizar este computador**.

---

*O app é licenciado para uso da sua empresa. Não é permitido copiar, revender ou redistribuir o app nem o seu código.*
