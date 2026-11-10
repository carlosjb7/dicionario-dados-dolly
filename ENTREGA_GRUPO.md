# Entrega ao Grupo 03 - revisão do site 1.2

Data: 10/11/2026.
Site: https://carlosjb7.github.io/dicionario-dados-dolly/
Repositório: https://github.com/carlosjb7/dicionario-dados-dolly

## O que está concluído neste pacote

Código integral separado em index.html, style.css e script.js, com 19 tabelas e 115 atributos do DDL. Busca por tabela/atributo, tema persistente, menu móvel, visualizador com zoom/arraste/reset, alternativa textual e downloads. A busca trata singular/plural, o zoom aguarda a imagem carregar e o menu móvel transfere o foco ao destino escolhido.

DDL original preservado em docs/ddl_original.sql. Exportação dos metadados em docs/catalogo.json. Nenhuma tabela ou coluna foi adicionada ao banco. Rotinas de negócio não fornecidas no DDL continuam sendo pendências, e não funcionalidades implementadas pelo site.

## Duas pendências obrigatórias antes da entrega final da AT6

1. Documento de requisitos: recuperar o modelo editável oficial da AT2 com o professor ou no ambiente da disciplina. Aplicar as correções do RELATORIO.md preservando layout, cores, tabelas, cabeçalhos e estrutura do modelo. Os PDFs recebidos não disponibilizam esse original editável. O arquivo docs/Especificacao_Requisitos_Regras_Negocio_BD.pdf deste pacote é uma PROPOSTA TÉCNICA POR ERRATA em outro layout; não é a especificação final aceita pelo professor.
2. DER: abrir o script docs/ddl_original.sql no MySQL Workbench, importar o modelo e gerar a imagem pelo próprio programa. A imagem assets/der.png e o Mermaid são referências geradas fora do Workbench; não são DER final conforme a exigência. Não há projeto .mwb fornecido nem instalação do Workbench identificada nesta máquina.

## Procedimento para o modelo no Workbench

No MySQL Workbench, usar File > Import > Reverse Engineer MySQL Create Script e selecionar docs/ddl_original.sql. Conferir o log de importação; se os CHECKs adicionados por ALTER TABLE não aparecerem no modelo importado, conferir o script e o modelo contra o catálogo. Não remover ou alterar regras para silenciar erro de importação.

Criar/abrir o diagrama EER do modelo e incluir TODAS as 19 tabelas. Organizar as posições e conferir os vínculos, com atenção às FKs compostas de pedido/endereco e item_pedido_lote/item_pedido/lote. Salvar o projeto .mwb. Exportar pela função File > Export > Export as PNG, com o diagrama EER ativo. Os nomes de menus podem variar conforme a versão; consultar a documentação oficial.

Conferir: usuario, cliente, endereco, fornecedor, categoria, produto, lote, preco_regiao, promocao, pedido, item_pedido, item_pedido_lote, nota_fiscal, conta_receber, pagamento, entrega, comprovante_entrega, estorno, log_auditoria.

O DDL é a referência física: 115 colunas, 21 FKs e 28 CHECKs. Nota fiscal, entrega e estorno admitem no máximo um registro por pedido. Comprovante referencia entrega.id_pedido. Item admite promoção opcional. Item_pedido_lote liga item e lote do mesmo produto por chaves compostas. Nenhuma FK obriga o pai a ter um filho.

## Como finalizar o site quando esses arquivos estiverem prontos

- Exportar os requisitos no layout oficial para docs/Especificacao_Requisitos_Regras_Negocio_BD.pdf.
- Exportar o DER do Workbench para assets/der.png e guardar o .mwb com o grupo.
- Conferir se os 115 atributos, tipos e constraints continuam iguais ao DDL; se houver mudança aprovada no DDL, atualizar também HTML, catálogo e documentos.
- Somente após a substituição real, atualizar no index.html os rótulos de proposta/referência e o aviso de pendência. Não retirar o aviso antes de concluir as etapas.
- Fazer commit dos arquivos na branch main e aguardar Pages concluir. Conferir busca, navegação, PDFs e imagem no endereço público.

## Revisão de conteúdo

O RELATORIO.md lista 27 apontamentos com localização nas páginas dos documentos. Pontos centrais: unificar RF01-RF09, resolver SEFAZ e DRE fora do escopo, corrigir preco_unitario para preco_unitario_venda, representar alocação por item_pedido_lote, incluir colunas e tabelas omitidas no DER, revisar estados e responsabilidades. Preservar as quatro entradas históricas originais e acrescentar a revisão real; não inventar assinaturas, autores ou aprovações.

FEFO, congelamento de preço, cálculo/consistência de totais, estorno, auditoria automática e RBAC exigem implementação no banco/aplicação. O DDL contém a estrutura e CHECKs locais; o site estático não implementa esses fluxos. A definição e implementação dessas rotinas precisam de validação do grupo.

## Como conferir o pacote

Abrir index.html no navegador ou acessar o site. Para a conferência automática: executar python verificar_catalogo.py dentro da pasta do projeto. O verificador usa apenas a biblioteca padrão do Python e compara DDL, HTML e JSON; não altera arquivos nem executa SQL. Também conferir a sintaxe com node --check script.js quando Node estiver disponível.

Este pacote corrige o código e a identificação dos artefatos; não declara que as pendências documentais da AT6 foram resolvidas.

## Referências oficiais dos menus

- Importação do script: https://dev.mysql.com/doc/workbench/en/wb-reverse-engineer-create-script.html
- Exportação do diagrama: https://dev.mysql.com/doc/workbench/en/wb-data-modeling-menus.html
