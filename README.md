# 🐦 Twitter da Madeira - Frontend (Cliente)

Este repositório contém a aplicação cliente (Frontend) para a plataforma **Twitter da Madeira**, desenvolvida com **React**, **TypeScript** e **Vite**. A aplicação replica os fluxos interactivos de rede social do Twitter/X, contendo feed, gestão de temas (claro/escuro), carregamento dinâmico de publicações, secção de likes/comentários e um painel de administração (Backoffice).

---

## 🛠️ Stack Tecnológica

* **Framework:** React 19
* **Linguagem:** TypeScript
* **Ambiente de Build/Dev:** Vite
* **Estilização:** Bootstrap 5 & CSS Personalizado (Custom Themes)
* **Rotas:** React Router DOM (v7)
* **Comunicação de Rede:** Axios
* **Visualização de Dados:** Recharts (utilizado no painel de administração)

---

## 🚀 Como Executar Localmente

### Pré-requisitos
* **Node.js** (v16.x ou superior recomendado)
* **npm** ou outro gestor de pacotes

### Passos de Instalação
1. Acede à pasta raiz do frontend:
   ```bash
   cd FrontEnd
   ```
2. Instale as dependências:
   ```bash
   npm install
   ```
3. Crie e configure o ficheiro `.env` conforme indicado na secção abaixo.
4. Inicie o servidor de desenvolvimento do Vite:
   ```bash
   npm run dev
   ```
   A aplicação cliente abrirá no teu navegador em `http://localhost:5173`.

---

## ⚙️ Variável de Ambiente (`.env`)

Cria um ficheiro `.env` na pasta raiz do frontend (`FrontEnd/.env`) para definir o endereço da API do teu backend.

> [!IMPORTANT]
> **Atenção ao Nome da Chave:**
> O código do frontend lê especificamente a variável **`VITE_API_BASE_URL`**. Se utilizares outro nome (como `VITE_API_URL`), a aplicação não a detetará e tentará comunicar por padrão com `http://localhost:3000`.

* **Cenário A: Para desenvolvimento local (com backend corrido na tua máquina):**
  ```env
  VITE_API_BASE_URL=http://localhost:3000
  ```
* **Cenário B: Para produção (com backend corrido no Render.com):**
  ```env
  VITE_API_BASE_URL=https://backend-p2.onrender.com
  ```

---

## 🏗️ Funcionalidades Implementadas no Frontend

### 1. Autenticação e Rotas Protegidas
* **Formulários de Registo e Login:** Com validações de campos e mensagens de feedback.
* **Persistência de Sessão:** O token JWT é guardado no `localStorage`.
* **Guardas de Rota (`ProtectedRoute.tsx`):** Impede que utilizadores não autenticados acedam ao feed, e restringe o acesso ao Painel de Administração apenas a utilizadores com o cargo (`role`) de administrador (`admin`).

### 2. Feed e Interações Reativas
* **Feed Dinâmico:** Alterna dinamicamente entre o "Feed Geral" e o feed de publicações de utilizadores que estás a seguir ("Estou a seguir").
* **Publicação com Imagem:** Formulário reativo para escrever posts (limite de 280 caracteres) com preview e upload de imagem.
* **Atualizações Otimistas:** Os likes e a contagem são atualizados de forma instantânea na interface para uma experiência ágil.
* **Componente de Comentários:** Secção colapsável integrada no card do tweet para visualizar e adicionar novos comentários de forma rápida.

### 3. Gestão de Temas (Tema Escuro / Light Theme)
* Utiliza um `ThemeContext` global que injeta classes CSS no `body` da aplicação.
* Permite mudar instantaneamente entre o modo Claro (Light) e Escuro (Dark) através do menu lateral, persistindo o estado do tema.

### 4. Backoffice de Administração (Dashboard)
* **Gestão de Utilizadores:** Tabela interativa para listar, alterar o cargo (Admin/User), editar dados ou apagar permanentemente utilizadores.
* **Gestão de Tweets:** Painel de auditoria para editar texto, remover anexos de imagens ou apagar publicações inadequadas.
* **Métricas em Gráficos:** Utiliza o Recharts para apresentar estatísticas de crescimento da plataforma.

---

## 📂 Estrutura do Código (`src/`)

```text
src/
├── components/            # Componentes reutilizáveis e páginas da aplicação
│   ├── AdminTweets.tsx    # Painel de Gestão de Tweets no Backoffice
│   ├── AdminUsers.tsx     # Painel de Gestão de Utilizadores
│   ├── Feed.tsx           # Feed principal (Geral vs A seguir)
│   ├── LeftMenu.tsx       # Barra lateral de navegação e controlo de tema/logout
│   ├── Login.tsx          # Página de login
│   ├── Register.tsx       # Página de registo
│   ├── Tweet.tsx          # Card de tweet individual (Likes, Follows, Comentários)
│   └── ProtectedRoute.tsx # Componente protetor de rotas
├── config/                # Ficheiros de configuração da aplicação
├── db/                    # Dados estáticos/mockups locais (fallback)
├── services/              # Configuração do Axios para comunicação de rede (api.ts)
├── styles/                # Temas Bootstrap e CSS customizado para Light/Dark
├── App.tsx                # Definição de rotas e estrutura principal
└── main.tsx               # Ponto de entrada do React
```

---

## 🔐 Controlo de Acesso e Utilizadores de Teste

Para testar todas as funcionalidades do projeto, incluindo o painel de administração (Dashboard), pode utilizar as seguintes contas de teste configuradas na base de dados:

### 👑 Administrador
- **E-mail:** `admin@gmail.com`
- **Palavra-passe:** `admin123`
- *Permissões:* Acesso total ao Feed e ao Painel de Administração (Backoffice).

### 👥 Utilizadores Comuns

- **Utilizador 1:**
  - **E-mail:** `joao@gmail.com`
  - **Palavra-passe:** `joao123`

> 📝 **Nota:** Se desejar, também poderá registar um novo utilizador diretamente na aplicação através do formulário de registo.

---

## 👥 Autores e Desenvolvedores

Este projeto foi elaborado como parte da avaliação académica na Universidade.

- **Desenvolvedores:**
  - Jlcdias ([@Jlcdias](https://github.com/Jlcdias))
  - Catarina Faria ([@catarinasdfaria](https://github.com/catarinasdfaria))
- **Agradecimentos:** Ao corpo docente da disciplina de Front-End pelo apoio e orientações fornecidas ao longo do desenvolvimento.
