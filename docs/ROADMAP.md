---
status: legacy_do_not_use_as_truth
legacy_marked_at: 2026-05-12
supersedes: C:\dev\Investigacion_Osla_consolidada\OK\verticales\osla_perfil_empresa\product.md
reason: OSLA canonical documentation moved to consolidated OK tree after V3/saneamiento audit.
do_not_use_for: product_truth, roadmap_truth, implementation_scope, claims, data_rights
---

# ROADMAP — OslaFirma (Supplier Risk + Company Intelligence)

## Estado actual

MVP conceptual. Requiere pipeline de datos DGI + BPS + RUPE + GLEIF. Necesita ML para bankruptcy prediction y supplier risk scoring.

---

## Roadmap integrado

### Fase 1 — Data pipeline + Scoring (semanas 1-10)

**Entidades canónicas:**
- Empresa (RUT DGI)
- Proveedor (RUPE)
- Estructura accionaria (DGI)
- Relación comercial (CFE, BPS)
- Vinculación sancionada (OFAC, GLEIF)

**Milestones:**
- **M1:** Pipeline DGI (facturación, certificados, RUT, socios)
- **M2:** Pipeline BPS (cotizantes, aportes, estado laboral)
- **M3:** RUPE sync (115K+ proveedores, status, domicilio)
- **M4:** GLEIF integration (estructuras corporativas globales)
- **M5:** Bankruptcy prediction model (GBM, 6-12 meses)
- **M6:** Supplier risk scoring determinístico
- **M7:** Continuous monitoring alerts (cambios estructurales)
- **M8:** Product surface `/product/supplier/` (profile explorer)
- **M9:** Dashboard B2B compliance officers
- **M10:** Testing + documentation (60+ test cases)

**ML Pipeline:**
1. Feature engineering: liquidez (facturación/aportes), crecimiento, estructura accionaria, histórico defaults
2. Bankruptcy prediction (GBM): 85-92% accuracy 6-12 meses
3. Supplier risk scoring (LightGBM ensemble): 0-100 scoring
4. Monitoring alerts (threshold-based + temporal change detection)

**Validation criteria:**
- DGI sync latency <24h
- Bankruptcy recall >85% (evitar false negatives)
- Risk scoring correlation >0.75 con defaults reales
- Compliance officer adoption (SUS >70)

---

### Fase 2 — Network Risk + Enhancement (semanas 10-20)

**Milestones:**
- **M11:** Network risk propagation (si proveedor A cae, qué clientes se afectan)
- **M12:** Change detection refinement (socios, facultades, domicilio)
- **M13:** OFAC/Sanctions checking (automated)
- **M14:** API product (/api/v1/company/*)

**ML enhancements:**
- Temporal GNN para network propagation
- NLP para cambios en actas constitutivas
- Enhanced feature store (Feast)

**Validation criteria:**
- Network risk RMSE <0.3 (6 meses)
- OFAC matching precision >98%
- API latency <500ms

---

### Fase 3 — Enterprise + Benchmarking (semanas 20-30)

**Milestones:**
- **M15:** Multi-workspace + RBAC
- **M16:** Advanced auth (OAuth2 + SSO para bancos)
- **M17:** Bulk import (nóminas, listas proveedores)
- **M18:** Benchmarking contra LATAM (Chile, Argentina)
- **M19:** Integración con sistemas bancarios (API contracts)

**Validation criteria:**
- Auth latency <100ms
- Bulk import processing <1min/1000 registros
- 99.9% uptime SLA

---

### Fase 4 — Escala regional (meses 6+)

**Milestones:**
- **M20:** Paraguay integration
- **M21:** Mercado Común del Sur (MERCOSUR) data
- **M22:** Mobile app (compliance on-the-go)

---

## Stack especificación

**Backend:**
```
FastAPI + Pydantic
Postgres 16 + caching (Redis)
Airflow para ETL diario
```

**Frontend:**
```
Next.js 15
Tailwind CSS
Nivo/Recharts para grafos y scoring
```

**ML:**
```
scikit-learn + LightGBM
PyTorch (GNN futuros)
statsmodels (temporal analysis)
MLflow
```

**Data sources:**
```
DGI API / bulk exports
BPS API / monthly exports
RUPE API
GLEIF JSON
OFAC list (público)
```

---

## Métricas de éxito

| Métrica | Actual | Target M10 | Target M20 |
|---------|--------|------------|------------|
| Empresas perfiladas | 0 | 50K | 500K |
| Relaciones mapeadas | 0 | 200K | 2M+ |
| Bankruptcy accuracy | N/A | 87% | 92% |
| Risk score correlation | N/A | 0.75 | 0.85 |
| Dashboard MAU | 0 | 30 | 300 |
| MRR | $0 | $500 | $8K |

---

## Riesgos y mitigaciones

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|-------------|--------|-----------|
| DGI datos incompletos/retrasados | Media | Medio | Validación + fallback RUPE |
| BPS aportes con gaps | Media | Medio | Interpolación + warnings |
| Regulación de datos privados (UY) | Media-Alta | Alto | Legal review, anonimización |
| Competencia bancaria interna | Media | Medio | Diferenciar con NLP + network insights |

---

## Presupuesto estimado (MVP)

| Línea | Costo | Duración |
|-------|-------|----------|
| Ingeniería (3 FTE) | $45K | 6 meses |
| Cloud infra | $2.5K/mes | ongoing |
| Datos (APIs, GLEIF) | $1K/mes | ongoing |
| Legal review | $5K | 1 mes |
| Testing + QA | $5K | 2 meses |
| **Total MVP** | **~$100K** | **6 meses** |

---

## Hitos clave

- **Week 4:** M1-M2, DGI+BPS fluyendo
- **Week 8:** M4-M5, bankruptcy model entrenado
- **Week 12:** M6-M8, scoring + product launch
- **Week 16:** M9-M10, dashboard piloto
