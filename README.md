# Dashboard de Receita

Protótipo de um cartão de dashboard interativo para acompanhar indicadores de receita, comparar períodos e consultar métricas comerciais. Foi desenvolvido como demonstração de interface para portfólio; os números exibidos são fictícios.

## Visão geral

O painel apresenta receita total, variação percentual, uma tendência visual e detalhes de pedidos. A pessoa usuária pode alternar entre 7, 30 e 90 dias. A interface atualiza os valores e o gráfico no navegador, sem recarregar a página.

## Problema de negócio

Equipes de vendas, operações e gestão precisam consultar indicadores sem navegar por várias telas ou planilhas. Um cartão de dashboard como este oferece uma visão rápida de receita, ajuda a identificar tendências e apoia conversas sobre resultados.

Nesta demonstração, os dados são fixos. Em uma empresa, a interface poderia consumir uma API conectada ao sistema de vendas, ERP ou plataforma de comércio eletrônico. Essa integração ainda não está implementada.

## Funcionalidades

- Exibe receita total e variação percentual.
- Filtra a visualização por 7, 30 ou 90 dias.
- Atualiza rótulos e gráfico SVG conforme o período escolhido.
- Mostra ou oculta métricas de pedidos, valor médio e conversão.
- Apresenta um botão de chamada para ação com um ponto de integração demonstrativo.
- Usa um layout adaptável e estilos utilitários do Tailwind CSS.

## Linguagens e tecnologias

- **HTML5** organiza o conteúdo e os controles.
- **JavaScript puro (ECMAScript)** trata eventos, mantém os dados de demonstração em memória e atualiza a página.
- **Tailwind CSS** fornece classes de estilo por CDN.
- **SVG** desenha o gráfico de tendência sem biblioteca de gráficos.
- **Python 3** serve os arquivos localmente durante a visualização.
- **npm** oferece os comandos de inicialização; não há dependências npm de aplicação.

## Arquitetura

A aplicação é uma página estática executada no navegador. O seletor de período dispara um evento JavaScript; a função de atualização consulta os dados em memória e atualiza o valor monetário, os rótulos e os caminhos do SVG. O botão de detalhes alterna a visibilidade de um painel. O botão de relatório exibe uma mensagem demonstrativa.

Veja [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) para o fluxo de dados, os limites atuais e uma proposta de evolução.

## Executar localmente

Para iniciar pelo npm, tenha Node.js/npm e Python 3 instalados. O servidor é local e não requer instalação de dependências do projeto.

No PowerShell, a partir da pasta do projeto:

    npm start

Depois, abra http://127.0.0.1:8000 no navegador. Para encerrar o servidor, pressione Ctrl+C no terminal.

Também é possível iniciar o servidor diretamente:

    python -m http.server 8000 --bind 127.0.0.1

## Estrutura atual

    Dashboard/
    ├── index.html
    ├── package.json
    ├── package-lock.json
    ├── README.md
    ├── .gitignore
    └── docs/
        ├── ARCHITECTURE.md
        └── PUBLISH_GITHUB_POWERSHELL.md

A interface, os estilos aplicados por classes Tailwind e o JavaScript estão atualmente em index.html. Essa organização mantém o protótipo pequeno; a arquitetura sugerida para expansão está documentada separadamente.

## Aplicações em uma empresa

Uma versão integrada poderia:

1. Receber vendas e metas de uma API corporativa.
2. Filtrar indicadores por unidade, canal, produto ou período.
3. Mostrar estados de carregamento, ausência de dados e falhas de conexão.
4. Restringir os dados conforme o perfil de acesso.
5. Apoiar reuniões de acompanhamento com indicadores atualizados.

A interface, sozinha, não substitui um sistema financeiro ou de BI. Para uso operacional, seria necessário integrar fontes confiáveis, validar cálculos e aplicar controles de acesso e privacidade.

## Próximas evoluções

- Separar JavaScript e estilos em arquivos próprios.
- Substituir os dados de exemplo por uma API documentada.
- Incluir estados de carregamento, erro e ausência de dados.
- Adicionar testes para os cálculos e interações.
- Melhorar a navegação por teclado e a leitura por tecnologias assistivas.
- Substituir o CDN por uma configuração de build do Tailwind para publicação.
- Adicionar uma captura de tela real da aplicação ao README.

## Competências demonstradas

Estruturação sem framework, manipulação do DOM, eventos, formatação monetária em pt-BR, atualização de SVG, composição de interface com Tailwind e documentação de limites e próximos passos de um protótipo.