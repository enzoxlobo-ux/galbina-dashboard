# CLAUDE.md — Galbina Dashboard

## O QUE É

Dashboard financeiro web da Galbina (escritório de consultoria financeira).
Arquivo HTML único, sem build, sem framework. Lê dados de uma planilha Google
Sheets publicada como CSV e renderiza 4 seções: Visão Geral, Insights & Análises,
Lançamentos, Projetos.

Cliente-piloto: ZancaFilms (produtora de vídeo).
O dashboard será compartilhado por link com o cliente final.

## STATUS ATUAL

- `index.html` já existe e funciona — motor de CSV, parsers, 4 renderizadores,
  Chart.js, identidade visual Galbina (azul petróleo + dourado, fontes Fraunces/Outfit).
- Hoje roda com dados de FALLBACK embutidos (exemplo da ZancaFilms).
- Falta: conectar aos CSVs reais do Sheets + publicar no GitHub Pages.

## OBJETIVO DESTA FASE

1. Versionar o projeto no GitHub (repositório novo)
2. Conectar o dashboard à planilha real via CSV publicado
3. Publicar ao vivo no GitHub Pages
4. Garantir que atualiza automaticamente quando a planilha muda

## STACK

- HTML/CSS/JS puro, arquivo único (`index.html`)
- Chart.js 4.4 via CDN
- Fontes via Google Fonts
- Fonte de dados: Google Sheets publicado como CSV
- Hospedagem: GitHub Pages
- SEM build, SEM npm, SEM framework — manter assim

## ESTRUTURA DO CÓDIGO (index.html)

O arquivo tem 8 blocos lógicos, em ordem:
1. head + CSS (design system com CSS variables)
2. body HTML (loader, header, sidebar, 4 módulos)
3. JS motor (parseCSV, parseDateBR, parseNum, formatadores)
4. JS dados (FALLBACK + parsers por aba: parseNFs, parseDespesas, parseProjetos)
5. JS cálculo (calcularKPIs, agruparDespesas, calcularProjetos, evolucaoMensal)
6. JS render M1 + M2
7. JS render M3 + M4
8. JS init (navegação, filtros, carregarDados, fetchCSV)

A config dos links CSV fica no objeto `CSV = {}` no topo do bloco 3.

## REGRAS

- NUNCA quebrar o arquivo em múltiplos arquivos. É single-file por design
  (facilita hospedar, versionar, e o usuário entender).
- NUNCA adicionar build step, bundler, ou dependência npm.
- O FALLBACK embutido deve continuar funcionando — é o que permite testar
  sem depender do Sheets. Não remover.
- Toda mudança de cor/fonte passa pelas CSS variables no :root.
- Os parsers (parseNFs etc.) usam a função `col()` que é tolerante a variação
  de nome de coluna. Manter essa tolerância — a planilha pode ter cabeçalhos
  ligeiramente diferentes.
- Commits pequenos e descritivos.

## COMO O USUÁRIO TRABALHA

Enzo está aprendendo desenvolvimento. Explique cada decisão antes de executar.
Ele prefere entender o "porquê" antes do "como". Trabalha no Claude Code para
execução e no Claude.ai (projeto separado) para estratégia.

## PLANILHA DE ORIGEM

A planilha tem 9 abas. O dashboard só consome 4:
- "💰 NFs Emitidas" → CSV.nfs
- "💸 Custos e Despesas" → CSV.despesas
- "🎬 Projetos" → CSV.projetos
- "⚙️ Configurações" → CSV.config

As outras abas (Painel, Análises, Mensal, Histórico) são visuais da própria
planilha — o dashboard recalcula tudo a partir das 4 abas de dados.
