---
status: legacy_do_not_use_as_truth
legacy_marked_at: 2026-05-12
supersedes: C:\dev\Investigacion_Osla_consolidada\OK\verticales\osla_perfil_empresa\product.md
reason: OSLA canonical documentation moved to consolidated OK tree after V3/saneamiento audit.
do_not_use_for: product_truth, roadmap_truth, implementation_scope, claims, data_rights
---

# AGENTS.md — OslaFirma

## Identidad del proyecto

- **Nombre**: OslaFirma (Supplier Risk + Company Intelligence)
- **Ranking InvestigaVert**: — Score 4.2)
- **AshRise project_id**: `empresa`
- **Puerto Postgres**: 5452
- **DB**: empresa / user: empresa
- **ICP primario**: Oficial de compliance en bancos/financieras
- **ICP secundario**: Inversores, estudios contables
- **Pricing target**: USD 200-500/usuario/mes
- **Estado validación**: PENDIENTE — requiere validación con compliance officers

## Qué es

Grafo empresarial persistente que cruza DGI (facturación, CFE) + BPS (empleados, aportes) + RUPE + GLEIF + Wikidata + licitaciones ARCE. Scoring crediticio, monitoreo continuo, alertas de cambio de estado. Sistema con memoria que detecta anomalías, quiebras inminentes, cambios en estructura accionaria y riesgos de vinculación con entidades sancionadas.

## Problema que resuelve

Un oficial de compliance en un banco revisa 500+ proveedores/año. Hoy vuela entre RUPE, DGI (si obtiene acceso), bases de datos fragmentadas, y análisis manual. Un sistema integrado que cruza facturación, empleados, estado legal, y vinculaciones ocultas detecta riesgos de contrapartes en segundos, alertando cambios antes de que generen exposición regulatoria.

## Modelos ML defensibles

1. **Bankruptcy Prediction** (GBM, 6-12 meses): predice quiebra próxima. Accuracy 85-92%.
2. **Supplier Risk Scoring**: scoring 0-100 integrando liquidez, crecimiento, estructura societaria, historial.
3. **Continuous Monitoring Alerts**: detección de cambios estructurales (cambio de socios, facultades, domicilio, estado legal).
4. **Network Risk Propagation**: si proveedor cae, qué clientes/proveedores del mismo se ven afectados.

## Fuentes de datos

### Uruguay
- DGI: facturación electrónica (CFE), certificados fiscales, impuesto a la renta
- BPS: cotizantes mensuales, aportes, estado del trabajador
- RUPE: registro de proveedores estado, domicilio, estado legal
- ARCE: licitaciones históricas, adjudicaciones
- BCU: cotizaciones, tipo de cambio (API SOAP)
- IMPO API: legislación mercantil

### Internacionales
- GLEIF (CC0): identificación legal global, estructuras corporativas
- Wikidata (CC0): metadata entidades, relaciones conocidas públicamente
- Companies House UK (open): estructuras corporativas internacionales (para vinculados)
- SEC EDGAR: empresas estadounidenses (si hay vinculación)
- OFAC Sanctions: lista de entidades sancionadas
- World Bank debarred: proveedores sancionados internacionalmente

## Acceso a datos compartidos (via FDW)

```sql
SELECT * FROM shared.entity WHERE ...;
SELECT * FROM shared.fx_rates WHERE currency_code = 'USD';
SELECT * FROM shared.normativa_snapshots WHERE ...;
```

## Stack técnico

- Backend: FastAPI (Python)
- Frontend: Next.js 15 + Tailwind
- DB: Postgres 16 (puerto 5452)
- ML: scikit-learn + LightGBM + MLflow
- Data pipeline: Airflow + dbt
- Storage: S3-compatible

## Reglas de boundary

1. Repo, base de datos, storage y colas propios.
2. No leer ni escribir directo en la base de otra vertical.
3. Compartir datos solo por FDW read-only desde shared-db.
4. Reusar patrones del núcleo reusable (source discovery, document extraction, identity resolution, alerts/tasks).

## Reglas para agentes

1. **No escribir en shared-db** — solo leer vía FDW
2. **DGI + BPS es fuente de verdad** para estado empresarial actual
3. **Evidence-first**: cada alerta deja fuente, fecha, snippet y confianza
4. **Deterministic-first**: no usar LLM en hot path si existe opción determinista
5. **No afirmar riesgo sin evidencia documental**

## Variables de entorno

```
ASHRISE_BASE_URL=http://localhost:8080
ASHRISE_TOKEN=<token>
ASHRISE_PROJECT_ID=empresa
```

## Documentación del producto

- **[docs/Producto.md](docs/Producto.md)** — Documento completo del producto: visión, ICP, propuesta de valor, fuentes de datos, modelos ML, competencia, arquitectura, roadmap y métricas. Se actualiza cuando una investigación impacta esta vertical.
- **[docs/Investigaciones.md](docs/Investigaciones.md)** — Log cronológico de investigaciones procesadas que impactan esta vertical: si fortalecen o debilitan la tesis, y qué se actualizó en Producto.md como consecuencia.
- **[docs/ROADMAP.md](docs/ROADMAP.md)** — Milestones técnicos de implementación.

## Contrato AshRise

Al iniciar sesión: leer AGENTS.md → docs/ROADMAP.md → GET /state/empresa → GET /handoffs/empresa?status=open
Al cerrar: emitir ashrise-close con run + state_update.
