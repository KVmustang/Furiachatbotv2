# FURIA Fan Hub - Desafio Técnico

Este projeto foi desenvolvido como parte do desafio técnico para a vaga de Assistente de Engenheiro de Software na Furia Esports.

## Visão Geral

O projeto consiste em duas partes principais:

1.  **Landing Page:** Uma página estática (`index.html`) que serve como ponto de entrada, apresentando o projeto e fornecendo um link para o chatbot.
2.  **Chatbot Furioso:** Uma aplicação Next.js com um chatbot interativo que responde a perguntas sobre a Furia, o time de CS2, história, etc. Ele utiliza Socket.IO para comunicação em tempo real com um backend Node.js.

## Links

*   **Landing Page:** https://usijmlre.manus.space
*   **Chatbot Furioso:** https://qvszcivj.manus.space

## Funcionalidades

*   **Landing Page:**
    *   Apresentação do projeto.
    *   Botão para acessar o chatbot.
    *   Design responsivo.
*   **Chatbot Furioso:**
    *   Interface de chat com abas (Chatbot, Time CS2, Quiz Furia).
    *   Comunicação em tempo real via Socket.IO com o backend.
    *   Respostas pré-definidas para perguntas comuns sobre a Furia.
    *   Avatar animado com diferentes emoções.
    *   Sugestões de perguntas.
    *   Indicador de status de conexão (Online/Offline).
    *   Modo offline com respostas de fallback caso o backend não esteja disponível.
    *   Componentes de UI utilizando Shadcn/ui e Tailwind CSS.

## Estrutura do Projeto

```
furia_project/
├── backend/             # Servidor Node.js (Express + Socket.IO)
│   ├── node_modules/
│   ├── .env             # Variáveis de ambiente (ex: PORT)
│   ├── package.json
│   ├── pnpm-lock.yaml
│   └── server.js        # Lógica do servidor e chatbot backend
├── furia-chatbot-app/   # Aplicação Frontend Next.js
│   ├── .next/           # Build do Next.js
│   ├── node_modules/
│   ├── public/          # Arquivos estáticos (imagens, etc.)
│   ├── src/
│   │   ├── app/         # Páginas e layout do Next.js App Router
│   │   ├── components/  # Componentes React (ChatSection, TeamSection, etc.)
│   │   └── styles/      # Estilos CSS
│   ├── .env.local       # Variáveis de ambiente do frontend (URL do backend)
│   ├── next.config.mjs
│   ├── package.json
│   ├── postcss.config.js
│   ├── tailwind.config.ts
│   └── tsconfig.json
├── static_landing/      # Diretório para deploy da landing page estática
│   └── index.html       # Landing page HTML
├── .gitignore
├── README.md            # Este arquivo
└── ...                  # Outros arquivos de configuração e scripts
```

## Como Executar Localmente

1.  **Clone o repositório:**
    ```bash
    git clone <URL_DO_REPOSITORIO>
    cd furia_project
    ```

2.  **Instale as dependências do Backend:**
    ```bash
    cd backend
    npm install -g pnpm # Se não tiver o pnpm instalado
    pnpm install
    cd ..
    ```

3.  **Instale as dependências do Frontend:**
    ```bash
    cd furia-chatbot-app
    npm install --legacy-peer-deps # Usar --legacy-peer-deps devido a conflitos de versão do React
    cd ..
    ```

4.  **Configure as variáveis de ambiente:**
    *   No diretório `backend/`, crie um arquivo `.env` se não existir e defina a porta (opcional, padrão 5000):
        ```
        PORT=5000
        ```
    *   No diretório `furia-chatbot-app/`, crie um arquivo `.env.local` se não existir e defina a URL do backend:
        ```
        NEXT_PUBLIC_BACKEND_URL=http://localhost:5000
        ```

5.  **Inicie o servidor Backend:**
    ```bash
    cd backend
    node server.js
    ```
    O servidor estará rodando em `http://localhost:5000` (ou na porta definida).

6.  **Inicie o servidor Frontend (em outro terminal):**
    ```bash
    cd furia-chatbot-app
    npm run dev
    ```
    A aplicação Next.js estará rodando em `http://localhost:3000`.

7.  **Inicie um servidor para a Landing Page (em outro terminal):**
    ```bash
    cd static_landing
    python3 -m http.server 8080
    ```
    A landing page estará acessível em `http://localhost:8080`.

8.  **Acesse a Landing Page:** Abra `http://localhost:8080` no seu navegador. Clique em "ACESSAR O CHATBOT" para ir para `http://localhost:3000`.

## Tecnologias Utilizadas

*   **Frontend:** Next.js, React, TypeScript, Tailwind CSS, Shadcn/ui, Socket.IO Client, Framer Motion, Emoji Picker React
*   **Backend:** Node.js, Express, Socket.IO
*   **Linguagens:** TypeScript, JavaScript, HTML, CSS
*   **Gerenciador de Pacotes:** npm, pnpm
*   **Hospedagem:** Manus (para deploy estático e Next.js)

## Observações

*   O código do frontend foi ajustado para usar `npm install --legacy-peer-deps` devido a um conflito de versão entre o React 19 (usado no template) e a dependência `cmdk` (que esperava React 18).
*   O chatbot foi corrigido para usar a conexão Socket.IO real com o backend, incluindo um modo offline de fallback.

