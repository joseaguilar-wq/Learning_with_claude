# 🤖 Learning with Claude
### Master Guide del Proyecto

> Programa de formación práctica para integrar Claude y LLMs en flujos de trabajo reales —  
> de la teoría a los 100+ agentes desplegables.

Desarrollado por **Nexus GO** para los equipos de **Grupo Ortiz**.  
Capacitación magistral de **~1h 20min** + biblioteca operativa permanente.

---

## Punto de entrada recomendado

> **→ Abre [`00_MOC_Capacitacion_IA.md`](00_MOC_Capacitacion_IA.md) para navegar el vault desde Obsidian.**

El MOC es el nodo raíz con el mapa visual de todos los bloques y recursos. Este README es la vista desde fuera del vault (GitHub, editor de texto). Ambos conectan a todo.

---

## ¿Qué hay aquí?

| Sección | Qué encontrarás |
|---------|-----------------|
| **Bloques de formación** | 5 módulos estructurados para aprender a usar Claude con eficiencia real |
| **Plantillas** | Archivos listos para copiar y usar desde el primer día |
| **Construyendo con IA** | Agentes, RAG, multi-agente, voz — todo para desplegar en tu negocio |
| **Metadatos del proyecto** | Estado, convenciones, decisiones tomadas |

---

## Los 5 bloques de formación

Recorre los bloques en orden — cada uno construye sobre el anterior.

### [Bloque 1 — ¿Qué es un LLM?](bloque_01_que_es_un_LLM.md) `~10 min`
La base conceptual. Entiende cómo piensa Claude antes de darle instrucciones.
- Qué son los tokens y por qué importan para tus costos
- El context window y sus límites reales
- El efecto **Lost in the Middle** (Stanford 2023) — por qué Claude "olvida" lo del medio
- Alucinaciones: qué son, por qué pasan, cómo reducirlas

### [Bloque 2 — Prompt Engineering](bloque_02_prompt_engineering.md) `~20 min`
El framework central del curso. Todo lo demás depende de esto.
- El **framework RTFC** (Rol · Tarea · Formato · Contexto)
- Zero-shot vs Few-shot — cuándo usar cada uno
- Chain of Thought (CoT) — cómo hacer que Claude razone paso a paso
- XML para Claude — por qué funciona mejor que el texto libre
- Casos reales con antes/después medibles

### [Bloque 3 — Optimización de tokens](bloque_03_optimizacion_tokens.md) `~15 min`
El más impactante en términos de ahorro. Equipos han pasado de $1,500/mes a $300/mes.
- **Context rot** — precisión cae 60–75% después de 64K tokens (Chroma Research 2025)
- **Caveman mode** — compresión extrema, −60–85% de tokens → ver [`caveman.md`](caveman.md)
- Chunking de documentos — procesar en partes, no todo junto
- La regla 15/20 — cuándo reiniciar una conversación
- ROI completo con datos reales de equipos

### [Bloque 4 — Flujos de trabajo con IA](bloque_04_flujos_trabajo_ia.md) `~10 min`
Cómo integrar IA en el trabajo diario sin crear más fricción de la que resuelve.
- Árbol de decisión: cuándo usar IA y cuándo no
- 3 patrones universales: Research→Draft, Reuniones→Acciones, Datos→Análisis
- HITL (Human-in-the-Loop) vs automatización total
- Refinamiento iterativo — cómo mejorar outputs sin empezar de cero

### [Bloque 5 — Obsidian como cerebro de Claude](bloque_05_obsidian_cerebro_claude.md) `~15 min`
Cómo construir memoria persistente para que Claude nunca olvide el contexto de tu equipo.
- El vault de Obsidian como sistema de memoria externo
- El archivo **CLAUDE.md** — 800 tokens vs 15,000 tokens de historial
- Flujo nota → prompt → resultado → vault
- Plugins esenciales: Templater, QuickAdd, Dataview
- Arquitectura del vault para equipos

---

## Plantillas listas para usar

### [plantilla_prompt_base.md](plantilla_prompt_base.md)
Template RTFC en 3 versiones para cualquier consulta:
- **Versión completa** — para tareas complejas o nuevas
- **Versión rápida** — para el día a día
- **Versión XML** — para Claude (mejor estructura = mejor resultado)

### [plantilla_CLAUDE_md.md](plantilla_CLAUDE_md.md)
Template del archivo de memoria persistente para tu vault de Obsidian. Cópialo, personalízalo con el contexto de tu equipo y úsalo en cada sesión con Claude.

---

## Construyendo con IA

La sección práctica del proyecto. Todo lo que necesitas para pasar de aprender a desplegar.

### [Índice de agentes IA](Construyendo%20con%20IA/Indice%20de%20agentes%20IA.md)
**+100 agentes listos para usar**, organizados por categoría — todos gratuitos, todos probados. El punto de entrada para cualquier implementación práctica.

### [Construye con estructura](Construyendo%20con%20IA/Construye%20con%20estructura.md)
El framework maestro para pasar de una idea a una app real. Estructura de prompt que funciona para cualquier tipo de proyecto con IA.

### [Sistemas RAG](Construyendo%20con%20IA/Sistemas%20RAG.md)
IA que consulta tus propios documentos sin alucinar. Para construir asistentes sobre bases de conocimiento internas — contratos, manuales, políticas, reportes.

### [Equipos Multi-agente](Construyendo%20con%20IA/Equipos%20Multi-agente.md)
Arquitecturas donde múltiples agentes especializados colaboran — uno investiga, otro redacta, otro revisa. Para tareas complejas que superan a un solo modelo.

### [Agentes de Voz](Construyendo%20con%20IA/Agentes%20de%20Voz.md)
Soporte 24/7 por voz integrado a tu operación. Casos de uso, plataformas y arquitecturas recomendadas.

### [Prompts para Code](Construyendo%20con%20IA/Prompts%20para%20Code.md)
Prompts listos para usar con **Claude Code** — el CLI de Anthropic. Para automatizar tareas de desarrollo, revisiones de código y generación de scripts.

### [AI Consultant Agent](Construyendo%20con%20IA/AI%20consultant%20Agent.md)
Agente consultor de negocios especializado. Ejemplo concreto de cómo construir un agente con rol definido, contexto de industria y outputs estructurados.

---

## Archivos de soporte

### [caveman.md](caveman.md)
El ejemplo vivo de optimización de tokens. Un prompt de sistema en modo cavernícola — máxima compresión, cero relleno. Se usa como demostración en clase durante el Bloque 3.

### [context.md](context.md)
La memoria del proyecto. Estado actual, decisiones tomadas, pendientes, convenciones del vault y reglas de sesión con Claude. **Actualizar al final de cada sesión de trabajo.**

### [De Cero a Experto con IA.gslides](De%20Cero%20a%20Experto%20con%20IA.gslides)
Presentación de Google Slides que acompaña la capacitación en vivo.

---

## El framework RTFC

El concepto ancla de todo el curso — reforzado en cada bloque:

```
ROL      → Quién es Claude en esta tarea
TAREA    → Qué debe hacer exactamente
FORMATO  → Cómo debe entregar el resultado
CONTEXTO → Qué información necesita para hacerlo bien
```

Sin RTFC, los prompts son ruido. Con RTFC, son instrucciones ejecutables.  
Template listo en → [`plantilla_prompt_base.md`](plantilla_prompt_base.md)

---

## Resultados documentados

| Métrica | Antes | Después | Fuente |
|---------|-------|---------|--------|
| Costo mensual (equipo 10 personas) | ~$1,500 | ~$300 | Datos internos |
| Tokens con caveman mode | base | −60–85% | Anthropic docs |
| Precisión en contextos largos (+64K tokens) | base | −60–75% sin optimizar | Chroma Research 2025 |
| Tiempo neto ahorrado por persona | — | 30–50% | CIO 2025 |
| Calidad nota curada vs historial completo | 800 tokens | vs 15,000 tokens | Bloque 5 |

---

## Tecnologías

- **[Claude](https://claude.ai)** (Anthropic) — LLM principal, Sonnet 4.6
- **[Obsidian](https://obsidian.md)** — Gestión del conocimiento y vault
- **[Claude Code](https://claude.ai/claude-code)** — CLI para automatización y desarrollo
- **Markdown + YAML frontmatter** — Formato portable para todo el contenido
- **Plugins Obsidian**: Templater · QuickAdd · Dataview

---

## Convenciones del vault

Para quien quiera contribuir o extender el proyecto:

- Frontmatter YAML en todos los archivos (`tags`, `bloque`, `previo`, `siguiente`, `relacionado`)
- `[[wiki links]]` bidireccionales entre bloques
- Callouts: `[!info]` navegación · `[!tip]` conexiones cruzadas · `[!warning]` alertas
- Nodo raíz: [`00_MOC_Capacitacion_IA.md`](00_MOC_Capacitacion_IA.md)
- Tags principales: `capacitacion` · `bloque` · `MOC` · `plantilla`
- Claude lee [`caveman.md`](caveman.md) antes de responder en sesiones de trabajo activas

---

## Estado del proyecto

| Entregable | Estado |
|------------|--------|
| Bloque 1 — ¿Qué es un LLM? | ✅ Completo |
| Bloque 2 — Prompt Engineering | ✅ Completo |
| Bloque 3 — Optimización de tokens | ✅ Completo |
| Bloque 4 — Flujos de trabajo | ✅ Completo |
| Bloque 5 — Obsidian como cerebro | ✅ Completo |
| Plantilla prompt base | ✅ Completo |
| Plantilla CLAUDE.md | ✅ Completo |
| Biblioteca de agentes (100+) | ✅ Completo |
| Slides de presentación | 🔄 En progreso |
| Ejercicio práctico para clase | ⏳ Pendiente |
| Checklist post-clase | ⏳ Pendiente |
| Vault starter descargable | ⏳ Pendiente |

---

## Cómo empezar

**En Obsidian:**
1. Archivo → Abrir vault → seleccionar esta carpeta
2. Abrir [`00_MOC_Capacitacion_IA.md`](00_MOC_Capacitacion_IA.md)
3. Seguir los bloques en orden (1 → 2 → 3 → 4 → 5)
4. Usar [`plantilla_prompt_base.md`](plantilla_prompt_base.md) para cualquier nueva consulta

**En GitHub / sin Obsidian:**
- Navega desde este README — todos los archivos están enlazados arriba
- El orden recomendado es el mismo: bloques 1 al 5, luego plantillas, luego "Construyendo con IA"

---

*Nexus GO × Grupo Ortiz · 2026 · Construido con [Claude Code](https://claude.ai/claude-code)*
