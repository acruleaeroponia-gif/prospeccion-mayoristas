# INTELIGENCIA — Acrule Meta

Este archivo es tuyo, Mariano. El agente lo lee PRIMERO cada mañana. Tus decisiones acá **mandan
sobre las reglas automáticas** del PLAYBOOK.

📚 Contexto completo (el agente también lo lee):
- `meta_dashboard/contexto/CONTEXTO_OPERATIVO.md` — negocio, campañas, aprendizajes, financiero.
- `creativos_sem22-28/DOCUMENTO_MAESTRO_ACRULE.md` — sistema creativo, conjuntos, naming.
- `meta_dashboard/REGLAS_API_META.md` — reglas anti-bloqueo (obligatorias).

---

## 🎯 Mis recomendaciones / decisiones (el agente las respeta)
<!-- Editá esta lista. Ejemplos de formato: -->
- NO juzgar las campañas de Mensajes por ROAS: su objetivo es costo por conversación y volumen.
- NO tocar campañas con <7 días desde el último cambio (fase de aprendizaje de Meta).
- Escalar presupuesto máximo +50% por vez, nunca más.
- Mini LED = INDOOR (cocina). Resto = OUTDOOR con sol. Respetar en toda recomendación creativa.

### Aprendizajes de la bitácora (reglas que el agente DEBE respetar)
- **Presupuesto en campañas CBO se sube a nivel CAMPAÑA, no conjunto.** Al escalar una CBO, redactar "subí +X% el presupuesto de la CAMPAÑA _Z_", NO "del conjunto". (Solo en ABO el presupuesto es por conjunto.)
- **Campaña corregida (29 jun):** "TEST Ang ABO Huerta 12 24 32" fue reemplazada por **"TEST Ang ABO Huerta 12 24 32 2"** (la vieja tenía catálogo dinámico mal armado). H-04 "Vivís en depto" y los tests viven ahora en la campaña **"...32 2"**. Referir siempre a la nueva.
- **Fatiga/ampliar: SOLO flaggear anuncios ACTIVE con frecuencia alta.** Nunca proponer refrescar/ampliar anuncios PAUSADOS (confunde). Verificar effective_status=ACTIVE antes de una orden de fatiga.
- **Órdenes de mantenimiento (P4) deben nombrar anuncio/conjunto/campaña EXACTOS y activos** — nada de "varias/varios".
- **Mensajes: evaluar por TEMPERATURA de audiencia, no con un target plano.** Los conjuntos FRÍO (audiencia nueva) sí apuntan al target $400/conv. Los conjuntos TIBIO/CALIENTE (retargeting, gente que ya interactuó) legítimamente cuestan MÁS por conversación porque la audiencia es más calificada y convierte mejor — NO pausarlos por costo alto. Si un conjunto tibio/caliente rinde caro, la orden correcta es **iterar el creativo (mejorar CTR) o crear un conjunto nuevo a esa misma audiencia con otros creativos**, no apagarlo. Sólo el frío se corta por costo.

### 🔬 FLUJO DE TESTING → ESCALA (aclarado 06/07) — cómo lee los lunes el cerebro
- Las campañas **TEST (ABO) son SOLO para testear** si un ángulo funciona — **NUNCA para escalar.** Presupuesto acotado y parejo; **no subir presupuesto en la campaña de test.** La pregunta que responde es "¿este ángulo vende, sí o no?", nada más.
- **Apagar rápido lo que no funciona:** apenas un ángulo muestra que no cierra (0 ventas + CTR/CPA malo con poco gasto), se **apaga de inmediato** — NO se deja correr los 7 días "por las dudas" ni se gasta de más. Los 7 días son el TECHO máximo, no un piso obligatorio. Solo los que muestran señal de venta se dejan madurar.
- **Escalar es SOLO en la CBO** (Huerta 12 24 32 2), nunca en el test. El test descubre; la CBO escala.
- **Los creativos/videos que funcionan se ESCALAN a la CBO** (ej. `CBO Huerta 12 24 32 2`) **usando el mismo post (postID)** — así se conserva la prueba social/engagement acumulado del anuncio.
- **El ángulo ganador se multiplica, no se congela:** además de subirlo a la CBO por postID, hay que **ITERARLO** (producir variantes nuevas del MISMO ángulo ganador — otro hook/formato/pieza) para seguir alimentando `CBO Huerta 12 24 32 2` con más de lo que ya gana. La CBO es el "estanque" de ganadores; los ganadores del test + sus iteraciones son lo que se mete ahí. Lo que no funciona: **apagar**.
- **Tarea de los LUNES del cerebro semanal:** bajar a nivel ANUNCIO dentro de cada conjunto de test y decir **qué ángulo/video ganó** (por ROAS + ventas). Por cada ganador, entregar: (a) recomendación de escalar a `CBO Huerta 12 24 32 2` por postID, y (b) un **brief de iteración de ese ángulo** (2-3 variantes) para producir. Por cada perdedor: apagar. No quedarse en métricas de campaña — el valor es "de este conjunto ganó el ángulo X → escalalo Y iteralo así; el resto apagá".
- Cadencia: cada lunes Mariano sube el test de la semana siguiente (ej. hoy sube el de Semana 3).

### 🔴 DECISIÓN CENTRAL (04/07): campañas de MENSAJES apagadas — foco 100% en VENTAS
- **Las campañas de Mensajes dedicadas NO generan las ventas de WhatsApp.** La gente que compra por WhatsApp entró por un anuncio de VENTAS/web, navegó el sitio y desde ahí escribió — no vino de los anuncios de las campañas de mensajes. Sus conversaciones eran baratas pero NO compraban (por eso su ROAS 0,13–0,59 era REAL, no un error de medición).
- **Decisión de Mariano: campañas de Mensajes APAGADAS.** El agente NO debe recomendar reactivarlas ni crear nuevas campañas de mensajes. Foco 100% en campañas de VENTAS (OUTCOME_SALES), que son las que alimentan tanto las compras web como las de WhatsApp.
- **Corolario de medición:** el ROAS real de las campañas de ventas es MÁS ALTO que el del píxel, porque parte de su tráfico convierte por WhatsApp (el píxel de compra web no lo cuenta). Tenerlo en cuenta al juzgar si una campaña de ventas "rinde": puede rendir más de lo que muestra el número.

## 📐 Parámetros del negocio (ver `contexto/KPIS_FINANCIEROS_2026.md`)
- Ticket Mini LED $218.900 · Mini sin LED $121.900 · Huerta 12/24/32 $348.900/$398.900/$486.300 · Curso $68.000 · Ebook $24.480.
- **Margen bruto: 65%.** AOV ~$199-234k. CAC Meta ~$77k.
- **Break-even ROAS (MEB): ~3,4.** Debajo de eso = se pierde plata. Hoy ROAS ~2,8 → EN PÉRDIDA.
- **El negocio está a pérdida en 2026 (–$95,7M).** Ads = 31% de la facturación (mayor costo controlable). Por eso el objetivo ROAS 6 es supervivencia, no lujo.
- **Target costo por conversación WhatsApp: $400 ARS** (KPI oficial). Actual $511–$1.181.
- % de conversaciones WA que terminan en venta: _____ %  ← completar (WhatsApp cierra ~$72M/año, no lo ve el píxel).
- ROAS objetivo ventas: **6** (mínimo para no perder: 3,4). Frecuencia máxima: 3.5.

## ✅ Ángulos GANADORES (confirmados con data)
- 🏢 **H-04 Vivís en depto** — ROAS 6.89x (escalando) — Huertas grandes
- 🍳 **Cocina Mini LED** — ROAS 4.70x (motor validado) — Mini LED
- ⭐ **RES-03 Antes/Ahora** — ROAS 4.65x — Mini sin LED (⚠️ cuidar política antes/después)
- 💬 **FRÍO-04 Problema/Solución** — mejor de Mensajes

## ❌ Ángulos MUERTOS (no reintentar igual)
H-01 ahorro/verdura · H-02 no sé de plantas (CTR 0.49%) · Fundador en estático (0) · RES-04 capturas WhatsApp (0) · SE Sin Esfuerzo (Meta descartó).

## 🔄 RE-TEST (fallaron por creativo, no por ángulo)
- H-05 +3.000 familias → re-test con MAPA de Argentina.
- H-07 Sin tiempo → re-test con "persona ocupada + huerta funcionando".

## 🧪 EN TESTING sem 2 (arranca 30 jun) — dejar 7 días sin tocar
H-03 ROI paga la huerta · H-08 de cero a cosecha en 3 semanas · H-09 tu balcón es suficiente · H-12 las que se mueren vs la que crece · H-14 sin saber/complicarte/morir.

## ⚪ BACKLOG (sin testear)
H-06 familia comiendo lo cultivado · H-10 antes gastaba en verdura · H-11 de la huerta al plato en 3 min · H-13 mi hijo se enamoró de las plantas · H-15 cosechar es meditar · H-16 Argentina cultiva en casa · H-17 sin químicos · H-18 regalá una huerta · H-19 el huerto que cabe en tu cocina · H-20 de vacía a cosechada en 21 días.

## 📄 Documentos madre
- ✅ Cargados: `contexto/CONTEXTO_OPERATIVO.md` y `creativos_sem22-28/DOCUMENTO_MAESTRO_ACRULE.md`.
- Pendiente completar arriba: margen por venta y % conversación→venta.
