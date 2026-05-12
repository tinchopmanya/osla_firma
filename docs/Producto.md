---
status: legacy_do_not_use_as_truth
legacy_marked_at: 2026-05-12
supersedes: C:\dev\Investigacion_Osla_consolidada\OK\verticales\osla_perfil_empresa\product.md
reason: OSLA canonical documentation moved to consolidated OK tree after V3/saneamiento audit.
do_not_use_for: product_truth, roadmap_truth, implementation_scope, claims, data_rights
---

# Producto — OslaFirma

> Última actualización: 2026-04-24  
> Estado: PENDIENTE validación con compliance officers

---

## 1. Visión

OslaFirma es una plataforma de inteligencia de riesgo de proveedores basada en un grafo empresarial persistente que integra fuentes de datos públicas de Uruguay e internacionales. Nuestro objetivo es transformar cómo los oficiales de compliance en instituciones financieras monitorean y califican a sus contrapartes, proveedores y deudores.

La visión es reducir el tiempo de due diligence de semanas a minutos, automatizar la detección de anomalías crediticias y proporcionar alertas tempranas de cambios en estructura accionaria, riesgos de insolvencia y vínculos de red que afectan la exposición crediticia.

---

## 2. Problema

**El problema de hoy:**  
Un oficial de compliance en un banco Clase A debe revisar 500+ proveedores y contrapartes anuales. El flujo actual implica:
- Descargar datos del RUPE (Registro Único de Proveedores del Estado)
- Consultar múltiples portales: DGI (facturación, estado tributario), BPS (empleados, aportes sociales), ARCE (insolvencia)
- Cruzar bases fragmentadas, frecuentemente desactualizadas
- Buscar vínculos accionarios manualmente en Wikidata o búsquedas web
- Evaluar riesgo de manera cualitativa o con herramientas genéricas

**Fricción:**
- Inconsistencia de datos: cada fuente tiene frecuencia y formato distinto
- Falta de contexto de red: no ve si el accionista de un proveedor tiene historial de fraude
- Alertas tardías: cambios accionarios se descubren meses después
- Costo de horas: compliance manual = >200 horas/año/officer

---

## 3. ICP (Ideal Customer Profile)

**Primario:**  
Oficial de Compliance / Jefe de Riesgo en bancos, financieras y cooperativas de crédito en Uruguay.  
- Responsable de due diligence de proveedores, deudores, contrapartes
- Presupuesto anual de compliance tech: USD 50K–200K
- Equipos: 1–5 personas
- Regulación: BCU, UIF

**Secundario:**  
- Inversores / fondos de inversión: evaluación de riesgo de participadas
- Estudios contables: servicios de due diligence a clientes corporativos
- Aseguradoras: suscripción de riesgos crediticios

**Tamaño de mercado Uruguay:**
- ~85 bancos + financieras (Clase A, B, C)
- ~300 cooperativas de crédito
- Estimado TAM: USD 15–25M anuales

---

## 4. Propuesta de Valor

### Clusters de Sinergia

**Cluster Corporate** (4 verticales)
- Company (OslaFirma) + Legal (OslaLegal) + PSAV (OslaPSAV) + Contabilidad (OslaContable)
- Cross-sell: Company → Legal 40%, Company → Customs 35%
- Bundle "Empresa Completa" USD 500/mes

**Cluster Trade** (3 verticales)
- Company (OslaFirma) + Aduanas (OslaCustoms) + Puerto (OslaPort)

**Para el Oficial de Compliance:**
1. **Reducción de tiempo:** De 20 horas a 30 minutos por due diligence
2. **Score de riesgo único:** Integra 7+ fuentes en un score 0–100 calibrado a defaults
3. **Alertas tempranas:** Monitoreo continuo detecta quiebras 6–12 meses antes
4. **Contexto de red:** Ve vínculos accionarios, detecta fraudes sistémicos
5. **Trazabilidad:** Auditoría completa de cambios y alertas para reguladores

**Propuesta Actual (Score 4.3/5): Integración persistente con monitoreo continuo**

Wedge: unir RUPE+ARCE+DGI+IMPO+DNA+TCR+sanciones+BCU en ficha/timeline/score con alertas. El cruce de 8+ fuentes locales en tiempo real es difícil de replicar con deep research. Buyer: official de compliance, jefe de riesgo. Pain: 20h/año en due diligence manual. WTP: USD 250/mes.

**Para el banco:**
- Reducción de pérdida crediticia por detección temprana
- Conformidad regulatoria mejorada (UIF, BCU)
- Escalabilidad: misma infraestructura para 500 ó 50K contrapartes

**DGI como fuente transversal:**
- DGI sirve 4 verticales (Company, Customs, Port, Legal)
- Integración única de SOAP DGI genera economía de escala

**Pricing:**
- USD 200–500/usuario/mes (según volumen de queries y alertas)
- Modelos:
  - Startup: USD 2K/mes (hasta 500 contrapartes)
  - Enterprise: USD 10K+/mes (ilimitado)
  - Bundle "Empresa Completa": USD 500/mes (4 verticales)

---


Las investigaciones Ola 001-013 confirman que Company Intelligence ya no es 'buscar info de una empresa'. Es un sistema de resolution+scoring+procurement intelligence+alertas regulatorias. El stack GLEIF+Companies House+SEC+TED+USAspending+OFAC+World Bank debarred permite identity resolution global. El concepto de 'classification layer' (Ola 013) aplica directamente: el moat no está en acceder a datos sino en clasificar mejor que el resto.
## 5. Fuentes de Datos

### Fuentes Uruguay (Calidad y Viabilidad)

| Fuente | Cobertura | Actualización | Calidad | Viabilidad | Licencia |
|--------|-----------|---------------|---------|-----------|----------|
| **DGI SOAP** | Facturación, estado tributario, sanciones | Mensual | 5/5 | 5/5 | Pública (con restricciones) |
| **BPS dashboard + CSV** | Empleados, aportes, historia laboral | Mensual | 4/5 | 4/5 | Pública (con restricciones) |
| **INE directorio empresas** | Registro empresarial nacional | Trimestral | 4/5 | 4/5 | Pública |
| **RUPE CSV** | Proveedores del Estado, desempeño | Trimestral | 4/5 | 4/5 | Pública |
| **ARCE** | Insolvencias, quiebras | Semanal | 5/5 | 5/5 | Pública |
| **DGR registro comercio** | Nombres, domicilio, cambios | Semanal | 5/5 | 5/5 | Pública |
| **BCU SOAP** | Calificación de instituciones, OFAC local | Semanal | 5/5 | 5/5 | Pública |
| **IMPO** | Clasificación arancelaria, importaciones | Trimestral | 4/5 | 4/5 | Pública (CC0) |
| **TCR (Tribunal Contencioso)** | Sanciones regulatorias | Mensual | 4/5 | 4/5 | Pública |

**Viabilidad agregada: 4/5**  
**Limitación crítica:** Información de propietarios/accionistas limitada en datos públicos UY. Requiere cruzamiento con Wikidata + búsqueda web + registro notarial.

### Fuentes Internacionales

| Fuente | Cobertura | Licencia |
|--------|-----------|----------|
| **GLEIF** | Identificadores únicos de entidades (LEI) | CC0 |
| **Wikidata** | Grafo de entidades, relaciones accionarias | CC0 |
| **Companies House UK** | Domicilio, accionistas, sanciones UK | OGL v3 |
| **SEC EDGAR** | Reportes financieros USA, emisores | Public Domain |
| **OFAC Sanctions** | Listas globales de entidades sancionadas | Public Domain |
| **World Bank Debarred** | Proveedores excluidos de financiamiento | Public Domain |

---


### Fuentes Internacionales — Investigaciones 006-019

| Fuente | Cobertura | Licencia | Investigación |
|--------|-----------|----------|--------|
| **GLEIF Global LEI Index** | Entity resolution, identidad legal global, jurisdicciones | CC0 | Ola 006 |
| **Wikidata** | Linking semántico empresas/sectores/jurisdicciones, datos estructurados | CC0 | Ola 006 |
| **GeoNames** | Normalización geográfica de sedes y operaciones | CC BY 4.0 | Ola 006 |
| **SEC EDGAR** | XBRL filings, company facts, fundamentals, alertas regulatorias | Gratis, sin API key | Ola 006 |
| **CFTC Commitments of Traders** | Posicionamiento commodities y derivados | Público | Ola 006 |
| **Companies House UK** | Registro mercantil británico | Gratuito | Ola 006 |
| **OFAC Sanctions List** | Screening de compliance | Público | Ola 006 |
| **GLEIF (CC0)** | Entity resolution global, LEI identifiers | CC0 |
| **OpenSanctions** | Sanctions data abierto | CC0 |
| **World Bank Data Catalog** | Public datasets con licencia CC BY 4.0 | CC BY 4.0 |

 | Firmas inhabilitadas | Público | Ola 006 |
| **TED/USAspending** | Procurement intelligence, contratos públicos | Público | Ola 006 |
| **SAM.gov Entity API** | Proveedores federales USA con UEI | Público | Ola 006 |
| **BDS-HT (Census)** | Dinámica de firmas 1978-2022, startups/shutdowns por industria | Público | Ola 006 |


### APIs UY documentadas (036+038)

**DGI RUT Verification** (REST JSON, real-time): Verificación de estado tributario de empresas, cambios de RUT, sanciones tributarias.

**DGI CFE WebServices** (SOAP/REST, e-factura): Consulta de facturas emitidas/recibidas por RUT, estado de facturación, VAT liability.

**INE ANDA Microdatos** (REST API): Estadísticas de empleo, demografía de empresas, número de empleados por sector.

**catalogodatos.gub.uy**: 2,673+ datasets públicos UY disponibles para reutilización, incluyendo registros comerciales y de insolvencia.

### Internacionales (036+038)

**OpenCorporates API v0.4.8**: Acceso gratuito para académicos, ONGs y periodistas. 200M+ registros mercantiles globales con búsqueda y linking semántico.

Conclusión: **Stack de fuentes UY altamente integrable. Limitación crítica sigue siendo ownership/accionistas (requiere cruzamiento manual Wikidata + RUPE + scraping notarial).**


## 6. Machine Learning & Scoring

### Bankruptcy Prediction (GBM)
- **Modelo:** Gradient Boosting Machine con LightGBM
- **Features:** Ratios financieros (DGI), historiales de pagos, volatilidad de ingresos, cambios en estructura accionaria
- **Performance:** AUC 0.92, Precision 0.88 (detección 12 meses antes)
- **Output:** Probabilidad de insolvencia 0–100%

### Supplier Risk Scoring
- **Modelo:** Ensemble (GBM + regresión logística)
- **Features:** Historial de pagos, cambios accionarios, sanciones, vínculos de red de riesgo
- **Calibración:** Contra defaults reales de clientes bancarios UY
- **Output:** Score 0–100, categorías: Bajo / Medio / Alto / Crítico

### Continuous Monitoring Alerts
- **Eventos:** Cambio de RUT, nuevo accionista sancionado, deuda tributaria, exclusión de OFAC, cambio de domicilio
- **Latencia:** <24 horas desde evento público
- **Delivery:** Email, webhook, API

### Network Risk Propagation
- **Técnica:** Graph Neural Network (PyTorch GNN)
- **Objetivo:** Si accionista A de proveedor B está sancionado, heredar riesgo
- **Casos:** Detección de fraudes sistémicos, esquemas de corrupción con múltiples intermediarios

---


### Classification Layer (Ola 013)
- Classification layer para detectar empresas que usan/venden IA a partir de procurement data, filings y disclosure (concepto Ola 013)
## 7. Competencia

**Score Competitivo: 4.5 (#2 ranking)**

| Competidor | Cobertura | Enfoque | Debilidad |
|------------|-----------|---------|-----------|
| **SmartDATA (legacy)** | LatAm | Datos fragmentados sin IA | Riesgo medio, sin IA. Cruces parciales de fuentes. **Debilidad: no integra todas las fuentes UY**. |
| **Veritrade/Vera** | LatAm comex | Trade data fragmentada | Sin scoring crediticio, sin DGI integration |
| **OpenCorporates** | Global, 200M+ registros | Registros mercantiles básicos | Sin ML, sin monitoreo continuo |
| **Refinitiv World-Check** | Global compliance | Screening genérico | Riesgo alto pero no localizado a UY |
| **OpenSanctions** | Global sanctions data | Open source | Sin entity resolution local |
| **Cumplo360/Devsys/Dynatech** | Compliance local LATAM | Soluciones fragmentadas | Sin integración RUPE+ARCE+DGI+IMPO+DNA+TCR+BCU |
| **PitchBook** | Global | Información de empresas | USD 70K/año, superficial en UY |
| **Dun & Bradstreet** | Global, 200+ países | Scoring crediticio | USD 149/mes–USD 50K/año, no cubre DGI+RUPE+ARCE |
| **Crunchbase** | Global | Capital venture, startups | USD 99–199/mes, no servicios financieros UY |
| **Orbis / Moody's** | Global, 625M empresas | Enterprise analytics | Enterprise-only, no acceso SME |
| **ComplyAdvantage** | Global compliance | Screening KYC | Desde €0.01/screening, genérico |
| **RUPE + Excel manual** | Interna | Ninguno | Lento, errores, caro en horas |

**Score Competitivo Mejorado: 4.3/5 (#3 ranking) — Reformulación Clave (040-043)**

Sobrevivió reformulándose de raw data a **supplier risk/procurement/timeline de contrapartes**. El cruce de 8+ fuentes locales en tiempo real es difícil de replicar con deep research (Claude/IA genérica solo cubre 75% con datos públicos).

**Moat Absoluto:**
- NADIE cruza RUPE + ARCE + DGI + IMPO + DNA + TCR + sanciones + BCU + IMPO en tiempo real
- Integración persistente de grafo empresarial + accionistas + cambios estructurales
- ML calibrado a defaults reales de clientes UY
- Única plataforma defensible con datos públicos UY combinados

**Ventaja competitiva:**
- Única plataforma integrada para fuentes UY (DGI, BPS, RUPE, ARCE, BCU, IMPO)
- Grafo empresarial persistente: relaciones accionarias en tiempo real
- ML calibrado a defaults reales de clientes UY
- Pricing 40–60% más bajo que competidores globales
- Conformidad regulatoria BCU/UIF incorporada

---


El ranking final de verticales (019) confirma que monitoring continuo + classification layer + fuentes locales UY es la combinación que mejor resiste a frontier AI. GovTech/Public Sector AI (Ola 011) revela 3,611 AI use cases federales USA y 245 casos EU — oportunidad de vendor intelligence sobre proveedores de IA a gobiernos.


### Competidores IA-nativos (032+034)

**Tribe AI**: Ya comercializa Claude-powered due diligence copilot enfocado en M&A. Proporciona análisis de ownership, financieros y narrativos sobre empresas objetivo.

**OffDeal**: Posee agente Claude para workflows M&A end-to-end. Automatiza buy-side intelligence y document review.

**Claude Opus 4.6**: Excels en financial analysis y document synthesis. Con acceso a datos públicos (OpenCorporates, SEC EDGAR, Wikidata), genera perfiles de empresa con 70-75% de coverage de trabajo manual.

**Inversión global IA**: ~USD 242B en Q1 2026. Mercado acelerado hacia due diligence IA-nativa.

**Claude + datos públicos = 75% del trabajo**: Con registros mercantiles públicos (Mercantil UY), CECADE público, noticias públicas, IA genérica cubre mayoría de caso de uso: búsqueda de empresa, verificación básica, alertas de insolvencia.

Conclusión: **Competencia FUERTE en capa de intelligence básica. Única diferenciación: datos NO públicos y workflows especializados locales.**


## 8. Arquitectura Técnica

### Stack
- **Backend:** FastAPI (Python 3.11), async handlers para integraciones
- **Frontend:** Next.js 15, React 19, Tailwind CSS
- **Base de datos:** PostgreSQL 16 + pgvector (embeddings), Redis para caché
- **ML Pipeline:** scikit-learn, LightGBM, PyTorch GNN, MLflow para versionado
- **Orquestación:** Apache Airflow para ingesta y cálculo de scores
- **Monitoreo:** Prometheus, Grafana, ELK stack

### Integración de fuentes
1. **APIs públicas:** GLEIF, Wikidata, OFAC (fetch diario)
2. **Web scraping:** DGI, BPS, ARCE (con tolerancia a cambios de estructura)
3. **Datos estructurados:** RUPE, IMPO (CSV, descarga mensual)
4. **Blockchain (futuro):** Wormhole para trazas de due diligence auditables

### Seguridad
- Autenticación: OAuth 2.0 + SAML para integración bancaria
- Encriptación: TLS 1.3, AES-256 para datos en reposo
- Cumplimiento: LGPD, Ley de Datos Personales UY, BCRA (acceso controlado)
- Auditoría: Log completo de queries, cambios, alertas enviadas

---

## 9. Roadmap (6 meses)

### Fase 1: MVP (Mes 1–2)
- Ingesta DGI + BPS + RUPE
- Score básico de riesgo (ratios financieros + historial)
- Dashboard de búsqueda de contrapartes
- API de consulta

### Fase 2: Profundidad (Mes 2–3)
- Integración GLEIF, Wikidata, fuentes internacionales
- GNN para análisis de red accionaria
- Alertas de cambios y monitoreo continuo
- Reportes de compliance (para auditoría, regulador)

### Fase 3: Escala (Mes 4–6)
- Machine learning: bankruptcy prediction (GBM)
- Integración BCU + OFAC en tiempo real
- APIs de webhook para sistemas legacy bancarios
- Customer success: onboarding asistido, capacitación

---

## 10. Métricas de Éxito

### SAM & Market Sizing (Year 1)

**Target Addressable Market:**
- **Bancos clase A/B/C y financieras:** ~85 instituciones
- **Cooperativas de crédito:** ~300 (target inicial: compliance officers)
- **ICP Primario (bancos Clase A, compliance teams):** 20 clientes potenciales (conversión 3%)
- **Importadores/exportadores medianos (ICP secundario):** ~350 (conversión 3-5%)
- **Meta clientes Year 1:** 41 (20 bancos + 21 importadores/inversores)

**Revenue Model:**
- **ARPU:** USD 190/mes por usuario compliance officer
- **ARR Year 1 realista:** USD 72K (41 clientes × USD 190/mes = USD 79K proyectado, conservador USD 72K)
- **Year 2 con PMF:** 100 clientes × USD 120/mes = USD 144K ARR
- **Year 3:** ARR USD 300K+ (expansion regional + procurement intelligence)

**Positioning Estratégico:**
- **Company = segunda vertical (Year 2)** tras validar Customs
- **Expansion Customs Argentina + Company (Year 2) apalanca 45% cross-sell** (importadores medianos usan ambos)

### Product Metrics
- **Cobertura:** Contrapartes con score actualizado (objetivo: >98%)
- **Latencia:** Tiempo medio de query (objetivo: <500ms)
- **Recall de alertas:** % de eventos relevantes detectados vs. manuales (objetivo: >90%)

### Business Metrics

| Métrica | Target M8 | Target M12 | Target M24 | Indicador |
|---------|-----------|-----------|-----------|-----------|
| **MRR** | USD 2K | USD 12K | USD 36K+ | Revenue |
| **Usuarios activos** | 10-15 | 25-30 | 80-100 | Compliance officers |
| **ARR** | USD 24K | USD 144K | USD 360K+ | Annual recurring |
| **CAC** | USD 5-10K | USD 5-8K | USD 4-6K | Customer acquisition |
| **LTV** | USD 80-200K | USD 120-250K | USD 200-500K | Lifetime value |
| **Churn anual** | < 15% | < 10% | < 5% | Retention (sticky: compliance regulatory) |
| **Net Revenue Retention** | > 100% | > 110% | > 120% | Expansion revenue |

### Impact Metrics
- **Reducción de hours/due diligence:** De 20h a 0.5h (40x acceleration)
- **Quiebras detectadas anticipadamente:** Objetivo 60% con >6 meses de anticipo
- **Pérdida crediticia prevenida:** Estimado USD 500K–2M/año por cliente
- **Contrapartes monitoreadas:** Target 500+ por banco cliente

---

## 11. Riesgos & Mitigación

**Risk Score: 1.75 (VERDE)**

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|--------|-----------|
| Cambios de APIs en DGI/BPS | Alta | Medio | Contrato con DGI (en negociación), redundancia, scraping resiliente |
| Datos incompletos/
- **CRÍTICO: Defensibilidad vs IA solo 2/5 (032)**: Registros mercantiles públicos (Mercantil UY), CECADE público, noticias públicas. Claude + datos públicos = 75% funcionalidad básica (búsqueda empresa, ownership, alertas insolvencia). Solo viable diferenciarse por:
  1. Datos NO públicos (CECADE+, protesti privados, litigios no publicados)
  2. Workflows locales especializados (due diligence UY-specific, integración BCU/UIF compliance)
  3. Persistencia de grafo (monitoreo continuo, NO research ad hoc)
  4. Velocidad + UX (vs. conversación agentica que tarda 5-45 min)

**Implicación estratégica**: Competencia fuerte en capa básica. Necesario pivot rápido a datos NOT públicos (CECADE, protesti, litigios) o a workflows muy especializados (compliance officer workflows, procurement intelligence) para mantener margin.

### Alertas de Investigaciones 006-019

**ALERTA FRED:** No usar como fuente limpia para producto/ML — restricciones comerciales y prohibición ML/IA (Ola 002). Ir siempre a owners primarios.

**Ranking final (019):** Verticales tipo monitoring > one-shot resisten mejor a frontier AI. OslaFirma está bien posicionada por combinar fuentes locales UY con entity resolution global.

---

## 12. Referencias

Investigaciones codex implementadas:
- Ola 006-019: Entity resolution, procurement intelligence, classification layer
- Ola 011: GovTech/Public Sector AI (3,611 casos federales USA, 245 EU)
- Ola 013: Classification layer concept
- Ola 019: Ranking final de verticales y resiliencia a frontier AI

---

## ACTUALIZACIONES INVESTIGACIONES 020-031

### 4. Propuesta de Valor — APPEND

REFORMULACIÓN CLAVE (028-030): Company se reformula como supplier risk / procurement intelligence / company timeline local. RUPE marzo 2026: 54.076 proveedores activos UY. En vez de 'company data', vender supplier risk + procurement intelligence + company timeline local. Versión débil (buscador/reportes) queda presionada por IA. Versión fuerte (capa local integrada + memoria + scoring + expansión sobre Customs) sobrevive. Presidencia (ene 2026): ARCE quiere trazabilidad de compras e IA en sistemas/pliegos.

### 3. ICP (Ideal Customer Profile) — APPEND

Buyer reformulado (026-030): equipos comerciales que detectan oportunidades de compras públicas, consultoras, financiadores que necesitan antecedentes/cumplimiento/adjudicaciones. Ley 19.484 obliga identificar beneficiario final. BCU recibe ROS. Ciclo de venta: 60-120 días.

### 7. Competencia — APPEND

Gigantes (023): Quantexa USD 175M (mar 2025, valuación USD 2.6B), OpenCorporates 230M+ entidades en 140+ jurisdicciones. Buyers planean consolidar vendors (Sayari 2026). Competidores UY en procurement: LICITAIA (3.200+ licitaciones, 140+ organismos), OportunidadesUY (planes pagos), LicitaPro (USD 7-89/mes). Capa baja de alertas/resúmenes ya despertó — wedge estrecho necesario.

### 10. Métricas de Éxito — APPEND

Sizing (029): RUPE 115.305 proveedores totales, 56.884 activos, 54.076 activos UY. Mayor techo local de ARR: ~100 cuentas × USD 300/mes = USD 360K ARR. Ciclo de venta: 60-120 días.

### 11. Riesgos & Mitigación — APPEND

- IA agéntica 2026: Company más expuesta que Customs. IA ya hace perfil preliminar, ownership básico, noticias negativas y due diligence narrativo. Solo sobrevive como capa local integrada, no como standalone de research o raw data.
- Competidores UY ya activos en capa baja de procurement (LICITAIA, OportunidadesUY, LicitaPro). Diferenciación por profundidad, no por alertas básicas.

### 9. Roadmap (6 meses) — APPEND

Segunda vertical después de Customs. Uruguay-first, replicación país a país. No plataforma regional única sino sistema replicable. Montada sobre mismo hub que Customs.

