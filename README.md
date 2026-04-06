# Dashboard de Terras Raras — TCU/DAmin

**Auditoria de Governança Mineral e Risco de Rejeitos (IRATR)**

Dashboard dark-themed em HTML/JS single-file para análise de terras raras no Brasil, com foco em detecção de risco de aproveitamento inadequado de rejeitos e exportação ilegal.

---

## 📋 Módulos

### 1. **Visão Geral**
- Estatísticas nacionais de processos ANM por fase (RP, APM, CL, DISP)
- Mapa de distribuição geográfica
- KPIs consolidados: total, ativos, disponíveis

### 2. **Pesquisa Mineral (RP)**
- Listagem completa de ~80 requerimentos de pesquisa por UF
- Filtros: UF, Substância, Fase
- Vencimentos e prazos
- Integração com SIGMINE

### 3. **Cotejo SGB-ANM**
- Incompatibilidades entre processos ANM e conhecimento geológico SGB
- ~40 anomalias nacionais com dados de aerogeofísica (Th/U ppm)
- Domínios geológicos: carbonatito, laterita, placer, granito A-type, etc.

### 4. **Produção e Preços**
- Índice TCU-TR Composite: Nd(30%) + Dy(25%) + Tb(20%) + Pr(15%) + La(5%) + Ce(5%), base=100
- Auto-fetch prices via metals.live API (cache localStorage)
- Histórico com timestamps

### 5. **Investimento Estrangeiro**
- Levantamento de empresas estrangeiras com participação em APMs
- Por UF e substância

### 6. **Fronteiras Minerais**
- 35+ fronteiras estratégicas de terras raras no Brasil
- Status: pesquisa, bloqueio, potencial
- Prioridade: alto/médio/baixo

### 7. **Mineralogia**
- Tabela TR associados por domínio geológico SGB
- Heatmap: Substância × Domínio → potencial TR

### 8. **Risco Radioativo (IRRM)**
- Índice de Risco Radioativo Mineral (0–100)
- Metodologia: Radiometria(40) + Processos ANM(20) + Operação CNEN(20) + Contexto Geo(15) + Exposição(5)
- ~40 municípios de maior risco, dados CPRM aerogeofísica

### 9. **Noticias TR**
- RSS feeds multi-fonte (EN + PT)
- 4-proxy CORS cascade (rss2json → allorigins → corsproxy → thingproxy)
- 15 notícias fallback offline
- Atualização periódica com timestamp

### 10. **Risco Especulativo (IRES)**
- Índice de Risco Especulativo Empresarial (0–100)
- Metodologia: Concentração Área(25) + Inércia Processo(25) + Part. Estrangeira(20) + CFEM/APM inadimplência(20) + Desvio PAE(10)
- ~30 empresas analisadas

### 11. **Incompatibilidades RP/APM-SGB**
- 23+ casos de conflito entre declaração ANM e evidência SGB
- Exemplo: Araxá (Nb declarado, TR+U nos rejeitos não contabilizado)
- Referências técnicas SGB/CNEN

### 12. **Rejeitos TR / Exportação Ilegal (IRATR)**
- **Índice de Risco de Aproveitamento de TR como Rejeito (0–100)**
- Metodologia: Assoc. TR(40) + Risco Barragem(30) + Risco Exportação(30)
- **IRATR_MATRIX**: 20 substâncias × SGB domínio geológico
- Upload Excel/CSV (SIGMINE format)
- 5 gráficos: donut risco, bar substância, bar UF, stacked decomposição, bubble análise
- Tabela com filtros: nível, tipo risco, UF, busca livre
- Matriz de referência SGB
- Alertas prioritários Top-8
- Exportação CSV

---

## 🎨 Estilo Visual

- **Tema**: Dark mode (`#0d1117` bg, `#161b22` panels, `#30363d` borders)
- **Cores por módulo**:
  - Preços: `#00ffcc` (cyan)
  - Noticias: `#8b5cf6` (purple)
  - Risco Especulativo: `#f59e0b` (amber)
  - Incompatibilidades: `#e879f9` (pink)
  - Rejeitos: `#fb923c` (orange)
  - Risco Radioativo: `#ef4444` (red)
  - Fronteiras: `#f85149` (red)
- **CSS variables**: Customizáveis via `--bg`, `--panel`, `--border`, `--text`, `--muted`, etc.

---

## 📊 Dados e Referências

### Processos ANM (~80 registros)
- Cobertura: Todos os UFs (BA, MG, GO, PA, AM, CE, RN, PB, PE, RO, MA, PI, SP, PR, MS, RS, RR, TO, DISP)
- Fases: RP, APM, CL, DISP
- Campos: processo, substância, UF, município, fase, titular, CNPJ

### Aerogeofísica SGB (Th/U ppm)
- ~40 municípios com dados CPRM
- Domínios geológicos identificados
- Base: Atlas Geofísico SGB, Boletim 47/2021 (TR em Carbonatitos)

### IRATR_MATRIX (20 substâncias)
Cada entrada contém:
- Substância + aliases (variações de nome)
- Domínio geológico SGB
- TR associados
- Ocorrências Brasil
- Scores: associação (40), barragem (30), exportação (30)
- Referência SGB

Substâncias catalogadas:
- Terras Raras (direto), Urânio/Tório, Nióbio, Columbita/Tantalita, Fosfato, Cassiterita, Titânio/Ilmenita, Ouro, Zircônio, Wolframita, Cobre (IOCG), Vermiculita, Ferro, Bauxita, Berilo, Grafita, Manganês, Calcário, Pb/Zn, Diamante

---

## 🚀 Como Usar

### Abrir no Browser
```bash
open dashboard-terras-raras.html
# ou simplesmente arrastar para o navegador
```

### Carregar Dados Demo
1. Clique na aba **Rejeitos TR / Exportação**
2. Clique em **▶ Dados Demo**
3. Dashboard carregará 25 registros SIGMINE de exemplo

### Carregar Seus Dados Excel/CSV
1. Abra `TCU_SIGMINE_Demo_TR.xlsx` como template
2. Substitua linhas com seus dados
3. Salve como Excel ou CSV
4. Na aba **Rejeitos TR**, clique **📂 Carregar Excel/CSV**
5. Selecione o arquivo
6. Dashboard processará automaticamente:
   - Normalização de colunas (detecção automática)
   - Cálculo IRATR por registro
   - Renderização de gráficos e tabelas

### Exportar Resultados
- Clique **↓ Exportar Resultados** para CSV com scores IRATR

---

## 📦 Dependências (CDN)

O arquivo é **single-file** e carrega tudo via CDN:

```html
<!-- Chart.js 4.4.1 para gráficos -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.min.js"></script>

<!-- SheetJS 0.18.5 para Excel/CSV parsing -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
```

**Sem Node.js, npm ou build tools necessários.**

---

## 🔧 Estrutura Técnica

### Arquivo Principal
- `dashboard-terras-raras.html` (~389 KB, 4880 linhas)
  - HTML (layout, grid, modais)
  - CSS (dark theme, variáveis, responsivo)
  - JS (260 KB de lógica)

### Padrões JS

#### Lazy Initialization (switchView)
```javascript
if (v === 'rejeitos') {
  if (!window._rejeitosInited) {
    initRejeitosView();
    window._rejeitosInited = true;
  }
}
```

#### Estado Global
```javascript
let rejeitosData = [];      // Array de registros processados
let _rejCharts = {};        // Cache de instâncias Chart.js
let newsLastUpdate = null;  // Timestamp da última atualização
```

#### Validação de Sintaxe JS
O código foi validado com Node.js:
```bash
node -e "new Function(jsBlock)"  # Zero syntax errors
```

---

## 📥 Demo Excel

`TCU_SIGMINE_Demo_TR.xlsx` contém:

### Aba 1: SIGMINE_TR_Export
25 registros com:
- NUP / Processo (ex: `800007/2018`)
- Substância Declarada (ex: `Nióbio`, `Fosfato`)
- UF, Município, Titular
- Fase, Área (ha), CNPJ
- Observações técnicas (referências SGB/CNEN)

Cobertura geográfica: MG, GO, AM, PA, RO, BA, ES, SP, SC, RN, MT

### Aba 2: Instruções
- Como carregar no dashboard
- Metodologia IRATR
- Referências SGB

---

## 🔒 Offline Mode

- **Noticias**: Fallback para 15 notícias curadas offline se proxies falharem
- **Preços**: Último valor em cache localStorage (TTL 24h)
- **Processos/Anomalias/Fronteiras**: Dados hardcoded, sempre disponíveis

---

## 📋 Formato SIGMINE Esperado

Ao fazer upload de Excel/CSV, o dashboard detecta automaticamente:
- `Processo`, `NUP`, `Proc`, `Numero` → processo
- `Substancia`, `Mineral`, `Commodity` → substância
- `UF`, `Estado` → UF
- `Municipio`, `Cidade`, `Local` → município
- `Titular`, `Empresa`, `Requerente` → titular
- `Fase`, `Status`, `Situacao` → fase
- `Area`, `ha`, `hectare` → área em hectares

**Colunas extras são ignoradas; colunas faltantes recebem valores padrão.**

---

## 🎯 Indicadores Principais

### IRATR (Rejeitos)
- **Alto** (≥ 65): Ação imediata recomendada
- **Médio** (35–64): Verificação técnica necessária
- **Baixo** (< 35): Monitoramento regular

### IRES (Especulativo)
- **Alto** (≥ 65): Empresa de risco geopolítico
- **Médio** (35–64): Atenção em mudanças de controle
- **Baixo** (< 35): Estável

### IRRM (Radioativo)
- **Alto** (≥ 65): Município de risco radiação
- **Médio** (35–64): Vigilância aerogeofísica contínua
- **Baixo** (< 35): Risco controlável

---

## 🛠️ Desenvolvido por

**TCU — Tribunal de Contas da União**
Departamento de Auditoria em Mineração (DAmin)
Porto Alegre, 2026

Auditor Federal: Raphael Marinho
Auditor Contador, especialista em Mineração & Finanças Públicas

---

## 📜 Licença

Uso público para auditoria governamental brasileira. Restrições de redistribuição comercial.

---

## 📞 Suporte Técnico

- **Dados SIGMINE**: Consultar ANM (https://www.gov.br/anm)
- **Aerogeofísica SGB**: GeoSGB (https://geosgb.cprm.gov.br)
- **CNEN / Radioatividade**: https://www.gov.br/cnen
- **Padrões INTOSAI**: NBC TA (Normas Brasileiras de Contabilidade)

---

**Versão**: 1.0
**Data**: Abril 2026
**Status**: Produção
