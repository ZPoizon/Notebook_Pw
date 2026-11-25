# Aula 09 — Ecoa — Interface, persistência e integração de serviços

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo

O [Ecoa](https://github.com/ZPoizon/Ecoa) reúne os conhecimentos de Programação Web em uma aplicação educativa sobre os 17 ODS. O projeto ajuda a encontrar ações conforme o tempo, o orçamento e o contexto da pessoa. É independente e não oficial da ONU.

## Objetivos de aprendizagem

- Relacionar requisitos, experiência do usuário e organização do código.
- Diferenciar armazenamento local e dados compartilhados.
- Integrar APIs e compreender as políticas de acesso aos dados.

## Interface e organização

- Definição do problema, levantamento de requisitos e filtros por tempo e orçamento.
- HTML, CSS e JavaScript organizados por responsabilidade.
- Design responsivo, acessibilidade, navegação por teclado e feedback visual.
- Seções Agir, Aprender, Na cidade e Meu espaço, com ações, guias, quiz e plano pessoal.
- Distinção entre informações oficiais, sugestões educativas e estimativas.

## Persistência, mapas e serviços

| Tecnologia | Aplicação no projeto |
| --- | --- |
| localStorage e JSON | Plano pessoal, preferências e cópia de segurança no navegador |
| Leaflet e OpenStreetMap | Exibição do mapa e consulta de lugares |
| Overpass, Photon e ViaCEP | Pontos geográficos, endereços e CEPs |
| Supabase e PostgreSQL | Dados compartilhados e políticas de acesso com RLS |
| pdf-lib | Exportação do plano em PDF |

O armazenamento local não sincroniza automaticamente entre aparelhos. As integrações externas dependem da conexão e da disponibilidade dos serviços. A chave pública do Supabase pode estar no cliente, mas os segredos não devem ser publicados e as políticas do banco precisam restringir o acesso.

## Atividades de revisão

1. Explorar os filtros e salvar uma ação no plano.
2. Recarregar a página e conferir a persistência dos dados.
3. Exportar uma cópia de segurança e gerar o PDF.
4. Pesquisar um endereço e identificar a origem dos pontos.
5. Revisar responsividade, navegação por teclado e mensagens da interface.
6. Conferir as políticas de acesso em ambiente de teste, sem publicar segredos.

As atividades são propostas de revisão por leitura de código, documentação e exercícios de implementação, não atividades oficiais atribuídas ao professor.

## Referências

- [Repositório e documentação do Ecoa](https://github.com/ZPoizon/Ecoa)
- [ODS — ONU Brasil](https://brasil.un.org/pt-br/sdgs)
- [Row Level Security — Supabase](https://supabase.com/docs/guides/database/postgres/row-level-security)
- [Aula 10 — PWA, testes, build e publicação](./Aula_10_Resumo.md)
- [Caderno de Programação Web](./README.md)


---

## Organização efetiva do Ecoa

| Arquivos em public/ | Responsabilidade |
| --- | --- |
| index.html, app.js, estrutura.js | Interface e organização da aplicação |
| rotas.js | Navegação por hash, histórico e abas |
| acoes.js, agir.js, agir.css | Catálogo e busca de ações |
| guias.js, aprender.js, quiz.js, quiz-ui.js | Conteúdo educativo e questionários |
| estimativa.js, estimativa-ui.js | Modelos e interface de estimativas |
| cidade.js, cidade-ui.js, cidade-busca.js | Experiência de consulta de locais |
| plano.js, progresso.js, desafio.js, rotina.js | Planejamento e acompanhamento |
| design-system.css, acessibilidade.js, acessibilidade.css | Consistência visual e recursos de acessibilidade |

Não há dependência de framework de interface. O projeto usa JavaScript modular por responsabilidades e scripts de build próprios. O resolverRotaEcoa(hash) e os ouvintes hashchange/popstate mostram navegação por fragmento de URL, sem React Router ou Vue Router. A navegação também gerencia foco de teclado e abas.

### Lógica de negócio: estimativas de impacto

O módulo estimativa.js valida valores numéricos, intervalos e campos inteiros antes de calcular. Exemplos de fórmulas reais:
- Banhos: (duração anterior − duração nova) × 10 L/min × quantidade de banhos.
- Energia: potência em W × quantidade × horas × dias ÷ 1.000 = kWh.
- Alimentos: gramas ÷ 1.000 = kg.
- Óleo: mililitros ÷ 1.000 = L.

Exemplo didático: reduzir 5 minutos em 10 banhos gera um cenário de referência de 500 L, assumindo vazão constante de 10 L/min. Não se trata de uma medição real. O projeto explicita fontes e limites das estimativas.

**Fontes:** [rotas.js](https://github.com/ZPoizon/Ecoa/blob/main/public/rotas.js), [estimativa.js](https://github.com/ZPoizon/Ecoa/blob/main/public/estimativa.js), [public/](https://github.com/ZPoizon/Ecoa/tree/main/public).
