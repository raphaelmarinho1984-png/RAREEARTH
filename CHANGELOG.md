# CHANGELOG — Dashboard de Terras Raras

## [1.0] — 2026-04-06

### ✨ Funcionalidades

#### Módulos Implementados (12)
- **Visão Geral**: Estatísticas nacionais, distribuição geográfica, KPIs
- **Pesquisa Mineral (RP)**: ~80 registros, filtros UF/Substância/Fase
- **Cotejo SGB-ANM**: ~40 anomalias nacionais com aerogeofísica (Th/U ppm)
- **Produção/Preços**: Índice TCU-TR Composite, auto-fetch metals.live
- **Investimento Estrangeiro**: Participação estrangeira em APMs
- **Fronteiras Minerais**: 35+ fronteiras estratégicas de TR Brasil
- **Mineralogia**: Tabela e heatmap TR × domínio geológico
- **Risco Radioativo (IRRM)**: ~40 municípios, índice 0–100
- **Notícias TR**: RSS multi-fonte (EN+PT), 4-proxy CORS cascade
- **Risco Especulativo (IRES)**: ~30 empresas, índice 0–100
- **Incompatibilidades RP/APM-SGB**: 23+ casos, referências técnicas
- **Rejeitos TR / Exportação Ilegal (IRATR)**: Upload Excel/CSV, 5 gráficos, matriz SGB, alertas

#### Recursos Técnicos
- Single-file HTML (389 KB, 4880 linhas)
- Dark theme CSS customizável via variáveis
- Chart.js 4.4.1 (5 tipos de gráfico)
- SheetJS 0.18.5 (parse Excel/CSV)
- Lazy initialization com `switchView()`
- localStorage cache (preços, noticias TTL)
- CORS proxy cascade para RSS feeds
- Validação JS (zero syntax errors)

#### IRATR_MATRIX
- 20 substâncias catalogadas
- Aliases para robustez em busca
- Scores: Associação TR (40), Barragem (30), Exportação (30)
- Referências SGB/CPRM/CNEN
- Níveis: Alto ≥65, Médio 35–64, Baixo <35

#### Demo Data
- 25 registros SIGMINE em Excel
- Cobre todas as UFs relevantes (MG, GO, PA, AM, BA, ES, SP, etc.)
- Inclui Araxá, Catalão, Seis Lagos, Pitinga, Itaituba, etc.

### 🐛 Correções/Otimizações (desta sessão)
- JS syntax validation com Node.js
- Mineral filter agora funciona em renderProcessTable()
- PROCESSOS expandido: 12 → ~80 registros nacionais
- ANOMALIAS expandido: 9 (NE) → ~40 nacional com campos mun/domGeo/sgb
- FRONTEIRAS expandido: 18 → 35 entradas
- RISCO_DADOS expandido: 20 → 40 municípios
- INCOMPAT_DATA expandido: 12 → 23 casos
- News proxy cascade + 15-item fallback
- AbortController timeout pattern (AbortSignal.timeout() não suportado)
- CSS vars em JS substituídos por hex values

### 📦 Arquivos Entregáveis
- `dashboard-terras-raras.html` — Dashboard principal
- `TCU_SIGMINE_Demo_TR.xlsx` — 25 registros demo + instruções
- `README.md` — Documentação completa
- `.gitignore` — Config GitHub
- `LICENSE` — Licença de uso (TCU)
- `CHANGELOG.md` — Este arquivo

### 🎯 Próximas Versões (sugestões)
- [ ] Integração direta SIGMINE API (autenticação TCU)
- [ ] Integração GeoSGB para download dinâmico aerogeofísica
- [ ] Relatórios PDF automáticos (auditoria)
- [ ] API REST backend (Node.js/Express)
- [ ] Autenticação LDAP/AD (TCU)
- [ ] Histórico de auditorias e achados
- [ ] Mapa interativo (Leaflet.js)
- [ ] Alertas em tempo real (WebSocket)
- [ ] Integração CNEN radioatividade (API)

---

**Versão**: 1.0
**Data Release**: 2026-04-06
**Status**: Production-Ready
**Autor**: Raphael Marinho (TCU/DAmin)
