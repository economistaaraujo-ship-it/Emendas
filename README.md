# Sistema de Consulta de Transferências Especiais - SEFAZ-ES

Sistema web para consulta e acompanhamento de transferências especiais (emendas parlamentares) para o Estado do Espírito Santo.

## Sobre

O sistema consulta dados da API oficial do Transferegov.br e apresenta informações detalhadas sobre:
- Emendas parlamentares e seus valores
- Status de execução e liberação de recursos
- Executores finais das políticas públicas
- Informações bancárias para acompanhamento

## Sistema de Cache Resiliente

O sistema implementa múltiplas camadas de backup automático para garantir disponibilidade contínua:

### 1. Cache de Sessão (30 minutos)
- Armazenado no navegador durante a sessão
- Acesso mais rápido aos dados recentes
- Limpo ao fechar o navegador

### 2. Cache Persistente (7 dias)
- Armazenado localmente no navegador
- Mantém dados mesmo após fechar o navegador
- Fallback automático quando API não responde

### 3. Cache Comunitário (GitHub)
- Arquivo `cache_data.json` no repositório
- Serve como último backup quando todos os caches locais falharem
- **Pode ser atualizado manualmente quando necessário**

## Como Atualizar o Cache Comunitário

Se você conseguir acessar a API com sucesso e quiser atualizar o backup comunitário:

1. Abra o Console do Desenvolvedor do navegador (F12)
2. Execute o seguinte comando:
```javascript
// Após carregar dados com sucesso, execute:
console.log(JSON.stringify({
    planos: window.dataCache.planos,
    timestamp: new Date().getTime(),
    cnpj: "27080530000143",
    ano: "2025",
    version: "1.0"
}, null, 2));
```
3. Copie o resultado e atualize o arquivo `cache_data.json` no repositório
4. Faça commit e push das alterações

## Estrutura de Arquivos

```
Emendas/
├── index.html          # Aplicação principal
├── cache_data.json     # Cache comunitário (fallback final)
└── README.md          # Este arquivo
```

## Tecnologias

- React 18 (via CDN)
- SheetJS (exportação Excel)
- API Transferegov.br
- LocalStorage/SessionStorage para cache
- Sistema de proxy CORS automático

## Como Usar

1. Abra `index.html` em um navegador moderno
2. O sistema carregará automaticamente os dados do ano configurado
3. Use os botões para:
   - **Consultar**: Buscar dados atualizados da API
   - **Excel**: Exportar dados para planilha
   - **Cache ON/OFF**: Ativar/desativar uso de cache
   - **Limpar Cache**: Remover caches locais e forçar nova consulta

## Resiliência

O sistema tenta buscar dados na seguinte ordem:
1. Cache de sessão (se < 30min)
2. Cache persistente local (se < 7 dias)
3. API Transferegov.br (com múltiplos proxies)
4. Cache comunitário do GitHub

Isso garante que o sistema funcione mesmo com instabilidades temporárias da API.

## Desenvolvido por

Tesouro Estadual | SEFAZ-ES
