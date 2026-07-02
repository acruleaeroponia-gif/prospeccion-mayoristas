# 🛡️ REGLAS DE USO DE LA API DE META — ANTI-BLOQUEO

> Obligatorio para CUALQUIER sesión (agente diario o chat interactivo) que toque la cuenta de Meta.
> Objetivo: nunca gatillar rate-limits ni poner en riesgo la cuenta `1447555046054434`.

## 1. Entender los dos riesgos (son distintos)
- **Rate limit (throttle):** demasiadas llamadas API en poco tiempo → bloqueo TEMPORAL de ~5 min (errores 17, 80000, 80004, 613). NO es baneo. Se resuelve solo esperando.
- **Baneo de cuenta:** lo causan violaciones de **políticas de anuncios**, problemas de pago o logins/actividad sospechosa — NO leer datos. (Ver sección 5.)
- Leer insights con conectores de lectura es de bajo riesgo. El peligro nace de loops, escrituras masivas o cambios repetidos de presupuesto.

## 2. Presupuesto de llamadas (heurística segura: ~60 puntos / 5 min)
- Lectura = 1 punto · Escritura = 3 puntos.
- **Tope duro auto-impuesto: máximo 20 llamadas de lectura por corrida.** El agente diario usa ~8-10. Nunca acercarse a 60/5min.
- **1 sola corrida automática por día** (cron 7AM). No re-correr el agente en loop.

## 3. Reglas DURAS (no romper)
1. **SOLO LECTURA.** Prohibido crear/editar/pausar/duplicar/borrar campañas, conjuntos, anuncios, presupuestos o audiencias vía API. El agente RECOMIENDA; Mariano EJECUTA en Ads Manager.
2. **Sin loops.** Nunca hacer llamadas repetidas en bucle "hasta que…". Si una llamada falla por rate-limit, ESPERAR y reintentar UNA sola vez, no en loop.
3. **Batch, no goteo.** Traer campaña/adset/ad en una llamada por nivel con todos los campos necesarios (sort + limit). No una llamada por entidad.
4. **Cachear en archivos.** Guardar los datos del día en el reporte/DASH. Si en la misma sesión se necesita el dato otra vez, releerlo del archivo, NO volver a llamar la API.
5. **Nada de cambios de presupuesto automatizados.** Aunque en el futuro se habilite escritura: subir presupuesto máx +50% por vez, nunca cambios repetidos en la misma hora (Meta lo marca como sospechoso).
6. **Ventanas estándar.** Usar date_preset (last_30d, last_7d). No barrer día por día en bucle.

## 4. Chequeo de conexión (verificar 1 vez)
La forma actual es correcta: conectores **de lectura** vía el MCP oficial de Meta. Checklist recomendado (buenas prácticas del blog de F. Vergara):
- [ ] Permisos en modo **`ads_read`** (lectura), no `ads_management`, mientras no se ejecute por API.
- [ ] Idealmente, integraciones desde un **Business Manager / System User** dedicado, separado del personal.
- [ ] Token de acceso sin vencimiento corto (evita reconexiones a mitad de análisis).
- [ ] Cuenta principal con método de pago sano y sin flags.

## 5. Políticas de anuncios (esto SÍ puede deshabilitar la cuenta)
Riesgos concretos para Acrule (huertas / salud / testimonios):
- **"Antes/Ahora" (RES-03) y transformaciones:** Meta restringe imágenes antes/después que impliquen cambio de vida/salud o generen autoimagen negativa. Usar con foco en el PRODUCTO/RESULTADO de cultivo, no en salud personal. Riesgo de rechazo.
- **Claims de salud:** no afirmar que cura/previene/mejora la salud sin evidencia. Foco en features (rendimiento, facilidad, sustentable), no en "más sano/curativo".
- **Testimonios:** deben ser reales y verificables; no exagerar resultados ni prometer ingresos garantizados (relevante para Emprendedores).
- **Atributos personales:** no dar a entender que conocés condiciones personales del usuario ("¿sos negada con las plantas?" puede rozar — cuidar el tono).
- **Emprendedores/ingresos:** evitar promesas de ganancias garantizadas.
- Regla práctica: mensaje sobre el producto (cosecha, facilidad, cuotas, kit), no sobre el cuerpo/salud/plata garantizada.

## 6. Si aparece un error de rate-limit
1. Parar. No reintentar en loop.
2. Esperar ~5-15 min.
3. Reintentar la corrida UNA vez.
4. Si persiste, avisar a Mariano y no insistir ese día.

---
*Fuentes: Meta Marketing API rate limiting (developers.facebook.com), Ad Standards (transparency.meta.com), guía Claude Code + Meta Ads (felipevergara.co). Última revisión: 30 jun 2026.*
