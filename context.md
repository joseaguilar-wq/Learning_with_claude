# PROYECTO: Capacitación IA — Mejores Prácticas

## Metadatos
- **Responsable:** Nexus GO (nexus.go@grupo-ortiz.com)
- **Última actualización:** 2026-04-15
- **Fase actual:** Contenido completo ✅ → Pendiente: Slides + Ejercicio práctico

---

## Objetivo
Capacitación magistral de ~1h 20min para el equipo de Grupo Ortiz.
Reducir consumo de tokens, mejorar calidad de outputs, construir cerebro en Obsidian.

## Audiencia
Compañeros del equipo. Usan IA variada (Claude, ChatGPT, otras). Consumos altos. Resultados precarios.

---

## Reglas de sesión con Claude
- Leer `caveman.md` antes de responder → responder en modo cavernícola (español)
- Ruta: `/sessions/lucid-confident-ride/mnt/Learning_with_claude/caveman.md`
- Actualizar este archivo al final de cada sesión de trabajo

---

## Estructura final de la clase — v2 DEFINITIVA

| # | Bloque | Duración | Archivo | Estado |
|---|--------|----------|---------|--------|
| 1 | ¿Qué es un LLM? | 10 min | `bloque_01_que_es_un_LLM.md` | ✅ |
| 2 | Prompt Engineering | 20 min | `bloque_02_prompt_engineering.md` | ✅ |
| 3 | Optimización de tokens | 15 min | `bloque_03_optimizacion_tokens.md` | ✅ |
| 4 | Flujos de trabajo con IA | 10 min | `bloque_04_flujos_trabajo_ia.md` | ✅ |
| 5 | Obsidian como cerebro de Claude | 15 min | `bloque_05_obsidian_cerebro_claude.md` | ✅ |
| — | Q&A + demo viva | 10 min | — | — |
| **Total** | | **~1h 20min** | | |

---

## Todos los archivos del vault

### Bloques de contenido
- `bloque_01_que_es_un_LLM.md` — tokens, context window, Lost in the Middle, alucinaciones
- `bloque_02_prompt_engineering.md` — framework RTFC, zero/few-shot, CoT, XML, casos reales
- `bloque_03_optimizacion_tokens.md` — context rot, caveman prompts, chunking, regla 15/20
- `bloque_04_flujos_trabajo_ia.md` — árbol decisión, 3 patrones, HITL, refinamiento iterativo
- `bloque_05_obsidian_cerebro_claude.md` — vault, CLAUDE.md, flujo nota→Claude→vault, plugins

### Plantillas
- `plantilla_prompt_base.md` — template RTFC en 3 versiones (completa, rápida, XML)
- `plantilla_CLAUDE_md.md` — template de memoria persistente para vault de Obsidian

### Navegación
- `00_MOC_Capacitacion_IA.md` — nodo raíz del vault, tabla de bloques, índice de conceptos

---

## Convenciones del vault (Obsidian)
- Frontmatter YAML en todos los archivos (tags, bloque, previo, siguiente, relacionado)
- `[[wiki links]]` bidireccionales entre todos los bloques
- Callouts: `[!info]` navegación, `[!tip]` conexiones cruzadas, `[!warning]` alertas
- Nodo raíz: `00_MOC_Capacitacion_IA.md`
- Tags principales: `capacitacion`, `bloque`, `MOC`, `plantilla`

---

## Pendiente para próxima sesión

### 1. Slides de presentación
- Formato: PowerPoint (.pptx)
- 1 slide por concepto clave de cada bloque
- Incluir visuales para: token table, context rot curve, RTFC framework, vault structure
- Demo slides con capturas de Obsidian graph view

### 2. Ejercicio práctico
- Actividad de 5 min que el equipo hace durante la clase
- Idea: cada quien reescribe un prompt real de su trabajo usando framework RTFC
- Comparar antes/después en vivo

### 3. Checklist de recursos post-clase
- Links a descargar Obsidian
- Vault starter (carpetas + CLAUDE.md + plantillas) para descargar
- Referencia rápida de los frameworks

---

## Ideas anotadas / decisiones tomadas
- Caveman.md como ejemplo vivo de optimización de tokens durante la clase SIEMPRE USAR
- Mostrar graph view de Obsidian al final del bloque 5 como demo visual del "cerebro"
- Context rot graph (tabla de precisión vs tokens) es el slide más impactante del bloque 3
- Framework RTFC es el concepto ancla de todo el curso → reforzar en múltiples bloques
