# Sistema de Consulta de Transferências Especiais - SEFAZ-ES

Sistema web para consulta e acompanhamento de transferências especiais (emendas parlamentares) através da API do Transferegov.br.

## 🚀 Funcionalidades

- ✅ Consulta de transferências especiais por CNPJ e ano
- 📊 Visualização detalhada de emendas parlamentares
- 💰 Separação por categoria (Custeio e Investimento)
- 📈 Estatísticas e totalizadores em tempo real
- 💾 Sistema de cache para melhor performance
- 📥 Exportação para Excel
- 🔗 Links diretos para detalhes no Transferegov
- 🎨 Interface moderna e responsiva com tema dark

## 🛠️ Tecnologias

- HTML5 + CSS3
- React 18 (via CDN)
- SheetJS (XLSX) para exportação
- API Transferegov.br
- Proxy CORS para acesso à API

## 📦 Estrutura

```
├── index.html          # Aplicação principal
├── .github/
│   └── workflows/
│       └── deploy.yml  # GitHub Actions para deploy
└── README.md          # Documentação
```

## 🚀 Deploy

O deploy é automático via GitHub Actions:

1. Push para a branch configurada
2. GitHub Actions constrói e publica no GitHub Pages
3. Site disponível em: `https://[usuario].github.io/[repositorio]`

## 💻 Uso Local

Basta abrir o arquivo `index.html` em um navegador moderno.

## 🔧 Configuração

O sistema está pré-configurado para:
- **CNPJ**: 27.080.530/0001-43 (SEFAZ-ES)
- **Ano padrão**: 2025
- **Proxy**: CorsProxy.io (com fallback para AllOrigins)

## 📝 Notas

- Dados atualizados D+1 pela API do Transferegov
- Cache de sessão válido por 30 minutos
- Suporte a múltiplos proxies CORS para maior confiabilidade

## 🏛️ Desenvolvido por

Tesouro Estadual | SEFAZ-ES

## 📄 Licença

Sistema de uso interno governamental.
