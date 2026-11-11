# Implementação — Dashboard DEMO comercial

1. Confirmar a planilha DEMO e exportar a versão atual como XLSX para arquivo temporário.
2. Validar que o XLSX é um pacote íntegro e substituir `demo/dados/base_atual.xlsx` apenas após sucesso.
3. Adicionar o perfil `demo` ao gerador compartilhado, mantendo os quatro perfis oficiais inalterados.
4. Gerar `entregas/demo/Dashboard_Demo.html` com código visual local e dados embutidos.
5. Acrescentar testes específicos do DEMO para confirmar identidade, três cenários financeiros, isolamento e ausência de fontes reais.
6. Executar os testes de snapshot, motor e acesso visual aplicáveis.
7. Revisar o dashboard localmente nos temas claro e escuro e conferir os principais valores contra a planilha.
8. Copiar apenas o HTML aprovado para `dashboard/demo.html`.
9. Fazer commit e push apenas dos arquivos do DEMO e da documentação, sem publicar XLSX, códigos ou auditorias.
10. Acompanhar o GitHub Pages até sucesso e validar `https://enzoxlobo-ux.github.io/galbina-dashboard/demo.html`.
