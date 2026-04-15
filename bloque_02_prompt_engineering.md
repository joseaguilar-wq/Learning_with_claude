---
tags: [capacitacion, bloque, prompt-engineering, mejores-practicas, framework]
bloque: 2
duracion: 20 min
previo: "[[bloque_01_que_es_un_LLM]]"
siguiente: "[[bloque_03_optimizacion_tokens]]"
relacionado: ["[[bloque_05_obsidian_cerebro_claude]]", "[[plantilla_prompt_base]]"]
---

# Bloque 2 — Prompt Engineering

> [!info] Navegación
> ← [[bloque_01_que_es_un_LLM]] | Siguiente → [[bloque_03_optimizacion_tokens]]

**Duración:** 20 minutos  
**Objetivo:** Que el equipo construya prompts que produzcan resultados consistentes y de calidad.

---

## 🎯 Idea central

> Un prompt es una instrucción de trabajo. Si a un humano le darías ese briefing y esperarías un buen resultado, Claude también lo dará. Si no, reescríbelo.

---

## 1. Por qué fallan los prompts (3 min)

La mayoría del equipo escribe prompts como si le mandara un mensaje de WhatsApp a un amigo que "ya sabe de qué va".

Claude **no sabe de qué va**. Cada conversación empieza desde cero.

### Los 4 errores más comunes

| Error | Ejemplo real | Problema |
|-------|-------------|---------|
| Vago | `"resúmeme esto"` | ¿Para quién? ¿Qué largo? ¿Qué formato? |
| Sin rol | `"escribe un email"` | ¿Qué tono? ¿De quién? ¿A quién? |
| Sin formato | `"analiza este reporte"` | Recibes un ensayo cuando querías una tabla |
| Sin límite | `"dame ideas"` | Recibes 20 ideas mediocres en lugar de 5 buenas |

> [!tip] Conecta con
> Ver [[bloque_01_que_es_un_LLM#El efecto "Lost in the Middle"|Lost in the Middle]] — Claude necesita instrucciones claras porque no adivina intención.

---

## 2. Anatomía de un buen prompt — El framework RTFC (5 min) {#Estructura del prompt}

Todo prompt de calidad tiene 4 capas. No todas son siempre necesarias, pero conocerlas te da control total.

```
R — Rol        ¿Quién eres?
T — Tarea      ¿Qué hacer exactamente?
F — Formato    ¿Cómo quiero la respuesta?
C — Contexto   ¿Qué información necesitas?
```

### El prompt sin RTFC vs con RTFC

**❌ Sin framework:**
```
resúmeme el reporte de ventas
```

**✅ Con RTFC:**
```
[R] Actúa como analista de ventas senior.
[T] Resume el siguiente reporte identificando: 3 hallazgos clave, 
    1 alerta crítica y 2 recomendaciones accionables.
[F] Usa este formato exacto:
    ## Hallazgos clave
    ## Alerta
    ## Recomendaciones
[C] El reporte es para presentar al Director Comercial mañana. 
    Audiencia no técnica. Tono ejecutivo.

--- REPORTE ---
[pega el reporte aquí]
```

**Diferencia de calidad: 10x**

---

## 3. El Rol — ¿para qué sirve realmente? (3 min) {#Instrucciones claras}

Asignar un rol **ajusta el registro y el vocabulario** de Claude.

### Cuándo SÍ usar rol
- Tareas creativas o de escritura
- Cuando necesitas un tono específico
- Cuando el dominio tiene jerga propia (legal, médico, técnico)

### Cuándo NO ayuda (y puede dañar)
- Preguntas factuales directas
- Datos o cifras que requieren precisión
- *Estudio ACL 2024: los roles degradan la precisión en tareas de alto detalle factual*

### Ejemplos de roles útiles para el equipo

| Rol | Cuándo usarlo |
|-----|--------------|
| `Analista financiero senior` | Reportes, presupuestos, KPIs |
| `Redactor corporativo bilingüe` | Comunicados, emails formales |
| `Facilitador de reuniones` | Actas, planes de acción |
| `Consultor de procesos` | Diagnóstico de problemas, flujos |
| `Editor de contenido` | Revisión y mejora de textos |

---

## 4. Zero-shot vs Few-shot (3 min)

### Zero-shot — solo instrucción, sin ejemplos
Funciona para tareas simples y directas.

```
Clasifica este email como: URGENTE, NORMAL o INFORMATIVO.
Email: "necesitamos la propuesta para el lunes o perdemos al cliente"
```

### Few-shot — instrucción + ejemplos
Funciona para tareas con formato específico o matiz difícil de describir.

```
Clasifica emails según estos ejemplos:

Email: "la reunión del jueves sigue en pie" → INFORMATIVO
Email: "el servidor cayó y producción está parada" → URGENTE  
Email: "adjunto el reporte mensual" → NORMAL

Ahora clasifica este:
Email: "necesitamos la propuesta para el lunes o perdemos al cliente"
```

**Regla:** Si el output tiene un patrón específico que es difícil de describir con palabras, usa 2-3 ejemplos.

---

## 5. Chain of Thought — hazlo pensar (2 min)

Para problemas complejos, dile a Claude que piense paso a paso antes de responder.

**Sin CoT:**
```
¿Deberíamos cambiar nuestro proveedor de logística?
```

**Con CoT:**
```
Analiza si debemos cambiar de proveedor de logística. 
Piensa paso a paso:
1. Qué criterios son relevantes
2. Qué información tenemos y qué falta
3. Cuáles son los riesgos de cambiar vs. quedarnos
4. Conclusión recomendada

Contexto: [info del proveedor actual]
```

> [!warning] Importante
> Chain of Thought funciona mejor en modelos grandes (Claude Sonnet/Opus). En modelos pequeños el beneficio es mínimo.

---

## 6. Control de formato (2 min)

Nunca dejes que Claude decida el formato. Especifícalo siempre.

### Formatos útiles para el equipo

| Necesitas | Pide esto |
|-----------|----------|
| Lista de acciones | `Formato: lista numerada. Cada ítem: verbo + responsable + fecha` |
| Comparación | `Formato: tabla con columnas [Criterio / Opción A / Opción B]` |
| Email | `Formato: asunto en negrita, cuerpo en 3 párrafos, firma estándar` |
| Resumen ejecutivo | `Máximo 150 palabras. Párrafo único. Sin bullet points.` |
| Datos estructurados | `Responde en JSON con campos: título, prioridad, responsable, fecha` |

### El poder de las etiquetas XML (específico de Claude)

Claude fue entrenado especialmente para entender etiquetas XML. Úsalas para separar secciones:

```xml
<contexto>
Soy gerente de operaciones en empresa manufacturera de 200 empleados.
</contexto>

<tarea>
Escribe un plan de comunicación interna para anunciar el nuevo sistema de ERP.
</tarea>

<restricciones>
- Tono: profesional pero cercano
- Largo: máximo 300 palabras
- Incluir: fecha de lanzamiento (15 mayo), canales (email + reunión)
</restricciones>
```

---

## 7. Antes y después — casos reales (2 min)

### Caso 1: Resumen de documento

❌ **Antes:** `"resume esto"`

✅ **Después:**
```
Resume el documento adjunto en máximo 5 puntos clave. 
Cada punto: 1 oración. 
Empieza cada punto con un verbo en infinitivo.
Audiencia: directivos sin tiempo. Tono: ejecutivo.
```

---

### Caso 2: Email difícil a cliente

❌ **Antes:** `"ayúdame a escribir un email al cliente que se quejó"`

✅ **Después:**
```
Actúa como gerente de servicio al cliente con tono profesional y empático.
Escribe un email de respuesta a un cliente que reportó entrega tardía.

Contexto: el pedido llegó 3 días tarde por falla del carrier (no nuestra falta).
El cliente es frecuente (5 años con nosotros).

Estructura:
1. Reconocer la experiencia del cliente (sin asumir culpa directa)
2. Explicar brevemente qué pasó
3. Ofrecer compensación: 10% descuento próximo pedido
4. Cierre cálido y reafirmación del compromiso

Tono: profesional, humano, no robótico. Máximo 200 palabras.
```

---

### Caso 3: Reunión → Plan de acción

❌ **Antes:** `"hazme el acta de la reunión"`

✅ **Después:**
```
A partir de estas notas de reunión, extrae SOLO los compromisos concretos.

Formato de salida:
| Acción | Responsable | Fecha límite | Prioridad |

Si algún dato no está en las notas, escribe "No definido".
No incluyas discusiones ni contexto. Solo compromisos.

--- NOTAS ---
[pega tus notas]
```

---

## 🔑 Takeaways del Bloque 2

1. Un prompt vago = resultado vago → **sé específico**
2. Usa **RTFC**: Rol, Tarea, Formato, Contexto
3. Output con patrón específico → **few-shot** (2-3 ejemplos)
4. Problema complejo → **"piensa paso a paso"**
5. **Siempre especifica el formato** de salida
6. Etiquetas **XML son tu mejor aliado** en Claude
7. Prompts guardados en [[bloque_05_obsidian_cerebro_claude|Obsidian]] = reutilizables al instante

---

## 📎 Plantilla base reutilizable → [[plantilla_prompt_base]]

```
[ROL] Actúa como ___

[TAREA] Tu objetivo es ___

[CONTEXTO] 
- Audiencia: ___
- Situación: ___

[FORMATO]
- Estructura: ___
- Longitud máxima: ___
- Tono: ___

[RESTRICCIONES]
- No incluir: ___
- Evitar: ___

--- INSUMO ---
[pega aquí el contenido a procesar]
```

---

> [!info] Navegación
> ← [[bloque_01_que_es_un_LLM]] | Siguiente → [[bloque_03_optimizacion_tokens]]

*Fuentes: Anthropic Prompt Engineering Docs, ACL 2024 Persona Study, IBM Think, Google Cloud Prompting Guide, Stanford CoT Paper (2201.11903)*
