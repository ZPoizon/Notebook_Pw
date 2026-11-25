# Aula 07 — React e Vite — CRUD de notas e API REST

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Conectar uma interface a um serviço remoto e compreender operações CRUD. O conteúdo é relacionado ao projeto [Notas-React-interface](https://github.com/ZPoizon/Notas-React-interface), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de React e Vite.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- Vite e servidor de desenvolvimento.
- useState e useEffect.
- formulários controlados.
- preventDefault.
- GET para leitura, POST para criação, PUT para edição e DELETE para exclusão.
- JSON.stringify e Content-Type.
- identificação de registros.
- confirmação de exclusão.
- atualização da lista após operações.

## Aplicação prática no projeto
O arquivo notas-react/src/App.jsx consulta uma API hospedada no Render. O formulário alterna entre criação e edição. O código carrega as notas ao iniciar e após alterações. O back-end e o banco não estão neste repositório.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Executar npm install e npm run dev dentro de notas-react.
2. cadastrar, editar e excluir notas em ambiente de teste autorizado.
3. verificar status HTTP e melhorar feedback de erros.

## Referências
- [Repositório Notas-React-interface](https://github.com/ZPoizon/Notas-React-interface)
- [Documentação de referência](https://react.dev/reference/react/useEffect)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Arquitetura e contrato observado

O diretório notas-react contém package.json, vite.config.js, index.html, public e src. O projeto é ES module (type: module). Dependências: React e React DOM ^19.2.8; Vite ^8.3.0, plugin React ^6.1.1 e Oxlint ^1.81.0 como ferramentas de desenvolvimento.

```text
Interface React (App.jsx)
    -> fetch / JSON / HTTP
    -> API hospedada no Render
    -> resposta com notas
    -> setNotas -> interface atualizada
```

URL configurada: https://notas-api-6o5u.onrender.com/api/notes.

| Método | Caminho | Dados enviados |
| --- | --- | --- |
| GET | /api/notes | Nenhum corpo |
| POST | /api/notes | titulo, texto, criadoEm (ISO 8601) |
| PUT | /api/notes/{id} | titulo, texto |
| DELETE | /api/notes/{id} | Nenhum corpo |

A interface espera id, titulo, texto e criadoEm nos registros. O estado editando indica o ID selecionado; editarNota preenche o formulário; cancelarEdicao limpa os campos; salvarNota usa preventDefault e escolhe POST ou PUT; excluirNota pede confirmação; carregarNotas executa GET e setNotas. A apresentação converte criadoEm com toLocaleString("pt-BR").

```jsx
useEffect(() => {
  carregarNotas();
}, []);
```

O efeito inicia a leitura após a montagem. Não confundir useEffect (sincronização com sistema externo) com useState (dados da interface).

### Limitações e melhorias verificáveis
O código não verifica resposta.ok antes de considerar as operações de escrita concluídas, nem exibe estado de carregamento; os erros são principalmente registrados no console. A API remota não foi chamada para evitar alterações em dados reais. O banco, framework do servidor, autenticação e políticas CORS não podem ser determinados apenas por esse front-end.

**Fontes:** [App.jsx](https://github.com/ZPoizon/Notas-React-interface/blob/main/notas-react/src/App.jsx), [package.json](https://github.com/ZPoizon/Notas-React-interface/blob/main/notas-react/package.json).
