# Aula 04 — APIs — HTTP, JSON e assincronismo

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Compreender a comunicação entre aplicações e tratar respostas externas. O conteúdo é relacionado ao projeto [Pwsite](https://github.com/ZPoizon/Pwsite), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de APIs.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- Cliente e servidor.
- URL e endpoint.
- HTTP e métodos GET, POST, PUT e DELETE.
- status de resposta.
- JSON.
- fetch e Promises.
- async/await.
- try/catch/finally.
- validação, carregamento e tratamento de falhas.
- CORS como política do navegador.

## Aplicação prática no projeto
O quiz prevê perguntas da Open Trivia DB e possui questões locais. O buscador de CEP do Mini Apps consulta ViaCEP, valida oito dígitos e trata erros de rede e CEP inexistente.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Consultar um CEP com fetch.
2. converter a resposta em JSON.
3. exibir endereço e mensagens de erro.
4. testar entradas inválidas.

## Referências
- [Repositório Pwsite](https://github.com/ZPoizon/Pwsite)
- [Documentação de referência](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Contratos de API encontrados no código

| Serviço | Endpoint usado | Dados e tratamento |
| --- | --- | --- |
| Open Trivia DB | https://opentdb.com/api.php | amount, category=31, type=multiple, difficulty opcional; resposta results e response_code |
| AnimeChan | https://animechan.xyz/api/random | O código espera quote, character e anime; combina uma citação remota com acervo local |
| ViaCEP | https://viacep.com.br/ws/{cep}/json/ | CEP, logradouro, bairro, localidade, uf, ddd e indicador erro |

fetchTriviaQuestions verifica res.ok, decodifica entidades HTML com decodeHtml, combina respostas corretas e incorretas e embaralha as alternativas. Se falhar ou não houver resultados, retorna questões locais. fetchQuoteQuestions também possui fallback. O funcionamento atual dos serviços não foi testado.

No Mini Apps, buscarCep retira caracteres não numéricos, verifica comprimento, ativa carregando, limpa erros antigos, consulta ViaCEP e trata falha no finally. Uma resposta HTTP bem-sucedida não garante que o CEP exista: é necessário verificar dados.erro.

```js
// Exemplo reduzido da consulta presente no Mini Apps
const resposta = await fetch(
  `https://viacep.com.br/ws/${cepLimpo}/json/`
);
if (!resposta.ok) throw new Error("Erro na consulta");
const dados = await resposta.json();
```

**Conceitos para prova:** API não é necessariamente banco de dados; endpoint é um endereço de operação; JSON é serialização de dados; await aguarda uma Promise dentro de uma função async; fetch não rejeita automaticamente todo erro HTTP.

**Fontes:** [Pwsite/script.js](https://github.com/ZPoizon/Pwsite/blob/HEAD/script.js), [Mini Apps/App.js](https://github.com/ZPoizon/mini-apps-react/blob/main/src/App.js).
