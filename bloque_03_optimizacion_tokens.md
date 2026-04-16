---
tags: [capacitacion, bloque, tokens, optimizacion, context-rot, chunking, caveman]
bloque: 3
duracion: 15 min
previo: "[[bloque_02_prompt_engineering]]"
siguiente: "[[bloque_04_flujos_trabajo_ia]]"
relacionado: ["[[bloque_01_que_es_un_LLM]]", "[[bloque_05_obsidian_cerebro_claude]]", "[[plantilla_prompt_base]]", "[[Construyendo con IA/Sistemas RAG]]"]
---

# Bloque 3 — Optimización de Tokens

> [!info] Navegación
> ← [[bloque_02_prompt_engineering]] | Siguiente → [[bloque_04_flujos_trabajo_ia]]

**Duración:** 15 minutos  
**Objetivo:** Que el equipo reduzca su consumo de tokens 60–80% sin sacrificar calidad de resultados.

---

## 🎯 Idea central

> Más tokens no es mejor. Contexto limpio supera a contexto grande.

---

## 1. Context Rot — el enemigo silencioso (4 min)

### ¿Qué es?

**Context rot** = degradación progresiva de la calidad de Claude conforme crece el historial de la conversación.

No es que se llene la ventana. Es que **el ruido acumulado contamina el razonamiento**.

> [!tip] Conecta con
> El efecto [[bloque_01_que_es_un_LLM#4. El efecto "Lost in the Middle"|Lost in the Middle]] se amplifica con cada turno extra.

### Los datos duros (Chroma Research, 2025)

Se evaluaron 18 modelos de última generación. Resultado:

| Tokens de contexto | Precisión promedio |
|--------------------|--------------------|
| 0 – 10K | 95% ✅ |
| 10K – 32K | 85–90% ✅ |
| 32K – 64K | 70–80% ⚠️ |
| 64K – 100K | 60–75% ❌ |
| 100K+ | < 60% ❌ |

**A 32K tokens, 11 de 12 modelos cayeron por debajo del 50% de precisión.**

### Síntomas que ya has vivido

- ✦ Claude "olvida" instrucciones que diste al inicio
- ✦ Respuestas se vuelven repetitivas o contradictorias
- ✦ Empieza a alucinar más que al inicio
- ✦ Cada respuesta tarda más y es menos útil
- ✦ Sientes que "se perdió el hilo"

### La causa raíz

Cada mensaje que envías **re-envía todo el historial anterior**.

```
Turno 1:  500 tokens enviados
Turno 2:  500 + 500 = 1,000 tokens enviados
Turno 3:  500 + 500 + 500 = 1,500 tokens enviados
...
Turno 20: 500 × 20 = 10,000 tokens solo de historial
```

Pagas el historial completo en cada turno. Y el 60% de ese historial suele ser ruido.

---

## 2. Las 5 técnicas de optimización (7 min)

### Técnica 1 — Prompts caveman 🪨

Elimina palabras innecesarias sin perder precisión. Claude entiende igual.

| Antes | Después | Ahorro |
|-------|---------|--------|
| "¿Podrías por favor resumirme este documento?" | `"Resumen:"` | 85% |
| "Revisa el código buscando errores, problemas de rendimiento y seguridad" | `"Review: bugs, perf, security"` | 82% |
| "Actúa como experto en finanzas y analiza el siguiente reporte" | `"[ROL: analista financiero] Analiza:"` | 60% |

**Promedio de ahorro en outputs:** 65% (rango: 22–87%)

> [!tip] Plantilla comprimida
> Ver [[plantilla_prompt_base#Versión rápida (tareas simples)|versión rápida]] de la plantilla RTFC.

---

### Técnica 2 — Formato eficiente 📊

El formato en que pegas información importa tanto como lo que pegas.

| Formato | Tokens para 100 filas de datos | Vs JSON |
|---------|-------------------------------|---------|
| JSON | 100% (baseline) | — |
| YAML | ~50% | -50% |
| CSV | ~55% | -45% |
| Tabla markdown | ~60% | -40% |

**Regla:** datos tabulares → CSV o YAML, nunca JSON crudo si puedes evitarlo.

---

### Técnica 3 — Chunking de documentos 📄

Nunca pegues un documento completo si solo necesitas una parte.

**El protocolo inteligente:**

```
Paso 1: Pega solo el índice o tabla de contenidos (~200 tokens)
Paso 2: Pregunta → "¿Qué secciones son relevantes para [tu tarea]?"
Paso 3: Claude responde → solo alimenta esas secciones (~2,000 tokens)
```

**Comparación real — reporte de 50 páginas:**

| Enfoque | Tokens usados | Costo aprox |
|---------|--------------|-------------|
| Pegar todo el documento | ~15,000 | $0.045 |
| Protocolo de chunking | ~2,200 | $0.007 |
| **Ahorro** | **85%** | **$0.038** |

**Tamaño ideal de chunk:** 300–500 tokens con 10–15% de solapamiento entre secciones.

---

### Técnica 4 — Nueva conversación a tiempo 🔄

**Regla de oro:** después de 15–20 turnos, empieza conversación nueva.

| Situación | Acción |
|-----------|--------|
| Cambias de tema radicalmente | Nueva conversación ✅ |
| Superas 15 turnos | Nueva conversación ✅ |
| Claude empieza a alucinar más | Nueva conversación ✅ |
| Refinando la misma tarea | Continuar ✅ |
| Construyendo sobre decisiones previas | Continuar ✅ |

**Para no perder el hilo al reiniciar:**

```
Lleva notas externas con:
- Decisiones tomadas
- Avances completados
- Instrucciones recurrentes

Al iniciar nueva conversación pega esas notas (~500 tokens)
en lugar de todo el historial anterior (~10,000 tokens)
→ Ahorro: 95%
```

> [!tip] Obsidian resuelve esto
> [[bloque_05_obsidian_cerebro_claude]] muestra cómo tu vault reemplaza el historial de conversaciones.

---

### Técnica 5 — Poda del output ✂️

~40% de las respuestas de Claude es explicación que no pediste.

Añade estas instrucciones para cortar el exceso:

```
"Solo el resultado. Sin explicaciones."
"Lista directa. Sin introducción ni cierre."
"Solo el código. Sin comentarios."
"Máximo 150 palabras."
"Sin contexto previo, directo al punto."
```

**Impacto:** reduce output tokens 40–60% con la misma utilidad.

---

## 3. Costo real: eficiente vs ineficiente (3 min)

### Caso: analizar un reporte financiero de 50 páginas

**Enfoque ineficiente:**

```
1. Pegar reporte completo: 15,000 tokens
2. Preguntas largas con contexto repetido × 5 turnos
3. Recibir respuestas con explicaciones extensas
Total: ~35,000 tokens → $0.135 por análisis
```

**Enfoque optimizado:**

```
1. Chunking (solo secciones relevantes): 2,500 tokens
2. Prompts caveman × 5 turnos
3. Output podado
Total: ~4,000 tokens → $0.024 por análisis
```

**Ahorro: 82%**

### Escala mensual — equipo de 10 personas

| Uso | Tokens/mes | Costo/mes |
|-----|-----------|----------|
| Sin optimizar | ~500M | ~$1,500 |
| Optimizado | ~100M | ~$300 |
| **Diferencia** | | **$1,200/mes** |

---

## 🔑 Takeaways del Bloque 3

1. **Context rot es real** — calidad cae al 60% pasados 64K tokens
2. **Regla 15/20** — nueva conversación cada 15–20 turnos
3. **Caveman prompts** — 60–85% ahorro en tokens de entrada
4. **Nunca pegues el documento completo** — usa chunking (85% ahorro)
5. **Poda el output** — "solo el resultado" = 40–60% menos tokens de salida
6. **CSV/YAML > JSON** para datos tabulares

---

## 💡 Demo sugerida (en vivo)

**Demo 1 — Mide el costo de una conversación larga:**
1. Abre una conversación con 20 turnos
2. Muestra cómo crece el historial
3. Compara con conversación limpia de 3 turnos para la misma tarea

**Demo 2 — Chunking en vivo:**
1. Toma un reporte de 10 páginas
2. Pega el índice y pide qué secciones importan
3. Alimenta solo esas secciones
4. Muestra la diferencia de tokens vs. pegar todo

---

> [!info] Navegación
> ← [[bloque_02_prompt_engineering]] | Siguiente → [[bloque_04_flujos_trabajo_ia]]

*Fuentes: Chroma Research "Context Rot" (2025), Redis Token Optimization Blog, Medium "Caveman Prompt" (2025), Pinecone Chunking Strategies, Anthropic Context Engineering Docs, SiliconData 2026*
