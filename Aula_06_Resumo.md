# Aula 06 — React — Miniaplicações e lógica de programação

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Aplicar estado e estruturas de dados em problemas interativos. O conteúdo é relacionado ao projeto [mini-apps-react](https://github.com/ZPoizon/mini-apps-react), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de React.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- To-do list: inclusão, conclusão e exclusão com map, filter e spread.
- contador: atualização de estado.
- jogo da velha: array de nove posições, combinações vencedoras, empate e alternância.
- calculadora: entrada, operações e erros.
- buscador de CEP: validação e consulta assíncrona.
- atualização imutável de arrays.

## Aplicação prática no projeto
As cinco ferramentas estão reunidas em src/App.js, com navegação por estado. A calculadora usa eval, uma abordagem que deve ser substituída por um avaliador matemático restrito. As tarefas ficam no estado em memória.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Implementar as cinco ferramentas.
2. testar vitória e empate.
3. evitar entradas vazias.
4. tratar CEP inválido e substituir eval como melhoria.

## Referências
- [Repositório mini-apps-react](https://github.com/ZPoizon/mini-apps-react)
- [Documentação de referência](https://react.dev/learn/updating-arrays-in-state)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Implementação das cinco ferramentas

| Ferramenta | Estado real | Algoritmo / funções |
| --- | --- | --- |
| Tarefas | tarefas, novaTarefa | adicionarTarefa, concluirTarefa, excluirTarefa |
| Contador | cliques | incremento e reset |
| Jogo da velha | tabuleiro, jogador | verificarVencedor, jogar, reiniciarJogo |
| Calculadora | valorCalculadora | adicionarNumero, calcular, limparCalculadora |
| CEP | cep, endereco, erroCep, carregando | alterarCep, buscarCep |

A tarefa possui id gerado por Date.now(), texto e concluida. O spread cria uma nova lista ao adicionar; map altera somente a tarefa encontrada e filter remove o ID. Não há persistência de tarefas após recarregar.

```js
// Trecho da lógica de exclusão
setTarefas(tarefas.filter(tarefa => tarefa.id !== id));
```

O jogo começa com Array(9).fill(""). O algoritmo verifica oito combinações de três casas; o empate exige tabuleiro cheio e ausência de vencedor. jogar impede movimentos em casas ocupadas ou após encerramento, copia o tabuleiro e alterna X/O. O resultado é derivado do estado, não precisa ser armazenado separadamente.

A calculadora concatena operadores e números em uma string e usa eval dentro de try/catch. Isso executa JavaScript e não é apropriado para entrada livre; um parser matemático restrito é mais seguro. O buscador utiliza inputMode numérico, autoComplete postal-code e maxLength 9; permite hífen e consulta após normalizar o CEP.

### Casos de revisão sugeridos
| Cenário | Resultado esperado |
| --- | --- |
| Tarefa em branco | Não adicionada |
| Excluir tarefa | Apenas o ID correspondente removido |
| Três X na mesma linha | Vitória de X |
| Casa já ocupada | Jogada ignorada |
| CEP com menos de 8 dígitos | Mensagem de validação |
| Erro de rede | Mensagem e fim do carregamento |

Esses casos são propostas de teste, não resultados de execução.

**Fonte:** [src/App.js](https://github.com/ZPoizon/mini-apps-react/blob/main/src/App.js).
