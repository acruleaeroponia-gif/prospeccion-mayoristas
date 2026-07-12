# 🚀 ESTRUCTURAS DE ESCALADO — Meta Ads Acrule

> Cómo escalar lo que YA funciona. El TEST descubre ganadores; estas estructuras los EXPLOTAN.
> Regla base común: se usan solo con **anuncios ganadores validados** (buen ROAS + buen CPA). Se duplican los MISMOS anuncios ganadores (por **postID**, para conservar prueba social), todos al **mismo producto/mismo link**. Se optimiza **matando los conjuntos que no venden**, no bajando presupuesto.
> API es de lectura: el agente detecta las condiciones y avisa; **Mariano crea la campaña en Ads Manager.**

---

## 0) onlypocket — explotar UN solo ganador (ya la usás)
- **Qué es:** 1 campaña · 1 conjunto · 1 anuncio ganador (postID). Presupuesto diario ≈ el **CPA (costo de adquisición)** que viene teniendo.
- **Cuándo:** tenés UN anuncio claramente ganador y querés exprimirlo para que llegue a más gente.
- **Objetivo:** darle aire a un ganador puntual sin romperle el aprendizaje.

---

## 1) DEEP POCKET — escalado FUERTE (el "hipoque")
- **Cuándo (condiciones):** tenés **4-5 anuncios ganadores en los últimos 7 días** con buen ROAS y buen CPA. Ideal: anuncios con **10-15 ventas** c/u.
- **Estructura:** CBO · presupuesto diario alto (ej. **$100k** o **$200k/día**). Nº de conjuntos = **presupuesto diario ÷ CPA** (ej. budget 70 USD ÷ CPA 8,86 ≈ 8 → armás **7-8 conjuntos**). Cada conjunto = los MISMOS 4-5 ganadores (postID), todos al mismo link/producto.
- **Dos versiones:** $100k/día (ganadores con 7-8+ ventas) · $200k/día (ganadores 10-15 ventas, súper rentables).
- **Optimización:** el presupuesto **NO se sube ni se baja**. Al **día 3** (decisión fuerte): matás los conjuntos que no vendieron o con CPA muy alto; dejás los que venden. Escalar más = **duplicar la campaña** (única forma).

## 2) BID CAP (Bidcap) — escalado con LÍMITE DE PUJA (medio, controlado)
- **Cuándo:** anuncios ganadores con **4+ ventas** (idealmente 24+), buen ROAS y CPA.
- **Estructura:** campaña con estrategia de puja = **Límite de puja**. Varios conjuntos, cada uno con un **límite de puja distinto alrededor del CPA actual**: ej. CPA $40 → conjuntos con 40, 41, 42, 43, 44, 45, 46 (**6 para arriba**) + 39, 38, 37 (**3 para abajo**). Presupuesto por conjunto ~**$60-70**. Mismos anuncios ganadores en todos.
- **Optimización:** los conjuntos que no gastan → quedan quietos. Los que gastan y venden bien (buen ROAS al mediodía) → **escalás intradía ×2** (60→120→240) mientras siga rindiendo, y **volvés a 60 al fin del día**. Detectás qué límites de puja funcionan y esos replicás.

## 3) COST CAP (Coscap) — meter ventas a BUEN COSTO (optimizar, no escalar fuerte)
- **Cuándo:** la cuenta está **floja / medio parada** (ej. ROAS ~2), querés inyectar ventas a costo controlado. También para probar antes de ir a Deep Pocket.
- **Estructura:** campaña (ABO) con estrategia = **Límite de coste / "Objetivo de costo por resultado" (cost cap)**. 3-4 conjuntos con los mismos ganadores, con **cost cap escalonado**: conjunto1 = tu CPA objetivo (ej. $50k), conjunto2 = +incremento (ej. $55k), conjunto3 = +otro (ej. $60k). Meta decide cuándo competir por más gente sin pasarse del costo.
- **Optimización:** dejás los cost caps que traen ventas a buen costo; duplicás. Es más tranqui que Deep Pocket: mete ventas rentables, no explota volumen.

## 4) BLUEPRINT — escalado por RÁFAGA (time-boxed, mini Deep Pocket)
- **Cuándo:** querés un empujón controlado por un período corto (mismas condiciones que Deep Pocket pero más chico).
- **Estructura:** igual que Deep Pocket pero **solo 2 conjuntos** (uno es duplicado del otro), mismos ganadores. Campaña con **fecha de finalización** (ej. 14 días). Los conjuntos con corte por fecha (~3 días): si va perdiendo, se apaga solo. Tener en cuenta **frecuencias** (separar los de alta freq/retargeting de los de baja).
- **Optimización:** se apaga por fecha; se leen frecuencias para decidir qué sostener.

---

## 🧭 Cuál usar según el momento
| Situación | Estructura |
|---|---|
| 1 ganador puntual para exprimir | **onlypocket** |
| Cuenta floja (~ROAS 2), meter ventas a buen costo | **Cost Cap** |
| 4+ ganadores, escalar controlado con pujas | **Bid Cap** |
| Empujón corto por ráfaga (14 días) | **Blueprint** |
| 4-5 ganadores con 10-15 ventas, ROAS y CPA muy buenos → romperla | **Deep Pocket** ($100k/$200k día) |

## 📌 Trigger para el sistema (qué debe avisar el agente/cerebro)
- Si en los últimos 7 días hay **≥4-5 anuncios ganadores** (ROAS ≥ objetivo y CPA sano) → avisar "condiciones para **Deep Pocket**" y calcular Nº conjuntos = presupuesto ÷ CPA.
- Si hay **1 ganador fuerte** aislado → sugerir **onlypocket** (budget = su CPA).
- Si un ganador tiene **≥4 ventas** pero querés escalar sin arriesgar → **Bid Cap** con límites alrededor del CPA.
- Si la cuenta se enfría (ROAS ~2) → **Cost Cap** para sostener ventas a costo objetivo.
- Siempre: mismos ganadores por postID, mismo link, matar conjuntos perdedores (día 3), escalar duplicando.

*Fuente: transcripción de 4 videos de estructuras de escalado (Cost Cap, Blueprint, Deep Pocket, Bid Cap) + lógica de onlypocket. Cargado 10/07.*
