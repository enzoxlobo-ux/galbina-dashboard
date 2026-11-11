# Dashboard DEMO — especificação de desenho

## Objetivo

Criar um dashboard comercial demonstrativo no mesmo modelo executivo dos dashboards Gaibina em produção, alimentado exclusivamente pela planilha Google Sheets `MODELO DEMO | APRESENTAÇÃO COMERCIAL` (`1mefQXYLhA0yllcbJ1V2sVqO8eKJZcLkrOirv6385ZCE`). O arquivo deve permitir que Mônica apresente o produto sem expor dados de clientes reais.

## Escopo aprovado

- Fonte exclusiva: planilha DEMO, com dados explicitamente fictícios.
- Saída local: `entregas/demo/Dashboard_Demo.html`.
- Saída pública: `dashboard/demo.html`, no mesmo GitHub Pages dos demais dashboards.
- Acesso: código visual distinto e estável, com a mesma limitação cosmética dos dashboards atuais.
- Atualização: manual nesta fase; o DEMO não entra na automação oficial das 08h e 16h.
- Modelo visual e motor: reutilizar `dashboard/index.html` e `ferramentas/gerar_snapshot.py`, sem criar um segundo motor.

## Dados demonstrativos esperados

O snapshot deve refletir somente os registros fictícios cadastrados em 11/11/2026:

- projeto `Campanha Institucional DEMO`;
- receita recebida de R$ 4.800,00;
- receita emitida a receber de R$ 3.600,00;
- despesa a pagar de R$ 1.250,00;
- saldo inicial fictício de R$ 50.000,00 e posição demonstrativa resultante de R$ 54.800,00.

A despesa sem Data de Pagamento não deve entrar como saída realizada nem na conciliação. A NF sem Data de Recebimento deve permanecer em `A receber`.

## Arquitetura e isolamento

1. Exportar a planilha DEMO para `demo/dados/base_atual.xlsx`, usando arquivo temporário antes da substituição.
2. Adicionar um perfil `demo` ao gerador compartilhado, apontando apenas para a base e a entrega do DEMO.
3. Preservar as configurações dos clientes Horda, Zanca, Mission e Brasis sem alterações funcionais.
4. Gerar um HTML autossuficiente, com dados e Chart.js embutidos, sem buscar dados de clientes reais.
5. Copiar somente a entrega aprovada para `dashboard/demo.html`.

## Publicação e segurança

O GitHub Pages é público. O código de entrada é apenas uma barreira visual e não deve ser apresentado como autenticação segura. O HTML não deve conter links para planilhas reais, códigos de outros clientes, credenciais ou arquivos de auditoria.

## Validação

- validar a exportação XLSX antes de substituir a base local;
- executar os testes de snapshot, motor e acesso visual aplicáveis ao perfil DEMO;
- confirmar os valores principais do snapshot contra a planilha DEMO;
- revisar visualmente o HTML em tema claro e escuro;
- publicar somente `demo.html` após os testes;
- acompanhar o workflow do GitHub Pages até `success` e conferir o link público.

## Fora do escopo

- incluir o DEMO na rotina automática das 08h e 16h;
- editar o modelo virgem ou a planilha da Bravo;
- usar dados reais ou copiar dados dos quatro clientes oficiais;
- criar autenticação real, domínio ou serviço pago.
