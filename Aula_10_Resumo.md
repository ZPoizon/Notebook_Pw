# Aula 10 — PWA, testes, build e publicação

**Professor da disciplina:** Me. Deivison S. Takatu

> Registro temático de revisão, elaborado a partir dos projetos do semestre. A numeração é organizacional e não representa uma aula oficial ou data confirmada.

## Resumo
Entender como preparar uma aplicação web para distribuição e manutenção. O conteúdo é relacionado ao projeto [Ecoa](https://github.com/ZPoizon/Ecoa), permitindo revisar a teoria junto à prática.

## Objetivos de aprendizagem
- Compreender os conceitos centrais de PWA, testes, build e publicação.
- Identificar sua aplicação no código e na estrutura do projeto.
- Relacionar os conceitos à construção e manutenção de aplicações web.

## Conteúdo principal
- Web App Manifest e instalação.
- Service Worker, ciclo de vida e cache.
- limites de uso offline.
- Node.js e scripts npm.
- build e diretório dist.
- testes automatizados.
- Vercel e funções serverless.
- Git, commits e revisão.
- diferenças entre desenvolvimento e produção.

## Aplicação prática no projeto
Ecoa possui manifest.json, sw.js, build.cjs, validar.cjs, tests e vercel.json. O README documenta npm run dev, npm test, npm run build e npm run preview. Consultas externas podem exigir internet.

## Metodologia e recursos
Leitura de código-fonte, revisão da documentação técnica, análise da estrutura do repositório e exercícios de implementação. Os exercícios abaixo são propostas de revisão, não atividades oficiais atribuídas ao professor.

## Atividades de revisão
1. Executar testes e build.
2. verificar cache após primeira visita.
3. testar comportamento sem conexão.
4. revisar a saída de produção e configurações de hospedagem.

## Referências
- [Repositório Ecoa](https://github.com/ZPoizon/Ecoa)
- [Documentação de referência](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps)
- [Caderno de Programação Web](./README.md)

---
Resumo temático baseado nos arquivos e documentação dos projetos acadêmicos.


---

## Integrações geográficas e persistência

| Tecnologia | Arquivo / utilização |
| --- | --- |
| Photon | enderecos.js: https://photon.komoot.io/api/ e /reverse, geocodificação direta e reversa |
| ViaCEP | enderecos.js: busca de CEP por /ws/{codigo}/json/ |
| Overpass API | pontos-osm.js: overpass-api.de e overpass.private.coffee, consulta a dados OSM por área e categoria |
| Leaflet | Biblioteca de mapa documentada no README |
| OpenStreetMap | Fonte de dados geográficos, não é o mesmo que Leaflet |
| Google Maps | pontos-osm.js: construção de link externo de rota |
| Supabase/PostgreSQL | pontos-compartilhados.js e supabase/schema.sql |
| localStorage | plano.js: armazenamento do plano e vínculos com pontos |
| pdf-lib | Exportação PDF documentada e módulo plano-pdf.js |

O autocomplete aplica debounce de 350 ms, consulta a partir de três caracteres, cancela requisições antigas com AbortController e usa atributos ARIA para interação por teclado. O módulo OSM monta consultas por bounding box (área delimitada por coordenadas), converte dados externos e combina pontos locais e remotos. A disponibilidade depende dos provedores e da cobertura regional.

### Banco relacional e segurança

schema.sql define public.pontos e public.denuncias, ambas com chave primária UUID. denuncias.ponto_id é chave estrangeira para pontos.id com ON DELETE CASCADE. Existem CHECKs para categoria, status, coordenadas e campos de texto. As extensões unaccent e pg_trgm auxiliam buscas sem acento e índices textuais GIN; há índices parciais de pontos aprovados por cidade, categoria e área.

O SQL ativa RLS nas duas tabelas. O visitante anon recebe SELECT em pontos, mas a policy restringe a leitura a aprovados. O cadastro anônimo de novos pontos foi removido: a policy antiga de INSERT permanece, porém não existe o GRANT correspondente. O visitante pode inserir apenas ponto_id e motivo em denúncias de pontos aprovados. Não há autorização de UPDATE/DELETE para visitantes. Um trigger incrementa a contagem de denúncias no banco.

```sql
-- Trecho real da política de leitura
create policy "Visitante le apenas aprovados"
on public.pontos for select to anon
using(status='aprovado');
```

RLS e GRANT atuam em conjunto. A chave pública não deve ser confundida com chave secreta de serviço. O plano pessoal não é sincronizado automaticamente pelo Supabase: plano.js serializa os dados localmente com JSON.stringify e recupera com JSON.parse; também permite importação e exportação.

**Fontes:** [enderecos.js](https://github.com/ZPoizon/Ecoa/blob/main/public/enderecos.js), [pontos-osm.js](https://github.com/ZPoizon/Ecoa/blob/main/public/pontos-osm.js), [schema.sql](https://github.com/ZPoizon/Ecoa/blob/main/supabase/schema.sql), [plano.js](https://github.com/ZPoizon/Ecoa/blob/main/public/plano.js).
