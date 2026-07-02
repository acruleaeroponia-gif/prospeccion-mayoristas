# CLAUDE.md — Reglas del proyecto Acrule

## 🛡️ Uso de la API de Meta (OBLIGATORIO — anti-bloqueo)
Antes de tocar la cuenta de Meta, leer y respetar `meta_dashboard/REGLAS_API_META.md`. Resumen no negociable:
- **SOLO LECTURA.** Nunca crear/editar/pausar/duplicar/borrar campañas, conjuntos, anuncios, presupuestos ni audiencias por API. Claude recomienda, Mariano ejecuta en Ads Manager.
- **Máx ~20 llamadas de lectura por corrida.** Sin loops. Batch por nivel (campaign/adset/ad), no una llamada por entidad.
- **Cuenta viva única:** `Acrule Publicidad` ID `1447555046054434` (ARS). Ignorar las demás cuentas.
- Si hay error de rate-limit (17/80000/80004): parar, esperar, reintentar 1 vez. No insistir en loop.
- Cuidar políticas de anuncios (antes/después, claims de salud, promesas de ingresos) — eso SÍ deshabilita cuentas.

## 📊 Sistema Meta (dashboard + agente)
- Panel y motor en `meta_dashboard/`. Ver `PLAYBOOK.md` (lógica), `INTELIGENCIA.md` (decisiones de Mariano — mandan), `contexto/CONTEXTO_OPERATIVO.md` y `creativos_sem22-28/DOCUMENTO_MAESTRO_ACRULE.md` (contexto de negocio/creativos).
- Ventas (OUTCOME_SALES) se miden por ROAS. Mensajes (MESSAGES/ENGAGEMENT) por costo por conversación (target $400) y cantidad — NO por ROAS.
- Objetivo: ROAS de ventas → 6.
