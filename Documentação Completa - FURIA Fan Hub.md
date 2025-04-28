# Documentação Completa - FURIA Fan Hub

Este documento fornece uma documentação abrangente do projeto FURIA Fan Hub, desenvolvido como parte de um desafio técnico para a vaga de Assistente de Engenheiro de Software na Furia Esports. A documentação inclui visão geral, estrutura do projeto, guia de instalação, guia de uso, documentação da API e análise do código.

## Sumário

1. [Visão Geral](#visão-geral)
2. [Funcionalidades Detalhadas](#funcionalidades-detalhadas)
3. [Estrutura do Projeto](#estrutura-do-projeto)
4. [Tecnologias Utilizadas](#tecnologias-utilizadas)
5. [Guia de Instalação](#guia-de-instalação)
6. [Guia de Uso](#guia-de-uso)
7. [Documentação da API e Código](#documentação-da-api-e-código)
8. [Análise do Código](#análise-do-código)
9. [Considerações para Desenvolvimento Futuro](#considerações-para-desenvolvimento-futuro)

## Visão Geral

O FURIA Fan Hub é uma aplicação web projetada para engajar os fãs da Furia Esports. Ele é composto por duas partes principais:

1.  **Landing Page:** Uma página de entrada estática (`index.html`) que apresenta o projeto e direciona os usuários para o componente principal.
2.  **Chatbot Furioso:** Uma interface de chat interativa construída com Next.js e TypeScript. O chatbot responde a perguntas sobre a Furia, seus times (especialmente CS2), história e outras informações relevantes. Ele foi projetado para se comunicar com um backend Node.js via Socket.IO para respostas em tempo real, mas também inclui um modo offline funcional.

## Funcionalidades Detalhadas

### Landing Page (`static_landing/index.html`)

*   **Apresentação:** Introduz o propósito do FURIA Fan Hub.
*   **Chamada para Ação (CTA):** Contém um botão claro que leva o usuário diretamente para a aplicação do chatbot.
*   **Design:** Apresenta um design simples e direto, utilizando HTML e CSS, com fontes temáticas (Orbitron e Roboto) e as cores da Furia.
*   **Responsividade:** O layout se adapta a diferentes tamanhos de tela (design responsivo básico).
*   **Disclaimer:** Informa que se trata de um projeto de desafio técnico e não um produto oficial da Furia.

### Chatbot Furioso (`furia-chatbot-app/src/components/ChatSection.tsx`)

*   **Interface de Chat:** Exibe a conversa entre o usuário e o bot em um formato familiar de mensagens.
*   **Comunicação em Tempo Real:** Utiliza Socket.IO para conectar-se a um servidor backend (não incluído no zip, mas descrito no README original) para obter respostas dinâmicas.
*   **Modo Offline:** Possui uma lógica de fallback (`getFallbackBotResponse`) que fornece respostas pré-definidas caso a conexão com o backend falhe ou não esteja disponível. Isso garante que o chatbot permaneça funcional.
*   **Avatar Dinâmico:** Apresenta um avatar animado de uma pantera (o mascote "Furioso") que muda de emoção (`happy`, `fury`, `thinking`, `neutral`) com base no contexto da conversa ou no status do bot (digitando).
*   **Mensagem de Boas-Vindas:** Envia automaticamente uma mensagem introdutória ao carregar.
*   **Indicador de Status:** Mostra visualmente se o chatbot está conectado ao backend ("Conectado") ou operando em modo offline ("Modo Offline").
*   **Entrada de Usuário:** Permite que os usuários digitem suas perguntas, enviem emojis (usando `emoji-picker-react`) e enviem mensagens pressionando Enter ou clicando no botão de envio.
*   **Sugestões de Perguntas:** Apresenta botões com perguntas comuns para facilitar a interação do usuário.
*   **Feedback de Digitação:** Mostra um indicador visual quando o bot está "digitando" uma resposta.
*   **Tecnologias Frontend:** Construído com React (Next.js), TypeScript, Tailwind CSS para estilização, Shadcn/ui para componentes de UI, Framer Motion para animações e Socket.IO Client para comunicação.

## Estrutura do Projeto (Ideal)

Embora o arquivo `.zip` fornecido contenha apenas partes do frontend e a landing page estática, a estrutura completa do projeto, conforme descrito no `README.md` original, seria a seguinte:

```
furia_project/
├── backend/             # Servidor Node.js (Express + Socket.IO) - NÃO INCLUÍDO NO ZIP
│   ├── node_modules/
│   ├── .env             # Variáveis de ambiente (ex: PORT)
│   ├── package.json
│   ├── pnpm-lock.yaml
│   └── server.js        # Lógica do servidor e chatbot backend
├── furia-chatbot-app/   # Aplicação Frontend Next.js
│   ├── .next/           # Build do Next.js
│   ├── node_modules/
│   ├── public/          # Arquivos estáticos (imagens, avatar.svg, etc.)
│   ├── src/
│   │   ├── app/         # Páginas e layout do Next.js App Router
│   │   ├── components/  # Componentes React (ChatSection.tsx, etc.)
│   │   └── styles/      # Estilos CSS (avatar.css)
│   ├── .env.local       # Variáveis de ambiente do frontend (URL do backend)
│   ├── next.config.mjs
│   ├── package.json
│   ├── postcss.config.js
│   ├── tailwind.config.ts
│   └── tsconfig.json
├── static_landing/      # Diretório para deploy da landing page estática
│   └── index.html       # Landing page HTML
├── .gitignore
├── README.md            # O README original do projeto
└── roteiro_video_final.md # Roteiro para um vídeo de apresentação
```

*   **`backend/`**: Conteria o servidor Node.js responsável por receber mensagens do cliente via Socket.IO, processá-las (possivelmente usando alguma lógica de NLP ou regras) e enviar as respostas de volta. *Esta parte não foi incluída no arquivo zip fornecido.*
*   **`furia-chatbot-app/`**: O frontend Next.js que renderiza a interface do chat (`ChatSection.tsx`) e se comunica com o backend.
*   **`static_landing/`**: Contém a página HTML simples que serve como ponto de entrada.
*   **`roteiro_video_final.md`**: Um arquivo Markdown contendo um roteiro, provavelmente usado para gravar um vídeo demonstrando o projeto.

## Tecnologias Utilizadas

*   **Frontend:** Next.js, React, TypeScript, Tailwind CSS, Shadcn/ui, Socket.IO Client, Framer Motion, Emoji Picker React
*   **Backend (Ideal):** Node.js, Express, Socket.IO
*   **Linguagens:** TypeScript, JavaScript, HTML, CSS
*   **Gerenciador de Pacotes:** npm, pnpm (mencionado no README original para o backend)
*   **Hospedagem (Exemplo):** Manus (mencionado no README original para deploy estático e Next.js)

## Guia de Instalação

### Pré-requisitos

Antes de começar, certifique-se de ter o seguinte software instalado em sua máquina:

*   **Node.js:** Versão 18 ou superior recomendada. Você pode baixá-lo em [nodejs.org](https://nodejs.org/). O Node.js inclui o npm (Node Package Manager).
*   **pnpm (Opcional, para Backend):** O README original menciona o uso de `pnpm` para o backend. Se você for usar o backend original, instale o pnpm globalmente: `npm install -g pnpm`.
*   **Git:** Necessário para clonar o repositório (se aplicável).
*   **Python 3 (Opcional, para Landing Page):** Uma maneira fácil de servir a landing page estática localmente. A maioria dos sistemas já o possui instalado.

### 1. Obtenha o Código do Projeto

Se você estiver trabalhando a partir do arquivo zip fornecido:

*   Descompacte o arquivo `furia_fan_hub_final_v10.zip` em um diretório de sua escolha. Você terá uma pasta `furia_fan_hub` contendo `furia_project`.

Se você estiver clonando de um repositório Git (substitua `<URL_DO_REPOSITORIO>` pela URL real):

```bash
git clone <URL_DO_REPOSITORIO>
cd furia_project
```

### 2. Configuração do Backend (Se o código estiver disponível)

**Nota:** Estas etapas são baseadas no README original e pressupõem que você tenha o diretório `backend/`.

1.  **Navegue até o diretório do backend:**
    ```bash
    cd backend
    ```

2.  **Instale as dependências:**
    *   Usando pnpm (recomendado pelo README original):
        ```bash
        pnpm install
        ```
    *   Ou usando npm:
        ```bash
        npm install
        ```

3.  **Configure as variáveis de ambiente:**
    *   Crie um arquivo chamado `.env` dentro do diretório `backend/`.
    *   Adicione a seguinte linha, definindo a porta em que o servidor será executado (o padrão é 5000 se não for especificado):
        ```
        PORT=5000
        ```

4.  **Inicie o servidor backend:**
    ```bash
    node server.js
    ```
    *   O servidor backend estará em execução (por padrão em `http://localhost:5000`). Mantenha este terminal aberto.

5.  **Volte para o diretório raiz do projeto:**
    ```bash
    cd ..
    ```

### 3. Configuração do Frontend (Chatbot Next.js)

1.  **Navegue até o diretório do frontend:**
    ```bash
    cd furia-chatbot-app
    ```

2.  **Instale as dependências:**
    *   O README original recomenda usar `--legacy-peer-deps` devido a possíveis conflitos de versão do React com dependências como `cmdk`. Execute:
        ```bash
        npm install --legacy-peer-deps
        ```
    *   Se encontrar problemas, você pode tentar `npm install` normalmente, mas esteja ciente dos possíveis avisos de dependência.

3.  **Configure as variáveis de ambiente:**
    *   Crie um arquivo chamado `.env.local` dentro do diretório `furia-chatbot-app/`.
    *   Adicione a seguinte linha, especificando a URL onde o servidor backend está (ou estará) em execução:
        ```
        NEXT_PUBLIC_BACKEND_URL=http://localhost:5000
        ```
        *Certifique-se de que a porta corresponde à definida no `.env` do backend.*

4.  **Inicie o servidor de desenvolvimento do frontend:**
    ```bash
    npm run dev
    ```
    *   A aplicação Next.js estará em execução, geralmente em `http://localhost:3000`. Mantenha este terminal aberto.

5.  **Volte para o diretório raiz do projeto:**
    ```bash
    cd ..
    ```

### 4. Executando a Landing Page Estática

1.  **Navegue até o diretório da landing page:**
    ```bash
    cd static_landing
    ```

2.  **Inicie um servidor HTTP simples:**
    *   Usando Python 3:
        ```bash
        python3 -m http.server 8080
        ```
    *   Alternativamente, você pode usar outras ferramentas como `npx serve` ou extensões do VS Code (Live Server).
    *   A landing page estará acessível em `http://localhost:8080` (ou na porta que você escolher). Mantenha este terminal aberto.

### 5. Acessando a Aplicação

1.  Abra seu navegador web.
2.  Acesse a **Landing Page** em `http://localhost:8080`.
3.  Clique no botão "ACESSAR O CHATBOT".
4.  Você será redirecionado para a aplicação **Chatbot Furioso** em `http://localhost:3000`.

Agora você deve ter o ambiente local do FURIA Fan Hub configurado e em execução. Se o backend estiver rodando, o chatbot tentará se conectar a ele. Caso contrário, ele funcionará no modo offline usando as respostas de fallback definidas no código do frontend.

## Guia de Uso

### Acessando a Aplicação

1.  **Landing Page:** Comece acessando a landing page (por exemplo, `http://localhost:8080` se estiver executando localmente, ou a URL de deploy fornecida).
2.  **Entrar no Chatbot:** Na landing page, clique no botão "ACESSAR O CHATBOT". Isso o redirecionará para a aplicação principal do chatbot (por exemplo, `http://localhost:3000` localmente).

### Interface do Chatbot Furioso

Ao acessar a aplicação do chatbot, você verá a seguinte interface:

*   **Área de Mensagens:** O painel principal onde a conversa entre você e o Furioso é exibida. Suas mensagens aparecem à direita, e as do bot à esquerda.
*   **Avatar do Furioso:** No topo (ou em uma seção destacada), você verá o avatar da pantera, o "Furioso". A aparência do avatar pode mudar para refletir diferentes emoções (feliz, pensando, furioso, neutro) com base na conversa ou se ele está "digitando".
*   **Indicador de Status:** Geralmente localizado no canto superior direito, este indicador mostra se o chatbot está "Conectado" ao servidor backend (verde) ou em "Modo Offline" (amarelo). No modo offline, as respostas são pré-definidas.
*   **Área de Entrada de Texto:** Na parte inferior, há um campo onde você pode digitar suas perguntas ou mensagens para o bot.
*   **Botão de Emoji:** Ao lado do campo de entrada, um ícone de sorriso permite abrir um seletor de emojis para adicionar às suas mensagens.
*   **Botão Enviar:** Um botão (geralmente com um ícone de envio) para mandar sua mensagem digitada.
*   **Sugestões de Perguntas:** Abaixo da área de entrada, podem aparecer botões com perguntas pré-sugeridas. Clicar em um desses botões enviará a pergunta diretamente ao bot.

### Interagindo com o Furioso

1.  **Mensagem de Boas-Vindas:** Ao carregar, o Furioso enviará automaticamente uma mensagem de boas-vindas.
2.  **Fazendo Perguntas:**
    *   **Digite sua pergunta:** Use o campo de entrada na parte inferior para digitar sua pergunta sobre a Furia, times, história, etc.
    *   **Use as Sugestões:** Clique em um dos botões de "Sugestões de Perguntas" para enviar uma pergunta comum rapidamente.
3.  **Enviando a Mensagem:**
    *   Pressione a tecla `Enter` após digitar sua mensagem.
    *   Ou clique no botão "Enviar".
4.  **Recebendo Respostas:**
    *   Você verá um indicador de "digitando" (geralmente três pontos animados) enquanto o bot prepara a resposta.
    *   A resposta do Furioso aparecerá na área de mensagens, vindo do lado esquerdo.
    *   Observe a emoção do avatar, que pode mudar com a resposta.
5.  **Usando Emojis:** Clique no botão de emoji, selecione o emoji desejado e ele será adicionado ao campo de entrada.

### Entendendo os Modos

*   **Modo Online (Conectado):** Se o indicador mostrar "Conectado", o chatbot está se comunicando com o servidor backend para obter respostas potencialmente mais dinâmicas e atualizadas (dependendo da implementação do backend).
*   **Modo Offline:** Se o indicador mostrar "Modo Offline", o chatbot não conseguiu se conectar ao backend. Ele ainda funcionará, mas usará um conjunto pré-definido de respostas (`getFallbackBotResponse` no código `ChatSection.tsx`). As respostas podem ser mais limitadas neste modo.

### Outras Seções (Conforme README Original)

O README original menciona que a aplicação completa teria abas ou seções adicionais como "Time CS2" e "Quiz Furia". A interação dentro dessas seções dependeria de sua implementação específica, que não está detalhada no código `ChatSection.tsx` fornecido no arquivo zip.

## Documentação da API e Código

### Componente Principal: `ChatSection.tsx`

Localizado em `furia-chatbot-app/src/components/ChatSection.tsx`, este é o componente React funcional que encapsula toda a lógica e interface do chatbot.

**Propósito:** Renderizar a interface de chat, gerenciar o estado da conversa, lidar com a entrada do usuário e comunicar-se com o backend (ou operar em modo offline).

#### Interfaces Definidas

```typescript
// Define a estrutura de uma mensagem na conversa
interface Message {
  sender: 'user' | 'bot'; // Quem enviou a mensagem
  text: string;          // O conteúdo da mensagem
  emotion?: string;       // Emoção associada (para mensagens do bot, controla o avatar)
}

// Define a estrutura da resposta esperada do bot (do backend ou fallback)
interface BotResponse {
  text: string;    // Texto da resposta do bot
  emotion: string; // Emoção que o bot deve expressar
}
```

#### Estados Principais (React `useState`)

*   `messages` (`Message[]`): Array que armazena o histórico da conversa. Cada item é um objeto `Message`.
*   `inputValue` (`string`): Armazena o texto atual no campo de entrada do usuário.
*   `socket` (`Socket | null`): Mantém a instância do objeto Socket.IO para comunicação com o backend.
*   `botEmotion` (`string`): Controla a emoção atual do avatar do bot (ex: 'neutral', 'happy', 'fury', 'thinking'). Afeta as classes CSS aplicadas ao avatar.
*   `isBotTyping` (`boolean`): Indica se o bot está atualmente "digitando" uma resposta. Usado para mostrar o indicador de digitação e desabilitar a entrada do usuário temporariamente.
*   `isConnected` (`boolean`): Indica se a conexão Socket.IO com o backend está ativa.

#### Funções Principais

*   `sendMessage()`: Chamada quando o usuário envia uma mensagem. Adiciona a mensagem do usuário ao estado `messages`, limpa o campo de entrada, define `isBotTyping` como `true`, e emite o evento `user-message` via Socket.IO (se conectado) ou chama `getFallbackBotResponse` (se offline).
*   `getFallbackBotResponse(message: string): BotResponse`: Função acionada no modo offline. Recebe a mensagem do usuário, realiza uma correspondência básica de palavras-chave (não sensível a maiúsculas/minúsculas) e retorna um objeto `BotResponse` pré-definido. As respostas tentam simular as que seriam dadas pelo backend.
*   `handleInputChange()`: Atualiza o estado `inputValue` conforme o usuário digita no campo de entrada.
*   `handleKeyPress()`: Detecta se a tecla Enter foi pressionada no campo de entrada para chamar `sendMessage()`.
*   `handleEmojiClick()`: Adiciona o emoji selecionado no `EmojiPicker` ao `inputValue`.
*   `handleSuggestedQuestionClick(question: string)`: Chamada quando um botão de sugestão é clicado. Funciona de forma semelhante a `sendMessage()`, enviando a pergunta sugerida diretamente.

#### Efeitos Colaterais (React `useEffect`)

*   **Conexão Socket.IO:** Um `useEffect` é responsável por inicializar a conexão Socket.IO quando o componente é montado. Ele configura os listeners para os eventos `connect`, `disconnect`, `connect_error`, e `bot-message`. Também lida com tentativas de reconexão e define o estado `isConnected`.
*   **Mensagem de Boas-Vindas:** Outro `useEffect` dispara uma única vez para enviar a mensagem de boas-vindas automática do bot logo após a montagem inicial do componente.
*   **Auto-Scroll:** Um `useEffect` observa mudanças nos estados `messages` e `isBotTyping` para rolar automaticamente a área de chat para a mensagem mais recente, garantindo que o usuário sempre veja as últimas interações.

### Comunicação via Socket.IO (Frontend)

A comunicação em tempo real com o backend é gerenciada pela biblioteca `socket.io-client`.

*   **Inicialização:** A conexão é estabelecida com a URL definida na variável de ambiente `NEXT_PUBLIC_BACKEND_URL` (fallback para `http://localhost:5000`).
    ```javascript
    const BACKEND_URL = process.env.NEXT_PUBLIC_BACKEND_URL || 'http://localhost:5000';
    const newSocket = io(BACKEND_URL, { /* opções */ });
    ```

*   **Eventos Emitidos (Cliente -> Servidor):**
    *   `user-message` (payload: `string`): Enviado quando o usuário manda uma mensagem. O payload é o texto da mensagem do usuário.
        ```javascript
        socket.emit('user-message', userText);
        ```

*   **Eventos Recebidos (Servidor -> Cliente):**
    *   `connect`: Disparado quando a conexão é estabelecida com sucesso. Define `isConnected` para `true`.
    *   `disconnect`: Disparado quando a conexão é perdida. Define `isConnected` para `false`.
    *   `connect_error`: Disparado quando ocorre um erro ao tentar conectar. Usado para contar tentativas de reconexão e, eventualmente, confirmar o estado offline.
    *   `bot-message` (payload: `BotResponse`): Recebe a resposta do bot vinda do servidor. O payload deve ser um objeto `BotResponse`. A função atualiza o estado `messages` com a resposta do bot e define `botEmotion` e `isBotTyping`.
        ```javascript
        newSocket.on('bot-message', (response: BotResponse) => {
          setIsBotTyping(false);
          setMessages(prev => [...prev, { sender: 'bot', text: response.text, emotion: response.emotion }]);
          setBotEmotion(response.emotion || 'neutral');
        });
        ```

### Animação do Avatar

A emoção do avatar é controlada dinamicamente pela adição de classes CSS ao elemento contêiner do avatar. O estado `botEmotion` (ex: 'happy', 'fury', 'thinking') é usado para determinar qual classe de emoção adicionar. Classes adicionais como `thinking` ou `talking` também podem ser adicionadas com base no estado `isBotTyping` ou em respostas específicas. As animações e estilos visuais correspondentes a essas classes seriam definidos em um arquivo CSS separado (como `avatar.css`, mencionado nos imports, mas não presente no zip).

```jsx
<div className={`avatar-container my-2 ${botEmotion} ${isBotTyping ? 'thinking' : ''} ...`}>
  <Image ... />
</div>
```

## Análise do Código

### Pontos Fortes

1. **Modo Offline Robusto:** O componente `ChatSection.tsx` implementa um sistema de fallback inteligente que permite que o chatbot continue funcionando mesmo quando não consegue se conectar ao backend. Isso melhora significativamente a experiência do usuário em cenários de conectividade instável.

2. **Feedback Visual Rico:** O chatbot fornece feedback visual através do avatar animado, indicador de status de conexão e animação de "digitando". Esses elementos tornam a interação mais envolvente e informativa.

3. **Sugestões de Perguntas:** A inclusão de botões de sugestão facilita a interação inicial do usuário com o chatbot, reduzindo a barreira de entrada e guiando a conversa.

4. **Gerenciamento de Estado Eficiente:** O código utiliza os hooks do React (`useState`, `useEffect`, `useRef`, `useCallback`) de maneira eficaz para gerenciar o estado da aplicação e os efeitos colaterais.

5. **Componentes Reutilizáveis:** O projeto utiliza componentes UI da biblioteca Shadcn/ui, o que promove a consistência visual e a reutilização de código.

### Áreas para Melhoria

1. **Separação de Responsabilidades:** A função `getFallbackBotResponse` contém uma grande quantidade de lógica condicional para determinar respostas. Em uma versão futura, essa lógica poderia ser extraída para um módulo separado ou utilizar uma abordagem mais estruturada (como um mapa de intenções ou um sistema de regras).

2. **Testes Automatizados:** Não há evidência de testes no código fornecido. A adição de testes unitários e de integração seria benéfica para garantir a robustez do sistema.

3. **Acessibilidade:** Embora o código utilize componentes modernos, não há menção explícita a considerações de acessibilidade (ARIA roles, navegação por teclado, etc.).

4. **Internacionalização:** O chatbot atualmente suporta apenas português brasileiro. Uma estrutura para suportar múltiplos idiomas poderia ser considerada para expansão futura.

## Considerações para Desenvolvimento Futuro

1. **Expansão do Backend:** Implementar um backend mais robusto que possa processar linguagem natural de forma mais sofisticada, possivelmente utilizando modelos de IA como GPT para gerar respostas mais contextuais.

2. **Persistência de Conversas:** Adicionar a capacidade de salvar históricos de conversa para que os usuários possam retomar conversas anteriores.

3. **Autenticação de Usuários:** Implementar um sistema de login para personalizar a experiência com base no perfil do usuário.

4. **Integração com APIs Externas:** Conectar o chatbot a APIs externas para fornecer informações em tempo real sobre jogos, resultados, estatísticas de jogadores, etc.

5. **Expansão das Seções:** Desenvolver completamente as seções "Time CS2" e "Quiz Furia" mencionadas no README original.

6. **Análise de Sentimento:** Implementar análise de sentimento nas mensagens do usuário para adaptar as respostas do bot de forma mais empática.

7. **Versão Mobile Nativa:** Considerar o desenvolvimento de versões nativas para iOS e Android para melhorar a experiência em dispositivos móveis.

Esta documentação fornece uma visão abrangente do projeto FURIA Fan Hub, cobrindo todos os aspectos desde a instalação até considerações para desenvolvimento futuro. Ela serve como um guia completo para entender, usar e potencialmente expandir o projeto.
