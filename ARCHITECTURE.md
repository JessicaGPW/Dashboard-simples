# Arquitetura do Dashboard de Receita

## 1. Escopo atual

O projeto é uma aplicação estática de uma página. O navegador renderiza a interface e executa o JavaScript. Não existe servidor de aplicação, banco de dados, autenticação ou integração com dados corporativos.

O servidor Python é usado apenas para entregar arquivos estáticos em ambiente local. Os comandos npm iniciam esse servidor; não há dependências de aplicação instaladas pelo npm.

## 2. Componentes

| Componente | Responsabilidade atual |
|---|---|
| index.html | Estrutura da página, controles, conteúdo, SVG do gráfico e JavaScript embutido |
| Tailwind CSS via CDN | Classes utilitárias aplicadas aos elementos |
| Objeto datasets no JavaScript | Valores fictícios para períodos de 7, 30 e 90 dias |
| Função updateChart | Formata a receita em BRL e atualiza a linha, a área, o ponto e os rótulos do SVG |
| Controles HTML | Seletor de período e botões de detalhes e relatório |
| Python http.server | Serve arquivos locais pela porta 8000 |
| package.json | Atalhos npm para iniciar o servidor Python |

## 3. Fluxo de interação

    Pessoa usuária
        ├── escolhe um período
        │       ↓
        │   evento change
        │       ↓
        │   datasets → updateChart()
        │       ↓
        │   receita, rótulos e SVG atualizados
        ├── seleciona View details
        │       ↓
        │   classe hidden alternada no painel de métricas
        └── seleciona Explore report
                ↓
            alerta demonstrativo

## 4. Dados

Os dados ficam em memória no próprio JavaScript. Cada período contém uma receita, pontos para a linha do gráfico e rótulos. A formatação da receita usa a localidade pt-BR e a moeda BRL.

Os valores são ilustrativos e não devem ser apresentados como resultados reais de uma empresa. Não há persistência entre sessões.

## 5. Limites e segurança

- Não há API nem validação de dados vindos de um serviço externo.
- Não há autenticação, autorização ou separação por perfil.
- O botão de relatório ainda não navega para um relatório real.
- Tailwind é carregado de uma CDN, então a página precisa de acesso à internet para receber esses estilos.
- O servidor Python simples é adequado para demonstração local, não para publicar uma aplicação de produção.
- Não inserir credenciais, dados pessoais ou informações comerciais reais no repositório.

## 6. Evolução recomendada

Se o protótipo crescer, uma organização possível seria:

    Dashboard/
    ├── index.html
    ├── src/
    │   ├── js/
    │   │   ├── dashboard.js
    │   │   └── data-service.js
    │   └── css/
    │       └── styles.css
    ├── docs/
    ├── package.json
    └── README.md

Nessa etapa, a interface poderia ser separada da lógica de dados. Um serviço consumiria uma API autenticada; a camada visual trataria estados de carregamento, erro e ausência de resultados. A escolha de framework ou ferramenta de build deve acompanhar a necessidade real do projeto.

## 7. Cenário empresarial

Para uma loja virtual, uma versão conectada poderia consolidar faturamento, pedidos, valor médio e conversão em um único painel. A gestão escolheria um intervalo, compararia tendências e abriria um relatório detalhado. A fonte de verdade seria o sistema de vendas, e as regras de cálculo precisariam ser validadas pela equipe responsável.