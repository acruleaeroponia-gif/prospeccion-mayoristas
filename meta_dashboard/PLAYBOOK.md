# PLAYBOOK Meta — Acrule · Camino a ROAS 6

Este es el cerebro del sistema. El agente diario lee Meta y aplica estas reglas para generar
las **órdenes del día**. Mariano las ejecuta en Ads Manager (los conectores MCP son de lectura).

## Contexto fijo
- **Cuenta viva:** `Acrule Publicidad` — ID `1447555046054434` (ARS). Ignorar las demás (read-only / vacías / disabled).
- **Negocio:** Acrule vende kits de huerta hidropónica urbana. **Las ventas se cierran en la web (Shopify).**
  → El píxel SÍ trackea las ventas. **El `purchase_roas` es confiable.** No hay venta oculta por WhatsApp.
- **Objetivo:** ROAS de cuenta = **6** (hoy 2,58 y bajando). **Sin techo de presupuesto** mientras el ROAS aguante.
- **Punto de partida (29 jun 2026):** ROAS 30d 2,58 · ROAS 7d 2,18 · CTR 2,87% → 2,06% · Opp. Score 57.

## Umbrales de decisión (reglas duras)

### A nivel CAMPAÑA / AD SET / ANUNCIO
| Condición | Veredicto | Orden |
|---|---|---|
| ROAS < 1 y gasto > $30k y ACTIVO | 🔴 SANGRA | **Pausar hoy** |
| Objetivo = Mensajes/Interacción y ROAS < 1,5 | 🔴 MAL OPTIMIZADO | Pausar o migrar a OUTCOME_SALES |
| ROAS 1–2 y ACTIVO | 🟠 DÉBIL | Recortar budget 50% / vigilar 3 días, si no mejora cortar |
| ROAS 2–3 | 🟡 MEDIO | Iterar creativo, mantener budget |
| ROAS ≥ 3 (campaña) / ≥ 4 (anuncio) | 🟢 GANADOR | **Escalar +20-25%/día** |
| ROAS ≥ objetivo (6) pausado | 💎 DORMIDO | Reactivar ya |
| Frecuencia > 3 | 😴 FATIGA | Refrescar creativo / ampliar audiencia |
| CTR < 1,3% | 👎 CREATIVO FLOJO | Pausar anuncio o nuevo hook |
| Audiencia < 50k (anomaly narrow) | 📉 ANGOSTA | Ampliar / Advantage+ Audience |

### CAMPAÑAS DE MENSAJES — NO se juzgan por ROAS
Objetivo = **costo por mensaje** (`cost_per_result`) y **cantidad de mensajes** (`results`, "Messaging conversations started"). El `purchase_roas` acá es irrelevante, ignoralo.
| Condición | Veredicto | Orden |
|---|---|---|
| Costo/msj ≤ target (def. $600, ver INTELIGENCIA) | 🟢 BARATO | Escalar / reactivar |
| Costo/msj entre 1–1,6× target | 🟡 MEDIO | Iterar creativo/audiencia |
| Costo/msj > 1,6× target o > 2× el mejor conjunto | 🔴 CARO | Pausar conjunto |
| Audiencia < 50k en conjunto de mensajes | 📉 ANGOSTA | Ampliar antes de pausar |
- Benchmark actual: mejor conjunto "CONJUNTO A Frío" = $494/msj. Usar como vara.
- Campañas de mensajes: `CBO Mensajes Huertas` (1447...) y `CBO Emprendedores Mensajes`.
- Si Mariano define en INTELIGENCIA el % de mensajes→venta, recalcular si el canal rinde de verdad.

### Reglas de escalado (no romper el aprendizaje)
- Subir presupuesto **máx +20-25% por día** por ad set. Nunca duplicar de golpe.
- No tocar un ad set con < 50 conversiones / aún en "learning" salvo que sangre.
- Al liberar budget de lo que se corta, **reasignarlo a ganadores existentes**, no a campañas nuevas.

### Palanca de ROAS = volumen rentable + eficiencia + AOV
1. **Cortar lo malo** (sube ROAS blended sin perder ventas reales).
2. **Concentrar** gasto en los 3 ángulos ganadores.
3. **Iterar creativos** sobre lo que ya gana (2-3 nuevos/semana).
4. **Subir AOV** (bundles, cuotas, order-bump): con el mismo CPA, más facturación = más ROAS. Esta es la palanca final hacia 6.

## Ángulos (actualizar el ranking cada día con los datos)
- 🍳 **Cocina / recetas frescas** → ganador #1 (ESCALAR)
- 🚀 **Innovación / huerta del futuro** → ganador #2 (ESCALAR)
- ⭐ **Reseñas / antes-después (UGC)** → probado (ITERAR)
- ⏱️ Fácil y sin tiempo → medio (ITERAR)
- 📚 Ebook / catálogo → flojo (PAUSAR)
- 💬 Emprendedores por mensajes → pésimo (PAUSAR)

## Quick-wins de Meta (Opportunity Score) — aplicar cuando aparezcan
- `budget_limited`: subir budget de los ad sets marcados (+9 pts).
- `aplusc_standard_enhancements`: activar mejoras A+ (+8 pts).
- `music`: activar música automática (+7 pts).
- `fragmentation`: combinar ad sets duplicados para salir antes del aprendizaje (+4-6 pts).
- `reels_pc`: usar 9:16 con audio.

## INTELIGENCIA (leer SIEMPRE primero)
Antes de generar órdenes, leer `meta_dashboard/INTELIGENCIA.md`. Las decisiones de Mariano
(sección "Mis recomendaciones") **mandan sobre las reglas automáticas**. Ejemplos: si dice
"no pausar Mensajes Huertas", no se pausa; si dice "testear ángulo X esta semana", va como orden P3.
Usar también: AOV, margen, target costo/msj, % mensaje→venta, y el backlog de ángulos pendientes.
Volcar `recomendaciones` y `pendientes` al objeto DASH.inteligencia del dashboard.

## Formato OBLIGATORIO de cada orden
Cada orden DEBE indicar la **ruta exacta** y la **acción** explícita:
- `accion`: una de `apagar | iterar | escalar | ampliar | reactivar`.
- `ruta`: { campana, conjunto, anuncio }. Si aplica a todo un conjunto/campaña, poner "(todo el conjunto)".
- Redactar como: "**Apagá** el anuncio _X_ del conjunto _Y_ de la campaña _Z_, porque _motivo (con el dato)_".
- Si `accion = iterar`: incluir `iteraciones` = lista de pasos EXACTOS y concretos (qué cambiar:
  hook, formato, copy, prueba social, oferta), y un `ejemplo` aplicado a Acrule. Estos se muestran
  bajo la flechita desplegable del dashboard.

## Cómo se priorizan las órdenes
- **P1 (rojo):** cortar sangría — apagar anuncios/conjuntos malos (ventas < ROAS 2 dentro de campañas buenas; mensajes caros).
- **P2 (verde):** escalar/reactivar ganadores — captura demanda no aprovechada.
- **P3 (azul):** iterar — con pasos exactos + ejemplos.
- **P4 (ámbar):** mantenimiento (audiencias, fatiga, quick-wins).

Máximo 8 órdenes por día, cada una con ruta exacta. Respetar SIEMPRE lo que diga INTELIGENCIA.md.
