# Dashboard financeiro da Horda — desenho aprovado

## Objetivo

Atualizar o dashboard HTML existente da Gaibina para usar a Horda como cliente-piloto da nova fase, preservando o arquivo único, as melhorias locais ainda não commitadas e a separação entre dados de clientes.

O primeiro entregável será um HTML fechado para validação de Mônica, Tânia e Cinira. A planilha oficial será consultada de forma autenticada apenas durante a geração do arquivo. Nenhuma aba ou CSV financeiro será publicado na web nesta fase.

## Fonte oficial

- Cliente: Horda / Warner.
- Planilha: `1FPy7nHDvjtgav17s0koY8VUZpksGTfuEFzRatAd4_Lg`.
- O arquivo vivo do Google Sheets é a fonte de verdade.
- O XLSX local antigo pode ser usado somente para comparação estrutural, nunca para substituir dados mais recentes.
- O dashboard não altera a planilha.

## Arquitetura

### Aplicação

- Manter `index.html` como aplicação single-file, sem framework, npm ou etapa de build.
- Preservar o fallback para testes, mas identificá-lo claramente como demonstração.
- Criar um perfil de cliente configurável dentro do próprio HTML, para evitar referências fixas à Zanca.
- Corrigir a marca de `Galbina` para `Gaibina` onde aparecer na interface e nos textos técnicos.

### Geração do snapshot

- Ampliar o gerador existente para aceitar `horda`.
- Exportar ou consultar a planilha oficial por acesso autenticado.
- Normalizar apenas os campos necessários e injetar os dados no HTML.
- O arquivo final não fará chamadas a CSV ou a serviços externos de dados.
- A data e a origem do snapshot serão exibidas na interface.

### Fontes de dados

- `🎬 Projetos`: cadastro, status, empresa do grupo e módulos estimado e realizado.
- `💰 NFs Emitidas`: faturamento, imposto, recebimento, cliente, projeto, conta e empresa.
- `💸 Custos e Despesas`: custos, despesas, comissões, pagamentos, projeto, conta e empresa.
- `Entradas Diversas 💸`: entradas de caixa que não são faturamento.
- `💵 Fluxo de Caixa`: saldos por conta e horizontes projetados.
- `🧩 Base Conciliação`: movimentos bancários normalizados, inclusive transferências, aplicações, resgates e rendimentos.
- `⚙️ Configurações`: contas, empresas e parâmetros mestres.
- `🏠 Painel`: controle de conferência, não fonte principal dos cálculos quando a base operacional estiver disponível.

## Regras financeiras

### Projetos

- Usar o módulo realizado da Horda em P:U: receita realizada líquida, outros custos pagos, comissão paga, custos pagos totais, resultado realizado e margem realizada.
- Manter custo estimado e receita prevista como referência de previsão, sem misturar com realizado.
- Projetos vigentes: início em 2026 e status `Em produção`.
- Projetos pagos: status `✅ Pago`.
- Não aplicar uma alíquota genérica sobre receita já líquida do módulo realizado.

### Caixa e conciliação

- NFs recebidas entram como faturamento realizado conforme os campos da planilha.
- Custos entram no caixa pela data de pagamento.
- Custos negativos permanecem como reembolsos, sem duplicação em Entradas Diversas.
- Entradas Diversas afetam caixa, não faturamento.
- Aplicações, resgates e transferências movimentam contas, mas não criam receita ou despesa econômica.
- Rendimentos entram no caixa e ficam identificados separadamente.
- Mútuos entre empresas do grupo não viram faturamento.
- Não inferir tipo, conta, empresa ou classificação ausente.

## Experiência e visual

- Preservar a linguagem visual já construída e as melhorias locais de tema, responsividade e acessibilidade.
- Alinhar as cores à identidade oficial Gaibina: grafite e verde, com vermelho para saídas e âmbar para validação.
- Adicionar filtros globais por ano, mês, empresa do grupo e conta bancária.
- Exibir estados de fonte, data do snapshot e dados ausentes sem usar zeros enganosos.
- Manter cinco módulos: Visão Geral, Caixa, Insights e Análises, Lançamentos e Projetos.

## Validação

- Conferir totais do dashboard contra as abas oficiais para 2026.
- Validar separadamente Gabriel, Getúlio e Rafael.
- Conferir pelo menos uma conta corrente e uma aplicação.
- Conferir um projeto realizado, um projeto sem realizado e os estados `Em produção` e `✅ Pago`.
- Validar aplicações, resgates, transferências, rendimentos e entradas diversas sem dupla contagem.
- Testar desktop, mobile, tema claro, tema escuro e abertura local do HTML.
- Tratar divergências como erro de cálculo ou ausência de fonte; nunca completar dados por inferência.

## Fora do escopo desta entrega

- Publicação de CSV da Horda.
- Hospedagem pública, GitHub Pages e domínio.
- Autenticação multiusuário.
- Edição da planilha pelo dashboard.
- Replicação para Zanca, Mission ou Brasis antes da validação do piloto da Horda.

