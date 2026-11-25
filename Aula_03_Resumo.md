# Aula 03 — JavaScript puro — Lógica, DOM e eventos

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Implementar comportamento interativo e compreender como dados alteram uma página. O conteúdo é relacionado ao projeto [Pwsite](https://github.com/ZPoizon/Pwsite), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de JavaScript puro.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- Variáveis let e const.
- funções, arrays, objetos e condicionais.
- métodos map e forEach.
- DOM com getElementById e querySelectorAll.
- eventos de clique.
- classList e textContent.
- estado da aplicação.
- setTimeout e setInterval.
- localStorage e Web Audio API.

## Aplicação prática no projeto
O quiz mantém um objeto de estado com pontuação, pergunta atual e tempo restante. As telas são alternadas por classes CSS e os recordes são consultados no localStorage. A lógica está em script.js, embora o HTML referencie app.js.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Implementar um contador de pontos, alternar telas com botões e salvar um recorde local.
2. conferir a referência ao script no HTML.

## Referências
- [Repositório Pwsite](https://github.com/ZPoizon/Pwsite)
- [Documentação de referência](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Anatomia do motor JavaScript

O script.js possui 799 linhas na versão consultada. Organiza dados locais, áudio, estado, referências DOM, utilitários, integração externa, jogo, resultados e eventos.

| Identificador real | Responsabilidade |
| --- | --- |
| CURATED_QUESTIONS_PTBR / CURATED_QUOTES | Arrays de objetos usados como acervo local |
| SoundEngine | Classe que usa AudioContext, osciladores e controle de ganho |
| state | Modo, dificuldade, questões, índice, score, streak, timer e bloqueio |
| dom | Referências a elementos HTML obtidas por seletores |
| shuffleArray | Cópia com spread e embaralhamento Fisher–Yates |
| showScreen | Remove a classe active das telas e ativa a escolhida |
| startQuiz / loadQuestion | Inicializa a partida e carrega questões |
| startTimer / handleTimeOut | Controle de tempo |
| handleOptionSelect | Processamento de resposta |
| finishQuiz / renderReviewList | Resultados e revisão |
| setupEventListeners | Associação dos eventos de interface |

Exemplo reduzido da lógica real:

```js
function showScreen(screenEl) {
  [dom.screenHome, dom.screenLoading, dom.screenQuiz, dom.screenResults]
    .forEach(s => s.classList.remove('active'));
  screenEl.classList.add('active');
}
```

A função não navega para outro HTML; apenas altera a classe. O objeto state centraliza o estado e a interface é atualizada manualmente. O evento DOMContentLoaded inicializa a aplicação; clearInterval evita manter temporizadores antigos quando uma partida começa.

As chaves anime_quiz_high_score e anime_quiz_max_streak persistem recordes por origem no localStorage. Os valores são strings e são convertidos com parseInt ao comparar recordes. Não existe banco remoto nesse projeto.

**Fonte:** [script.js](https://github.com/ZPoizon/Pwsite/blob/HEAD/script.js).
