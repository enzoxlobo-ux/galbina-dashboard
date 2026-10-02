# Dashboard Executivo Horda — desenho aprovado

## Objetivo

Entregar à direção uma única página de leitura rápida, baseada no snapshot oficial da Horda, sem misturar competência com caixa e sem duplicar impostos.

## Estrutura da página

1. **Posição bancária**: saldo disponível, aplicado e total.
2. **Horizonte de caixa**: hoje, 7, 15 e 30 dias, com entradas e saídas previstas dos próximos 30 dias.
3. **Resumo de competência do ano**: receita bruta emitida, imposto apurado nas NFs, receita líquida, custos vinculados a projetos e resultado gerencial.
4. **Comparativo 2025 × 2026**: somente faturamento bruto emitido, por mês.
5. **A receber**: total aberto, vencido e sem vencimento informado.
6. **Top clientes**: bruto, imposto, líquido, custos vinculados, resultado e margem.
7. **Pendências de qualidade**: alertas objetivos para dados que dependem de classificação humana.

## Regras financeiras

- O imposto de competência vem exclusivamente da coluna **Valor Imposto** da aba **NFs Emitidas**. A alíquota é variável e administrada na própria NF.
- O resultado gerencial é `receita líquida das NFs - custos vinculados aos projetos`.
- Guias de imposto pagas em **Custos e Despesas** continuam sendo saídas de caixa, mas não são descontadas novamente do resultado gerencial se o imposto da NF já foi reconhecido.
- Custos sem projeto não entram no resultado por cliente/projeto.
- O comparativo 2025 × 2026 é de faturamento, porque não existe uma base consolidada equivalente de custos de 2025.
- Nenhum dado ausente é estimado, preenchido ou reclassificado automaticamente.

## Fonte e distribuição

- Fonte: planilha oficial Horda no Google Drive, exportada em 02/10/2026.
- Entrega offline: HTML único, com dados e Chart.js embutidos.
- Entrega por link: cópia estática do mesmo snapshot publicada no GitHub Pages.
- A página identifica a data do snapshot; não afirma atualização automática quando estiver usando dados embutidos.

