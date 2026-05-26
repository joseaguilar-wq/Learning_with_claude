---
tags:
  - capacitacion
  - bloque
  - obsidian
  - segundo-cerebro
  - vault
  - memoria
  - plugins
bloque: 5
duracion: 15 min
previo: "[[bloque_04_flujos_trabajo_ia]]"
siguiente: "[[00_MOC_Capacitacion_IA]]"
relacionado:
  - "[[plantilla_prompt_base]]"
  - "[[plantilla_CLAUDE]]"
  - "[[bloque_03_optimizacion_tokens]]"
  - "[[Construyendo con IA/Sistemas RAG]]"
  - "[[Construyendo con IA/Indice de agentes IA]]"
---

# Bloque 5 — Obsidian como Cerebro de Claude

> [!info] Navegación
> ← [[bloque_04_flujos_trabajo_ia]] | Volver al mapa → [[00_MOC_Capacitacion_IA]]

**Duración:** 15 minutos  
**Objetivo:** Que el equipo construya un vault en Obsidian que funcione como memoria persistente y biblioteca de prompts para Claude.

---

## 🎯 Idea central

> Claude olvida todo al cerrar la conversación. Obsidian recuerda todo. Juntos, no pierdes nada.

---

## 1. ¿Por qué Obsidian? (2 min)

### El problema que resuelve

Claude no tiene memoria entre sesiones. Cada vez que abres una conversación nueva:
- Vuelves a explicar quién eres
- Vuelves a describir el proyecto
- Vuelves a copiar el contexto
- Vuelves a buscar el prompt que funcionó la semana pasada

**Eso es tiempo desperdiciado. Y tokens desperdiciados.**

> [!tip] Conecta con
> [[bloque_03_optimizacion_tokens#Técnica 4 — Nueva conversación a tiempo|Técnica 4 del Bloque 3]] — notas externas para reiniciar conversaciones sin perder contexto.

### Por qué Obsidian específicamente

| Característica | Ventaja para IA |
|---------------|----------------|
| Todo es Markdown | Claude lee y escribe Markdown nativo |
| Archivos locales | Tú controlas qué pasa al contexto |
| `[[wiki links]]` | Red de conocimiento que Claude puede navegar |
| Sin base de datos | Transparente, portable, sin vendor lock-in |
| Gratuito | Sin costo extra para el equipo |

---

## 2. La estructura del vault (3 min)

### Arquitectura recomendada

```
📁 Tu Vault
├── 📄 CLAUDE.md              ← memoria de Claude (raíz)
├── 📁 Clientes/
│   └── 📁 Cliente_X/
│       ├── Perfil.md
│       ├── Comunicaciones/
│       └── Proyectos/
├── 📁 Proyectos/
│   ├── Activos/
│   └── Archivo/
├── 📁 Prompts/               ← biblioteca de prompts
│   ├── Redaccion/
│   ├── Analisis/
│   └── Procesos/
├── 📁 Investigacion/
├── 📁 Borradores_IA/         ← outputs antes de revisar
└── 📁 Plantillas/
```

### Reglas de oro para el vault

1. **Notas atómicas** — una idea por nota (Claude cita mejor)
2. **Frontmatter consistente** — mismas etiquetas en todos los archivos
3. **Links en lugar de copias** — `[[Nota]]` en vez de pegar contenido repetido
4. **`/Borradores_IA/`** — todo output de IA va aquí primero, tú lo apruebas
5. **Actualiza `CLAUDE.md` cada semana** — es la memoria activa

---

## 3. CLAUDE.md — el archivo más importante (3 min)

### ¿Qué es?

Un archivo en la raíz del vault que le dice a Claude todo lo que necesita saber antes de empezar a trabajar contigo.

**Claude lo lee automáticamente** al inicio de cada sesión cuando trabajas desde tu vault.

### Estructura mínima viable

```markdown
# Contexto para Claude — [Tu nombre]

## Mi rol
[Tu cargo y empresa en 1-2 oraciones]

## Proyectos activos
- Proyecto X → deadline: 15 mayo
- Proyecto Y → en espera de cliente

## Estilo de comunicación
- Tono: profesional pero directo
- Formato: listas cuando sea posible
- Longitud: conciso, máximo 3 párrafos para emails

## Estructura del vault
- /Clientes/ → perfiles y comunicaciones
- /Prompts/ → plantillas reutilizables
- /Borradores_IA/ → outputs pendientes de revisión

## Esta semana
[Actualiza cada lunes — máximo 5 líneas]

## Reglas para Claude
- Guarda outputs en /Borradores_IA/ primero
- No reorganices carpetas
- Etiqueta nuevas notas con #ia-generado
```

> [!tip] Plantilla completa
> Ver [[plantilla_CLAUDE]] para la versión lista para copiar y personalizar.

---

## 4. El flujo central: nota → Claude → resultado → vault (3 min)

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  1. OBSIDIAN          2. CLAUDE           3. VAULT  │
│                                                     │
│  Abres nota      →   Pegas contexto  →   Guardas   │
│  del cliente         + prompt RTFC       resultado  │
│                       ↓                  en         │
│  Copias info     ←   Respuesta       →  /Borradores │
│  relevante           de calidad         /IA/        │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### Ejemplo real — Email de status semanal

```
Lunes 9am:
1. Abres /Clientes/Cliente_X/Actualizaciones/2026-04-15.md
2. Tienes tus notas de la semana ahí
3. Copias esas notas + tu prompt de email (de /Prompts/Redaccion/)
4. Pegas en Claude
5. Claude redacta el email con tu voz y contexto
6. Guardas en /Borradores_IA/Email_Status_2026-04-15.md
7. Revisas, personalizas, envías
8. Mueves a /Clientes/Cliente_X/Enviados/

Total: 8 min vs 30 min manual
```

### Por qué funciona mejor que copiar y pegar historial

| Método | Tokens usados | Calidad |
|--------|-------------|---------|
| Pegar historial completo de conversación | ~15,000 | ⚠️ Baja por context rot |
| Pegar nota curada de Obsidian | ~800 | ✅ Alta por contexto limpio |

> [!tip] Conecta con
> [[bloque_03_optimizacion_tokens#1. Context Rot — el enemigo silencioso|Context rot del Bloque 3]] — nota curada = contexto limpio = mejor calidad.

---

## 5. Plugins esenciales (2 min)

Solo 3 para empezar. No instales más hasta dominar estos.

### Plugin 1 — Templater

Crea plantillas dinámicas que se auto-completan.

```markdown
<%* 
let proyecto = await tp.system.prompt("¿Proyecto?")
let cliente = await tp.system.prompt("¿Cliente?")
-%>
---
fecha: <% tp.date.now("YYYY-MM-DD") %>
proyecto: <% proyecto %>
cliente: <% cliente %>
tags: #borrador #ia-generado
---

# Borrador: <% tp.file.title %>
```

Al crear una nota nueva con este template, Obsidian te pregunta el proyecto y cliente, y llena los datos automáticamente.

---

### Plugin 2 — QuickAdd

Dispara macros con un atajo de teclado.

**Macro útil: "Guardar output de IA"**
- `Cmd+Shift+S`
- Crea nota en `/Borradores_IA/`
- Fecha automática en el nombre
- Tags: `#ia-generado #pendiente-revision`

---

### Plugin 3 — Dataview

Consulta tu vault antes de ir a Claude.

```dataview
TABLE cliente, deadline, status
FROM "Proyectos/Activos"
WHERE status != "completado"
SORT deadline ASC
```

Ejecutas esto → copias la tabla → la pegas como contexto en Claude → preguntas: *"¿Qué proyecto debo priorizar esta semana?"*

Claude responde con datos reales de tu vault, no suposiciones.

---

## 6. La biblioteca de prompts (2 min)

### Por qué guardar prompts en Obsidian

Un buen prompt tomó tiempo construirlo. Si no lo guardas, lo pierdes.  
Tu biblioteca crece y mejora con el tiempo.  
El equipo puede compartirla.

### Formato de nota de prompt

```markdown
---
tipo: prompt
categoria: redaccion
tags: #email #cliente #formal
creado: 2026-04-15
veces-usado: 0
---

# Prompt: Email de respuesta a queja

## Cuándo usar
Cuando un cliente reporta problema con entrega, servicio o producto.

## El prompt
[ROL] Redactor corporativo con tono profesional y empático.
[TAREA] Escribe email de respuesta a queja de cliente.
[CONTEXTO]
- Cliente: ___
- Problema reportado: ___
- Causa real: ___
- Compensación disponible: ___
[FORMATO] 3 párrafos. Máximo 150 palabras. Sin jerga técnica.

## Resultados anteriores
- [[Email_Cliente_X_2026-03-10]] → funcionó bien, tono muy positivo
- [[Email_Cliente_Y_2026-02-28]] → ajustar: fue muy largo

## Notas de mejora
Agregar siempre fecha concreta de resolución en párrafo 2.
```

> [!tip] Conecta con
> [[plantilla_prompt_base]] — versión base RTFC para cualquier tarea.

---

## 🔑 Takeaways del Bloque 5

1. **Claude olvida. Obsidian recuerda.** — úsalos juntos
2. **`CLAUDE.md`** = memoria activa de Claude en tu vault
3. **Nota curada (800 tokens) > historial completo (15,000 tokens)** en calidad
4. **Flujo: nota → Claude → borrador → revisión → vault**
5. **3 plugins para empezar**: Templater, QuickAdd, Dataview
6. **Biblioteca de prompts** = activo que crece con el equipo

---

## 💡 Demo en vivo (15 min de clase → 5 min de demo)

**Muestra esto en pantalla:**

1. Vault real con estructura básica ya creada
2. `CLAUDE.md` con info del proyecto actual
3. Una nota de cliente con contexto de la semana
4. Copias nota + prompt → pegas en Claude
5. Claude responde con email listo
6. Guardas en `/Borradores_IA/`
7. Graph view de Obsidian → muestra el cerebro conectado

**Pregunta al equipo:** ¿cuánto tiempo gastan cada semana re-explicando contexto a la IA?

---

## 🚀 Setup en 15 minutos (tarea post-clase)

```
□ Instalar Obsidian (gratis en obsidian.md)
□ Crear vault nuevo
□ Crear carpetas: /Clientes /Proyectos /Prompts /Borradores_IA
□ Copiar y llenar plantilla CLAUDE.md → [[plantilla_CLAUDE_md]]
□ Crear 3 prompts de tus tareas más repetitivas
□ Instalar Templater y QuickAdd
□ Primera sesión: pegar CLAUDE.md en Claude y preguntar por tu proyecto
```

---

> [!info] Navegación
> ← [[bloque_04_flujos_trabajo_ia]] | Volver al mapa → [[00_MOC_Capacitacion_IA]]

> [!tip] Conecta tu vault con un agente RAG
> Un [[Construyendo con IA/Sistemas RAG|sistema RAG]] puede consultar directamente tu vault de Obsidian, eliminando el paso manual de copiar contexto. Es el siguiente nivel del flujo nota→Claude→vault.

*Fuentes: MindStudio "Build AI Second Brain with Obsidian" (2026), Medium "Obsidian + Claude Code" (2026), DEV Community "Claude Code Inside Obsidian" (2026), Obsidian Dataview Docs, QuickAdd Guide, Templater Plugin Docs*
