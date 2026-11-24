# 📓 Notebook PW — Caderno de Programação Web

**Curso:** Análise e Desenvolvimento de Sistemas — Fatec Itapetininga  
**Disciplina:** Programação Web  
**Professor:** Me. Deivison S. Takatu  
**Aluno:** Henrique Tobias Ribeiro Domingues

Este repositório reúne minhas anotações, atividades e projetos da disciplina de Programação Web. A ideia é registrar não apenas o que foi desenvolvido, mas também os conceitos praticados e como as tecnologias se relacionam na construção de aplicações web.

## Resumos das aulas e conteúdos

A Aula 01 corresponde ao registro original. As demais são resumos temáticos de revisão baseados nos projetos, com numeração organizacional.

- [Aula 01 — Introdução à Programação Web](./Aula_01_Resumo.md)
- [Aula 02 — HTML e CSS](./Aula_02_Resumo.md)
- [Aula 03 — JavaScript, DOM e eventos](./Aula_03_Resumo.md)
- [Aula 04 — APIs, HTTP, JSON e assincronismo](./Aula_04_Resumo.md)
- [Aula 05 — React, componentes, JSX e estado](./Aula_05_Resumo.md)
- [Aula 06 — React — Miniaplicações](./Aula_06_Resumo.md)
- [Aula 07 — React, Vite e CRUD de notas](./Aula_07_Resumo.md)
- [Aula 08 — Vue 3 e Vite](./Aula_08_Resumo.md)
- [Aula 09 — Ecoa — UX e modularização](./Aula_09_Resumo.md)
- [Aula 10 — Ecoa — Persistência, mapas e serviços](./Aula_10_Resumo.md)
- [Aula 11 — PWA, testes, build e publicação](./Aula_11_Resumo.md)

## Índice de estudos

| Repositório | Atividade | Tecnologias principais |
| --- | --- | --- |
| [Notebook_Pw](https://github.com/ZPoizon/Notebook_Pw) | Anotações e introdução à disciplina | Markdown, Git e GitHub |
| [Pwsite](https://github.com/ZPoizon/Pwsite) | Quiz de animes | HTML, CSS, JavaScript e APIs |
| [mini-apps-react](https://github.com/ZPoizon/mini-apps-react) | Cinco miniaplicações interativas | React, JSX, CSS e ViaCEP |
| [Notas-React-interface](https://github.com/ZPoizon/Notas-React-interface) | Interface de gerenciamento de notas | React, Vite, JavaScript e API REST |
| [vue-vite](https://github.com/ZPoizon/vue-vite) | Estudo de estrutura de painel administrativo | Vue 3, Vite, TypeScript e Pinia |
| [Ecoa](https://github.com/ZPoizon/Ecoa) | Projeto web educativo sobre os 17 ODS | HTML, CSS, JS, PWA, Supabase e APIs |

---

## 1. Notebook PW — Fundamentos da disciplina

[Acessar resumo da Aula 01](./Aula_01_Resumo.md)

Na primeira aula, estudamos a organização da disciplina, a metodologia, as atividades práticas e a importância de construir um portfólio de desenvolvimento web.

### Conteúdos abordados

- Git e GitHub: controle de versões, branches e colaboração.
- Arquitetura de sites, UX/UI, definição de escopo e prototipação.
- Introdução ao JavaScript puro e à manipulação do DOM.
- Frameworks de front-end: React, Vue e Angular.
- Conceitos de back-end, MVC, APIs REST, autenticação e bancos NoSQL.
- Hospedagem, deploy, ambientes, CI/CD, CMS e construtores de sites.

**Aprendizado:** compreender as partes que compõem uma aplicação web e documentar os estudos em Markdown. Os conceitos desta aula são introdutórios; nem todos foram implementados nos projetos abaixo.

## 2. Pwsite — Anime Quiz Master

[Repositório](https://github.com/ZPoizon/Pwsite) · [HTML](https://github.com/ZPoizon/Pwsite/blob/HEAD/index.html) · [JavaScript](https://github.com/ZPoizon/Pwsite/blob/HEAD/script.js)

### O que foi trabalhado

Criação de um quiz temático de animes e mangás, com seleção de dificuldade, quantidade de perguntas, modo de perguntas em português, citações e desafio contra o tempo. O código também contempla pontuação, sequência de acertos, revisão das respostas e efeitos sonoros.

### Tecnologias e aprendizado

- **HTML5:** estrutura das telas, botões e conteúdo.
- **CSS3:** estilização e organização visual.
- **JavaScript puro:** funções, objetos, arrays, classes, condicionais, eventos e manipulação do DOM.
- **Open Trivia DB:** integração prevista para obter perguntas externas, com base local de perguntas como alternativa.
- **Web Audio API:** geração de efeitos sonoros pelo navegador.
- **localStorage:** armazenamento de recordes locais.
- Temporizadores e gerenciamento do estado do jogo.

**Aprendizado:** transformar uma página estática em uma aplicação interativa, controlando dados e atualizando a interface diretamente pelo JavaScript, sem depender de frameworks.

> Observação técnica: o HTML atualmente referencia `app.js`, mas o arquivo JavaScript presente no repositório é `script.js`. É necessário alinhar essa referência para executar corretamente a lógica do quiz.

## 3. Mini Apps React — Exercícios de React

[Repositório](https://github.com/ZPoizon/mini-apps-react) · [Código principal](https://github.com/ZPoizon/mini-apps-react/blob/main/src/App.js)

Projeto criado com Create React App, reunindo cinco exercícios em uma interface com menu de navegação.

| Miniaplicação | O que praticamos |
| --- | --- |
| To-Do List | Adicionar, concluir e excluir tarefas; listas, identificadores, `map` e `filter`. |
| Contador | Estado, eventos de clique, incremento e reinicialização. |
| Jogo da velha | Arrays, alternância de jogadores, regras de vitória, empate e renderização condicional. |
| Calculadora | Operações básicas, controle de entrada e tratamento de erros. |
| Buscador de CEP | Consumo do ViaCEP, validação, JSON, requisições assíncronas e estados de carregamento e erro. |

### Tecnologias e aprendizado

- React, JSX, JavaScript, CSS, npm e Create React App.
- Hook `useState` para atualizar a interface a partir de mudanças nos dados.
- Componentes funcionais, inputs controlados e eventos como `onClick` e `onChange`.
- Renderização de listas com chaves, condições e navegação interna por estado.
- `fetch`, `async/await` e `try/catch/finally`.

**Aprendizado:** compreender a diferença entre alterar o DOM manualmente e declarar uma interface que reage ao estado da aplicação.

**Ponto de melhoria:** substituir o uso de `eval` na calculadora por um avaliador restrito a operações matemáticas.

Para estudar localmente: `npm install` e `npm start`.

## 4. Notas React — Front-end conectado a uma API

[Repositório](https://github.com/ZPoizon/Notas-React-interface) · [Código principal](https://github.com/ZPoizon/Notas-React-interface/blob/main/notas-react/src/App.jsx)

Interface para criar, visualizar, editar e excluir anotações, utilizando uma API externa hospedada no Render.

### Operações CRUD

| Operação | Método HTTP | Finalidade |
| --- | --- | --- |
| Create | POST | Cadastrar uma nota |
| Read | GET | Consultar notas |
| Update | PUT | Atualizar uma nota |
| Delete | DELETE | Excluir uma nota |

### Tecnologias e aprendizado

- React, JSX, JavaScript, CSS, Vite e npm.
- `useState` para controlar formulários, lista de notas e modo de edição.
- `useEffect` para carregar as notas ao iniciar a aplicação.
- API REST, métodos HTTP, `fetch`, JSON e cabeçalho `Content-Type`.
- Validação de campos, confirmação de exclusão, cancelamento de edição e atualização da lista.

**Aprendizado:** separar a interface da lógica de armazenamento do servidor e compreender como o front-end envia e recebe dados. O repositório contém a interface; a implementação do back-end e seu banco não foram verificados.

Para estudar localmente, entre em `notas-react/`, execute `npm install` e `npm run dev`.

## 5. Vue + Vite — Estrutura de uma aplicação administrativa

[Repositório](https://github.com/ZPoizon/vue-vite) · [Dependências](https://github.com/ZPoizon/vue-vite/blob/main/package.json)

Este repositório utiliza o template open source [V3 Admin Vite](https://github.com/un-pany/v3-admin-vite), distribuído sob licença MIT. Ele serve como referência para estudar a organização de aplicações Vue de maior porte, sem atribuir ao aluno a autoria das funcionalidades originais do template.

| Tecnologia | Conceito estudável na estrutura |
| --- | --- |
| Vue 3 | Componentes, reatividade e Composition API |
| Vite | Servidor de desenvolvimento e build |
| TypeScript | Tipagem estática |
| Vue Router | Rotas e navegação |
| Pinia | Gerenciamento de estado compartilhado |
| Element Plus | Componentes de interface administrativa |
| Axios | Requisições HTTP |
| SCSS e UnoCSS | Estilização e organização visual |
| pnpm, ESLint e Vitest | Dependências, análise de código e testes |

A estrutura possui diretórios para páginas, layouts, rotas, estado, plugins e comunicação HTTP. O template inclui exemplos de login, dashboard, permissões, temas e páginas de erro.

**Aprendizado:** reconhecer uma arquitetura front-end modular, comparar o ecossistema Vue com React e entender como ferramentas e bibliotecas são combinadas em um projeto maior. Os recursos do template são registrados como referências de estudo, não como implementações próprias comprovadas.

Para estudar localmente: `pnpm install` e `pnpm dev`.

## 6. Ecoa — Projeto integrador: pequenas ações, 17 objetivos

[Repositório](https://github.com/ZPoizon/Ecoa) · [Documentação](https://github.com/ZPoizon/Ecoa/blob/main/README.md)

O Ecoa é uma aplicação web educativa que aproxima os 17 Objetivos de Desenvolvimento Sustentável (ODS) da realidade das pessoas. A proposta é ajudar o usuário a encontrar ações possíveis de acordo com seu tempo, orçamento e contexto.

### O que foi desenvolvido

- **Agir:** filtros de ações sustentáveis e estimativas de impacto.
- **Aprender:** guias dos 17 ODS, quiz e referências oficiais.
- **Na cidade:** mapa, busca de endereços e pontos úteis de reciclagem, doação e outras ações.
- **Meu espaço:** plano pessoal, progresso, desafios, conquistas, lembretes, PDF e backup.
- Interface responsiva, temas, preferências de leitura e instalação como PWA.

### Tecnologias e aprendizado

| Tecnologia | Aplicação prática |
| --- | --- |
| HTML5, CSS3 e JavaScript puro | Interface, módulos, eventos, responsividade e navegação |
| PWA, Service Worker e Manifest | Instalação e cache para acesso offline a recursos locais |
| localStorage e JSON | Persistência de preferências, plano pessoal e bases locais |
| Leaflet e OpenStreetMap | Visualização de dados geográficos |
| Overpass, Photon e ViaCEP | Consultas de pontos e endereços |
| Supabase e PostgreSQL | Dados compartilhados e políticas de acesso RLS |
| pdf-lib | Exportação do plano em PDF |
| Node.js | Scripts, servidor local, build e testes |
| Vercel e Vercel Functions | Configuração de hospedagem e integração complementar com conteúdos da ONU Brasil |

**Aprendizado:** integrar os conhecimentos de desenvolvimento web em um projeto com finalidade social, aplicando organização modular, consumo de serviços externos, persistência, acessibilidade, experiência do usuário, testes e preparação para publicação.

O Ecoa é um projeto acadêmico independente, não oficial da ONU. O uso offline não abrange todas as consultas externas e os dados pessoais do plano são armazenados localmente no navegador.

Para estudar localmente, com Node.js 22: `npm run dev`, `npm test` e `npm run build`.

---

## Revisão geral — o que aprendemos na disciplina

| Conceito | Para que serve | Exemplo prático |
| --- | --- | --- |
| HTML | Estruturar o conteúdo | Telas do quiz |
| CSS | Estilizar e adaptar interfaces | Quiz e Ecoa |
| JavaScript | Implementar comportamento e lógica | Pontuação, filtros e eventos |
| DOM | Acessar e alterar elementos da página | Pwsite |
| Componentização e estado | Organizar interfaces reativas | Mini Apps e Notas |
| API REST e JSON | Trocar dados entre sistemas | Notas e ViaCEP |
| CRUD | Criar, consultar, atualizar e excluir registros | Notas |
| Persistência | Manter informações disponíveis após recarregar a página | Recordes e plano do Ecoa |
| Rotas e estado compartilhado | Organizar aplicações com várias páginas | Template Vue |
| PWA | Permitir instalação e acesso a recursos em cache | Ecoa |
| Versionamento | Registrar alterações e organizar projetos | Git e GitHub |
| Build, testes e deploy | Preparar, verificar e disponibilizar aplicações | Projetos React, Vue e Ecoa |

### Conclusão

As atividades permitem revisar desde os fundamentos de HTML, CSS e JavaScript até o desenvolvimento com bibliotecas e frameworks, comunicação com APIs e organização de aplicações mais completas. O principal aprendizado foi entender como a interface, a lógica, os dados e os serviços externos se conectam para resolver problemas reais.

Este caderno funciona como material de revisão e índice do portfólio da disciplina. A ordem das seções é temática, não um calendário oficial de aulas. Os registros descrevem os arquivos e a documentação disponíveis nos repositórios, sem afirmar que todos os recursos foram testados em execução.
