# Dicionário de dados Dolly

Revisão do código 1.2 em 10/11/2026. Leia primeiro ENTREGA_GRUPO.md: requisitos no modelo oficial e DER exportado do Workbench continuam pendentes. Publicado no GitHub Pages: https://carlosjb7.github.io/dicionario-dados-dolly/ . Repositório: https://github.com/carlosjb7/dicionario-dados-dolly . Leia RELATORIO.md antes de aprovar. O documento PDF disponível no botão Proposta técnica NÃO atende ao layout original exigido na AT2. Ele é uma consolidação por errata: preserva o conteúdo textual original e indica a correção que prevalece. Regras ausentes no DDL não foram implementadas. Papéis e RBAC são propostas.

## Estrutura exata para uso

```text
/meu-dicionario
├── index.html
├── style.css
├── script.js
├── README.md
├── RELATORIO.md
├── docs/
│   ├── Especificacao_Requisitos_Regras_Negocio_BD.pdf
│   ├── Relatorio_Auditoria.pdf
│   ├── ddl_original.sql
│   └── catalogo.json
└── assets/
    ├── der.png
    ├── der.mmd
    └── der_original.png
```

Extraia o ZIP e abra index.html no navegador. Não exige instalação, build, internet ou CDN. Pesquisa, tema e zoom usam JavaScript nativo. Há 19 seções e 115 linhas de atributos presentes no próprio HTML; a página não depende de fetch. O JSON é uma exportação de auditoria, não uma dependência de execução.

O HTML já contém `<link rel="stylesheet" href="style.css">` e `<script src="script.js" defer></script>`. Os caminhos são relativos à pasta de index.html, assim como `docs/Especificacao_Requisitos_Regras_Negocio_BD.pdf` e `assets/der.png`. Mantenha os nomes e a posição das pastas. Não use caminhos começando por barra, para que o site funcione no subdiretório de um repositório GitHub Pages.

## Conferência de aceite

1. Abra index.html; confira 19 tabelas e 115 atributos. A navegação é construída a partir das seções existentes.
2. Pesquise item_pedido_lote: aparecem os seis atributos da entidade. Pesquise quantidade_estornada: aparece apenas o atributo correspondente. Pesquise um termo inexistente: a mensagem sem resultados deve aparecer. Limpe a busca para recuperar tudo.
3. Alterne o tema. A escolha é persistida quando o navegador permite localStorage; sem armazenamento, o tema ainda funciona na sessão.
4. Abra Explorar modelo de referência. Use scroll, arraste, Zoom +, Zoom - e Reset. O desenho usa conectores R01-R21 e uma lista de arestas sem cruzamentos. Leia a cardinalidade na lista: pai indica quantos pais o filho admite; filhos indica quantos filhos um pai admite. Há alternativa Mermaid editável. Esc fecha o modal e retorna o foco.
5. Em celular, abra Navegar pelas tabelas. As tabelas permitem rolagem horizontal. O diagrama suporta arraste com toque e zoom por botões.
6. Baixe os dois PDFs e o PNG. Confira todos antes da aprovação.

## Publicar no GitHub Pages

1. Primeiro aplique/valide as correções de requisitos e DER e aprove a versão. A implementação de automações e RBAC deve ser tratada no projeto do banco/aplicação. Um catálogo estático não executa controles de acesso ao banco.
2. Acesse GitHub, entre na sua conta e use New repository. Escolha um nome, visibilidade Public e crie o repositório.
3. Use Add file > Upload files. Abra a pasta meu-dicionario no computador e arraste seu conteúdo, mantendo docs/ e assets/. Não envie apenas o ZIP nem crie uma pasta extra envolvendo index.html.
4. Faça Commit changes na branch main. Confirme que index.html está na raiz do repositório.
5. Vá a Settings > Pages > Build and deployment > Source: Deploy from a branch > selecione main > selecione / (root) > Save.
6. Aguarde a conclusão do fluxo pages build and deployment na aba Actions. Em Settings > Pages, abra o endereço apresentado pelo GitHub.
7. Verifique pesquisa, navegação, PDF, modal e PNG no endereço publicado.

GitHub Pages diferencia maiúsculas e minúsculas: assets/der.png é diferente de Assets/DER.PNG. O nome Especificacao_Requisitos_Regras_Negocio_BD.pdf deve coincidir exatamente com o link. Caso altere nomes, atualize o HTML e verifique os caminhos novamente.

Somente metadados foram incluídos; RGMs e assinaturas de aprovação foram omitidos da página. O repositório público expõe todo arquivo enviado, inclusive PDFs. Revise a autorização de divulgação da equipe antes de publicar. Não adicione dados reais do banco, credenciais nem cópias de canhotos.

Referência oficial do procedimento: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## Arquivos completos de código

index.html, style.css e script.js estão completos e separados. CODIGO_COMPLETO.md, na raiz do repositório, contém os três blocos integrais em Markdown para copiar. Não há trechos omitidos.

## Verificação realizada

Comparação automatizada do inventário DDL com o HTML e JSON, nomes e tipos das FKs, presença de CHECKs, sintaxe JavaScript e caminhos locais. PDFs renderizados para inspeção visual. Testes no endereço público concluídos: pesquisa por atributo e sem resultados, restauração dos 115 atributos, troca de tema, abertura do DER, carregamento do PNG, zoom por botões e scroll, arraste e reset, fechamento do modal, downloads dos dois PDFs e menu móvel em 390 x 844. Sem rolagem horizontal da página nessa largura; tabelas têm rolagem interna. Nenhum banco MySQL foi executado nesta revisão.


## Conferência de coerência

Execute `python verificar_catalogo.py` na pasta do projeto. A verificação compara todas as colunas, tipos, nulabilidade e definições do DDL com JSON e HTML. O script não executa o banco. Veja ENTREGA_GRUPO.md para concluir a documentação no formato exigido pelo professor.
