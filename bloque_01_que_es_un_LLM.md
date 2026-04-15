---
tags: [capacitacion, bloque, fundamentos, LLM, tokens, context-window]
bloque: 1
duracion: 10 min
previo: "[[00_MOC_Capacitacion_IA]]"
siguiente: "[[bloque_02_prompt_engineering]]"
relacionado: ["[[bloque_03_optimizacion_tokens]]", "[[bloque_05_obsidian_cerebro_claude]]"]
---

# Bloque 1 — ¿Qué es un LLM y cómo piensa?

> [!info] Navegación
> ← [[00_MOC_Capacitacion_IA]] | Siguiente → [[bloque_02_prompt_engineering]]

**Duración:** 10 minutos  
**Objetivo:** Que el equipo entienda qué hace Claude por dentro, sin tecnicismos.

---

## 🎯 Idea central

> Claude no piensa. Predice.

Todo lo demás en este bloque explica esa frase.

---

## 1. ¿Qué es un LLM? (2 min)

**LLM = Large Language Model = Modelo de Lenguaje Grande**

### La analogía más honesta
Imagina que alguien leyó **todo el internet, todos los libros y todos los artículos del mundo**.  
No los entendió como tú. Los memorizó como **patrones**:

> "Cuando alguien escribe *'El problema es que…'*, normalmente después viene una explicación de un obstáculo."

> "Cuando alguien escribe *'Estimado cliente'*, lo que sigue suele ser una carta formal."

Claude aprendió billones de estos patrones. Cuando tú escribes algo, predice cuál es la palabra más probable que debería seguir. Luego la siguiente. Y la siguiente. Hasta completar tu respuesta.

### La analogía del autocomplete
Tu teléfono tiene autocomplete. Claude es un autocomplete **entrenado con toda la literatura humana**, con miles de veces más sofisticación.

### Lo que NO es Claude
- ❌ No es un buscador (no "busca" en Google)
- ❌ No "recuerda" tus conversaciones anteriores
- ❌ No "piensa" como tú
- ❌ No tiene certeza: **estima probabilidades**

> [!tip] Conecta con
> Esto explica por qué los [[bloque_02_prompt_engineering#Instrucciones claras|prompts claros]] importan tanto: Claude no adivina tu intención, sigue patrones del texto que le das.

---

## 2. ¿Qué son los tokens? (3 min)

**Token = unidad mínima de texto que procesa Claude**

No es exactamente una palabra. Es un fragmento de texto.

### Ejemplos concretos

| Texto | Tokens aprox. |
|-------|--------------|
| "Hola" | 1 token |
| "conversación" | 2 tokens |
| "El zorro marrón salta" | 5 tokens |
| Un párrafo de 100 palabras | ~130 tokens |
| Una página de Word | ~500 tokens |
| Un documento de 20 páginas | ~10,000 tokens |
| Una novela completa | ~100,000 tokens |

### Por qué importa
Cada token **cuesta dinero y ocupa espacio de memoria**.

- Tokens que envías (tu pregunta) = **tokens de entrada**
- Tokens que recibes (la respuesta) = **tokens de salida** ← cuestan más

### El problema real del equipo
Si mandas 10 mensajes con 500 tokens cada uno en una conversación larga,  
Claude lleva 5,000 tokens de contexto acumulado.  
Si el 60% es relleno ("gracias", "ok", "ahora dime"), estás **pagando por ruido**.

> [!warning] Profundiza aquí
> Ver [[bloque_03_optimizacion_tokens]] para técnicas concretas de reducción.

---

## 3. El context window — ventana de contexto (2 min)

**Context window = la memoria de trabajo de Claude**

Claude no recuerda conversaciones pasadas.  
Solo ve lo que está **dentro de la ventana actual**.

### Analogía del escritorio
Imagina que tienes un escritorio. Solo puedes trabajar con lo que está **sobre el escritorio ahora mismo**. Lo que quedó en cajones (otras conversaciones) no existe para ti en este momento.

### Tamaños actuales (2026)

| Modelo | Ventana | Equivale a |
|--------|---------|-----------|
| Claude Sonnet 4.6 | 1,000,000 tokens | ~3,000 páginas |
| GPT-5 | 400,000 tokens | ~1,200 páginas |
| Gemini 2.5 Pro | 1,000,000 tokens | ~3,000 páginas |

### ¿Problema resuelto entonces?
**No.** El tamaño ya no es la limitación. El problema es **qué metes** en esa ventana.

> Meter basura en 3,000 páginas produce respuestas malas en 3,000 páginas.  
> **Calidad del contexto > Cantidad del contexto.**

> [!tip] Solución en Obsidian
> [[bloque_05_obsidian_cerebro_claude]] muestra cómo construir un vault que inyecta solo contexto relevante, no todo tu historial.

---

## 4. El efecto "Lost in the Middle" (2 min)

### Hallazgo clave — Stanford 2023

Claude presta más atención al **inicio y final** de tu prompt.  
Lo que pones en el **medio** tiende a perderse.

```
[Inicio del prompt]     ← Claude lee bien aquí ✅
...
...
[Medio del prompt]      ← Claude lee mal aquí ⚠️
...
...
[Final del prompt]      ← Claude lee bien aquí ✅
```

### Implicación práctica
Si tienes una instrucción crítica, **ponla al inicio o al final**.  
Nunca enterrada en el medio de un texto largo.

> [!tip] Ver en acción
> [[bloque_02_prompt_engineering#Estructura del prompt|La anatomía del prompt]] en el Bloque 2 aplica esto directamente.

---

## 5. Alucinaciones — por qué se equivoca (1 min)

Claude no "sabe" si lo que dice es verdad.  
**Predice qué texto suena correcto**, no qué texto es correcto.

Cuando no tiene suficiente información, **inventa con confianza**.  
Esto se llama **alucinación**.

### Regla de oro
> Si Claude te da un dato importante (fecha, cifra, nombre, ley),  
> **verifica siempre antes de usarlo**.

---

## 🔑 Takeaways del Bloque 1

1. Claude **predice texto**, no piensa
2. Los **[[bloque_03_optimizacion_tokens|tokens]]** son la unidad de costo y de memoria
3. La **context window** es su memoria de trabajo (grande, pero no infinita en calidad)
4. Lo importante no va al **medio** del prompt → [[bloque_02_prompt_engineering]]
5. Puede **alucinar**: siempre verifica datos críticos

---

## 💡 Demo sugerida (en vivo)

1. Abre `claude.ai`
2. Prompt malo: `"dime cosas sobre IA"`
3. Prompt bueno:
```
Actúa como experto en logística. Explica en 3 puntos cómo la IA puede 
reducir costos de inventario en una empresa manufacturera mediana. 
Formato: lista numerada, máximo 2 oraciones por punto.
```
4. Compara la diferencia de calidad → abre el debate para [[bloque_02_prompt_engineering]]

---

> [!info] Navegación
> ← [[00_MOC_Capacitacion_IA]] | Siguiente → [[bloque_02_prompt_engineering]]

*Fuentes: IBM Think, AWS ML Blog, Stanford "Lost in the Middle" (2023), Anthropic Docs, SiliconData 2026*
