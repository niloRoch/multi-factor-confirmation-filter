# 📊 Multi-Factor Confirmation Filter

[![TradingView](https://img.shields.io/badge/TradingView-Pine%20Script%20v6-blue)](https://www.tradingview.com/)
[![License: MPL 2.0](https://img.shields.io/badge/License-MPL%202.0-brightgreen.svg)](https://opensource.org/licenses/MPL-2.0)
[![Version](https://img.shields.io/badge/version-1.0.0-orange)]()

> Sistema de confirmação multi-fatores para análise técnica com suporte a Gaussian Bands e detecção inteligente de sinais de trading.

## 🎯 Visão Geral

O **Multi-Factor Confirmation Filter** é um indicador completo para TradingView que combina múltiplos fatores técnicos para gerar sinais de alta confiabilidade. Utilizando um sistema de pontuação ponderado, o indicador avalia tendência, momentum, volume, volatilidade e estrutura de preço para identificar as melhores oportunidades de trading.

### ✨ Características Principais

- **Sistema de Score Inteligente**: Pontuação de 0-100% baseada em múltiplos fatores
- **Análise Multi-Dimensional**: Combina 12+ indicadores técnicos
- **Detecção de Divergências**: Identifica divergências bullish/bearish no RSI
- **Stops Dinâmicos**: Sugestões de stop-loss baseadas em ATR
- **Painel Informativo Completo**: Visualização clara de todos os fatores
- **Medidor de Força Visual**: Barras de progresso para compra e venda
- **Alertas Customizados**: Notificações para sinais fortes e moderados

## 📈 Componentes do Sistema

### 1. Análise de Tendência (20%)
- **EMA 200**: Média exponencial principal
- **SMA 200**: Média simples de referência
- **Distância da Tendência**: Percentual de afastamento das médias

### 2. Indicadores de Momentum (25-30%)

#### RSI (14) - 10-15%
- Zonas de força: forte (>60 ou <40), moderada (>50 ou <50)
- Níveis de sobrecompra/sobrevenda configuráveis
- Detecção de divergências com lookback ajustável

#### MACD - 10-15%
- Configuração: 12/26/9 (personalizável)
- Análise de histograma crescente/decrescente
- Confirmação de cruzamentos

### 3. Força da Tendência (20%)

#### ADX (14)
- Threshold padrão: 25 (tendência forte)
- Análise de +DI e -DI
- Detecção de ADX crescente (fortalecimento)

### 4. Análise de Volume (10%)
- Volume médio: 20 períodos
- Multiplicador de volume alto: 1.5x
- Confirmação de volume crescente

### 5. Alinhamento de EMAs (15%)
- **EMA 9/21/50**: Sistema de médias curtas
- Alinhamento bullish: 9 > 21 > 50
- Alinhamento bearish: 9 < 21 < 50
- Separação forte quando >2%

### 6. Volatilidade (ATR)
- **ATR (14)**: Average True Range
- Volatilidade percentual
- Stops sugeridos: ATR × 1.5 (configurável)

### 7. Estrutura de Preço (5%)
- Higher Highs / Lower Lows
- Confirmação de estrutura bullish/bearish

## 🎨 Visualização

### Painel Principal
Exibe em tempo real:
- ✅ Status de cada indicador (✓✓ Forte, ✓ Moderado, ○ Neutro)
- 📊 Valores atuais
- 🎨 Cores indicativas (verde/vermelho/cinza)
- 🎯 Score final e qualidade do sinal
- 🛡️ Stop sugerido

### Medidor de Força
- Barras de progresso visuais
- Escala 0-100%
- Verde (compra) / Vermelho (venda)

### Gráfico de Scores
- Linha verde: Score de compra
- Linha vermelha: Score de venda
- Zonas coloridas para sinais ativos
- Marcadores de divergências

## ⚙️ Configuração

### Parâmetros Principais

```pine
// Médias de Referência
EMA 200: 200 períodos
SMA 200: 200 períodos

// Momentum
RSI: 14 períodos
RSI Sobrecompra: 70
RSI Sobrevenda: 30
MACD: 12/26/9

// Tendência
ADX: 14 períodos
Threshold ADX: 25

// Volume
Média Volume: 20 períodos
Multiplicador: 1.5x

// Volatilidade
ATR: 14 períodos
Multiplicador Stop: 1.5x

// Filtros
Score Mínimo: 60%
```

### Personalizações Disponíveis

1. **Ajuste de Sensibilidade**: Altere o score mínimo (40-80%)
2. **Timeframe**: Funciona em qualquer temporalidade
3. **Divergências**: Ative/desative detecção
4. **Visualização**: Oculte scores ou medidor conforme preferência

## 📊 Sistema de Pontuação

### Score de Compra (100% total)
- 20% - Tendência acima EMA/SMA 200
- 15% - RSI em zona de força bullish
- 10% - MACD bullish
- 5% - MACD crescente
- 15% - ADX confirmando alta
- 5% - ADX crescente
- 8% - Volume acima da média
- 2% - Volume crescente
- 10% - EMAs alinhadas bullish
- 5% - Separação forte entre EMAs
- 10% - Divergência bullish
- 5% - Estrutura de preço bullish

### Score de Venda (100% total)
Mesma estrutura aplicada para sinais bearish.

### Qualidade dos Sinais
- **FORTE**: Score ≥ 80%
- **BOA**: Score 70-79%
- **MODERADA**: Score 60-69%

## 🔔 Alertas

Configure alertas para:
- 🔥 Sinais fortes (≥80%)
- ✓ Sinais moderados (60-79%)
- 📈 Divergências bullish
- 📉 Divergências bearish

### Exemplo de Mensagem
```
🔥 COMPRA FORTE - Score: 85% | Stop: 45.230
```

## 🚀 Como Usar

### 1. Instalação
1. Abra o TradingView
2. Clique em "Pine Editor"
3. Cole o código do indicador
4. Clique em "Adicionar ao Gráfico"

### 2. Interpretação dos Sinais

#### Sinal de Compra
- Score verde ≥ 60%
- Fundo verde no gráfico
- Painel mostra "🟢 COMPRA"
- Quanto maior o score, maior a confiança

#### Sinal de Venda
- Score vermelho ≥ 60%
- Fundo vermelho no gráfico
- Painel mostra "🔴 VENDA"
- Quanto maior o score, maior a confiança

#### Aguardar
- Scores abaixo de 60%
- Painel mostra "⚪ AGUARDAR"
- Evite operar em zonas neutras

### 3. Estratégia Sugerida

**Entrada:**
- Aguarde score ≥ 70% para maior confiabilidade
- Confirme com divergências se disponíveis
- Verifique alinhamento de timeframes maiores

**Stop Loss:**
- Use o stop sugerido pelo indicador (baseado em ATR)
- Ajuste conforme seu gerenciamento de risco

**Take Profit:**
- Use relação risco/retorno de no mínimo 1:2
- Considere resistências/suportes principais
- Parcialize lucros em níveis importantes

## 📖 Casos de Uso

### Day Trading
- Timeframes: 5m, 15m, 30m
- Score mínimo recomendado: 70%
- Foco em volume alto e volatilidade moderada

### Swing Trading
- Timeframes: 1H, 4H, 1D
- Score mínimo recomendado: 65%
- Foco em tendência e estrutura de preço

### Position Trading
- Timeframes: 1D, 1W
- Score mínimo recomendado: 60%
- Foco em alinhamento de médias longas


## 🛠️ Requisitos Técnicos

- **TradingView**: Conta Free ou superior
- **Pine Script**: Versão 6
- **Browser**: Atualizado (Chrome, Firefox, Safari, Edge)

## 📝 Licença

Este projeto está licenciado sob a [Mozilla Public License 2.0](https://www.mozilla.org/MPL/2.0/)

## 🤝 Contribuições

Contribuições são bem-vindas! Por favor:
1. Faça um Fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📧 Suporte

Para questões, sugestões ou reportar bugs:
- Abra uma [Issue](../../issues)
- Consulte a [Wiki](../../wiki) para documentação adicional


