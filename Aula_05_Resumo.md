# Aula 05 — React — Componentes, JSX e estado

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Entender interfaces declarativas e atualizar componentes a partir do estado. O conteúdo é relacionado ao projeto [mini-apps-react](https://github.com/ZPoizon/mini-apps-react), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de React.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- Componentes funcionais.
- JSX.
- props como mecanismo de passagem de dados.
- useState.
- eventos onClick e onChange.
- inputs controlados.
- renderização condicional.
- listas e keys.
- diferença entre DOM manual e renderização declarativa.
- npm e Create React App.

## Aplicação prática no projeto
O Mini Apps utiliza useState para controlar a página atual, o contador e os dados dos exercícios. A função renderPagina seleciona o componente conforme o estado.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Criar um contador com incremento e reset.
2. construir um componente de menu.
3. renderizar uma lista com identificadores.

## Referências
- [Repositório mini-apps-react](https://github.com/ZPoizon/mini-apps-react)
- [Documentação de referência](https://react.dev/learn)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Estrutura e dependências reais

- package.json: React e React DOM ^19.2.8; react-scripts 5.0.1; Testing Library e web-vitals.
- package-lock.json: registra a árvore resolvida de dependências npm.
- public/: recursos estáticos do Create React App.
- src/index.js: ponto de entrada; src/App.js: aplicação principal; src/App.css e src/index.css: estilos disponíveis; src/App.test.js e setupTests.js: infraestrutura de testes.
- O App.js também contém estilos em uma tag style com template literal.

O projeto usa Create React App, não Vite. Os scripts são npm start, npm run build e npm test.

### Estado e renderização

```jsx
const [cliques, setCliques] = useState(0);
<button onClick={() => setCliques(cliques + 1)}>
  Clique aqui
</button>
```

O hook retorna o valor do estado e a função de atualização. O JSX incorpora expressões JS entre chaves. React renderiza novamente a interface quando o estado muda. Não é necessário usar getElementById para atualizar a contagem.

Inicio, TodoList, Contador, JogoDaVelha, Calculadora e BuscadorCep são funções declaradas dentro de App. A seleção da tela é feita por switch em renderPagina(), não por React Router. O menu usa aplicativos.map e key={app.id}. Props são um conceito relevante de React, mas este código concentra a maior parte do estado no componente App.

**Ponto de revisão:** declarar componentes dentro de App pode recriar sua identidade nas renderizações e provocar remontagem; separar componentes é uma melhoria possível.

**Fontes:** [package.json](https://github.com/ZPoizon/mini-apps-react/blob/main/package.json), [App.js](https://github.com/ZPoizon/mini-apps-react/blob/main/src/App.js).
