# Aula 08 — Vue 3 e Vite — Arquitetura de front-end

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Conhecer a estrutura de aplicações Vue e comparar seu ecossistema ao React. O conteúdo é relacionado ao projeto [vue-vite](https://github.com/ZPoizon/vue-vite), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de Vue 3 e Vite.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- Single File Components (.vue).
- Composition API e reatividade.
- TypeScript.
- Vue Router e navegação.
- Pinia e estado compartilhado.
- Element Plus.
- Axios.
- SCSS e UnoCSS.
- pnpm, ESLint e Vitest.
- separação em páginas, layouts, rotas e serviços HTTP.

## Aplicação prática no projeto
O repositório utiliza o template V3 Admin Vite, de autoria de terceiros, sob licença MIT. A estrutura oferece exemplos de dashboard, login e permissões. Esses recursos são referências de estudo, não funcionalidades cuja autoria acadêmica foi comprovada.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Identificar src/pages, src/router, src/pinia e src/http.
2. localizar um componente.
3. comparar reatividade Vue e estado React.
4. executar pnpm dev em ambiente configurado.

## Referências
- [Repositório vue-vite](https://github.com/ZPoizon/vue-vite)
- [Documentação de referência](https://vuejs.org/guide/introduction.html)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Inventário técnico do template V3 Admin Vite 5.2.0

Versões declaradas no package.json consultado: Vue 3.5.39, Vite 7.3.6, TypeScript 5.9.3, Pinia 3.0.4, Vue Router 5.1.0, Element Plus 2.14.2, Axios 1.18.1, UnoCSS 66.7.5, Vitest 4.1.10. Também há VXE Table, Sass, ESLint, Husky e lint-staged.

| Diretório/arquivo | Papel |
| --- | --- |
| src/main.ts | Criação da aplicação, instalação de plugins, Pinia e Router |
| src/App.vue | Componente raiz |
| src/pages | Dashboard, login, erros, redirect e demonstrações |
| src/layouts | Estrutura compartilhada de páginas |
| src/router/index.ts | Rotas constantes e dinâmicas, imports preguiçosos, resetRouter |
| src/router/guard.ts | Registro de guardas, verificação de token e uso de stores |
| src/pinia | Estado global |
| src/http | Camada de comunicação HTTP |
| src/common | Utilitários e recursos compartilhados |
| vite.config.ts | Plugins, aliases, configuração de proxy e build |
| tests | Infraestrutura de testes |

Em main.ts, app.use(pinia).use(router) instala as duas bibliotecas e router.isReady() antecede app.mount("#app"). Em router/index.ts há rotas /login, /403, /404, /demo e /permission; rotas dinâmicas usam meta.roles e meta.permissions. O template exemplifica lazy loading por import().

O Vite configura um proxy de demonstração para https://apifoxmock.com/m1/2930465-2145633-default. Isso evidencia um serviço mock; não comprova uma API própria de produção. Permissões no front-end não substituem autorização no servidor.

### Comparação didática
React usa JSX e hooks; Vue oferece arquivos .vue, templates e Composition API. O Mini Apps escolhe telas por estado; Vue Router usa rotas declarativas. Pinia compartilha estado entre componentes; Axios encapsula requisições HTTP, enquanto os projetos React analisados usam fetch.

Scripts: pnpm dev, pnpm build (vue-tsc e Vite), pnpm test e pnpm lint.

**Fontes:** [package.json](https://github.com/ZPoizon/vue-vite/blob/main/package.json), [main.ts](https://github.com/ZPoizon/vue-vite/blob/main/src/main.ts), [router](https://github.com/ZPoizon/vue-vite/blob/main/src/router/index.ts), [Vite](https://github.com/ZPoizon/vue-vite/blob/main/vite.config.ts). Autoria original: [V3 Admin Vite](https://github.com/un-pany/v3-admin-vite).
