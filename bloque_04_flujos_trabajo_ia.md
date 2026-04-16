---
tags: [capacitacion, bloque, flujos-de-trabajo, productividad, automatizacion, HITL]
bloque: 4
duracion: 10 min
previo: "[[bloque_03_optimizacion_tokens]]"
siguiente: "[[bloque_05_obsidian_cerebro_claude]]"
relacionado: ["[[bloque_02_prompt_engineering]]", "[[bloque_05_obsidian_cerebro_claude]]", "[[plantilla_prompt_base]]", "[[Construyendo con IA/Indice de agentes IA]]", "[[Construyendo con IA/Equipos Multi-agente]]"]
---

# Bloque 4 — Flujos de Trabajo con IA

> [!info] Navegación
> ← [[bloque_03_optimizacion_tokens]] | Siguiente → [[bloque_05_obsidian_cerebro_claude]]

**Duración:** 10 minutos  
**Objetivo:** Que el equipo sepa *cuándo*, *cómo* y *hasta dónde* usar IA en su trabajo diario.

---

## 🎯 Idea central

> La IA no es un reemplazo. Es un acelerador con frenos. Saber cuándo frenar vale tanto como saber cuándo acelerar.

---

## 1. ¿Cuándo usar IA y cuándo NO? (3 min)

### Árbol de decisión rápido

```
¿La tarea es repetitiva y tiene patrones claros?
├── NO → ¿Requiere juicio sobre personas o relaciones?
│         ├── SÍ → Humano solamente ✋
│         └── NO → IA + revisión humana 🤝
└── SÍ → ¿El error tiene consecuencias graves?
          ├── SÍ → IA propone, humano aprueba (HITL) 🔍
          └── NO → Automatiza con auditoría periódica ⚡
```

### Úsala SÍ para
- Redactar primeros borradores (emails, reportes, propuestas)
- Resumir documentos largos
- Analizar datos y crear tablas comparativas
- Estructurar ideas y brainstorming inicial
- Estandarizar formatos repetitivos
- Extraer compromisos de reuniones

### NO la uses para
- ❌ Decisiones sobre personas (despidos, evaluaciones, sanciones)
- ❌ Compromisos contractuales o legales sin revisión
- ❌ Información en tiempo real (precios de mercado, noticias de hoy)
- ❌ Datos sensibles de clientes sin política de privacidad definida
- ❌ Comunicaciones estratégicas que definen la voz de marca

> [!warning] El dato incómodo
> 40% de las ganancias de productividad se pierden en retrabajo de errores de IA (CIO, 2025). Siempre presupuesta tiempo de revisión.

---

## 2. Los 3 patrones de flujo más útiles (4 min)

### Patrón A — Investigación → Borrador → Revisión → Publicar

Sirve para: reportes, propuestas, artículos, comunicados.

```
1. [IA]     Investiga y extrae puntos clave del tema
2. [IA]     Genera borrador con estructura definida
3. [Humano] Verifica datos, añade contexto estratégico
4. [IA]     Ajusta según feedback específico
5. [Humano] Aprueba y publica
```

**Tiempo manual:** 4–8 horas → **Con IA:** 1.5–3 horas

---

### Patrón B — Reunión → Notas → Acciones → Seguimiento

Sirve para: cualquier reunión de trabajo.

```
1. [Humano] Dirige la reunión
2. [IA]     Recibe las notas en bruto
3. [IA]     Extrae: decisiones + compromisos + responsables + fechas
4. [Humano] Revisa en 5 minutos, ajusta si falta algo
5. [IA]     Formatea y distribuye
```

**Tiempo manual:** 30 min/reunión → **Con IA:** 5 min/reunión

> [!tip] Plantilla lista
> Usa el Caso 3 de [[bloque_02_prompt_engineering#7. Antes y después — casos reales|Bloque 2]] para este flujo.

---

### Patrón C — Datos → Análisis → Reporte → Acción

Sirve para: cierres de mes, KPIs, comparativos de ventas.

```
1. [IA]     Limpia y estandariza los datos (CSV/tabla)
2. [IA]     Calcula métricas, identifica variaciones
3. [Humano] Interpreta las anomalías con contexto del negocio
4. [IA]     Redacta el reporte ejecutivo
5. [Humano] Revisa + añade conclusiones estratégicas
6. [IA]     Formatea y distribuye
```

**Tiempo manual:** 6–12 horas → **Con IA:** 2–4 horas

---

## 3. Humano en el loop (HITL) vs Automatización total (2 min)

| Criterio | HITL 🔍 | Automatización ⚡ |
|----------|---------|-----------------|
| Error tiene consecuencias legales | ✅ | ❌ |
| Afecta directamente a personas | ✅ | ❌ |
| Tarea es repetitiva y reversible | ❌ | ✅ |
| Cliente o proveedor lo verá | ✅ | ❌ |
| Es interno y de bajo riesgo | ❌ | ✅ |

### Arquitectura híbrida recomendada

```
Alto riesgo (legal, RRHH, finanzas >$5K)
→ IA genera → Humano revisa y aprueba → Ejecutar

Riesgo medio (reportes internos, emails de equipo)
→ IA genera y ejecuta → Humano audita 10% mensual

Bajo riesgo (categorización, agendas, formatos)
→ IA automatiza completamente → Auditoría trimestral
```

---

## 4. Refinamiento iterativo — cómo mejorar sin desperdiciar tokens (1 min)

No pidas todo de una sola vez. Itera en rondas específicas:

| Ronda | Enfoque | Calidad esperada |
|-------|---------|-----------------|
| 1 | Estructura y dirección general | 50% |
| 2 | Tono, longitud, secciones clave | 75% |
| 3 | Ajustes específicos de detalle | 85–90% |
| 4+ | Rendimientos decrecientes | Edita tú |

**Regla:** después de la ronda 3, es más rápido editar manualmente que seguir conversando.

> [!tip] Conecta con tokens
> Cada ronda extra = más historial acumulado. Ver [[bloque_03_optimizacion_tokens#4. Nueva conversación a tiempo|Técnica 4 del Bloque 3]].

---

## 5. Ahorros reales por rol (referencia rápida)

| Rol | Tarea más impactada | Ahorro estimado |
|-----|--------------------|----|
| Operaciones | Coordinación de proveedores y procesos | 30–40% |
| Finanzas | Cierre mensual, conciliaciones | 25–35% |
| RRHH | Reclutamiento (screening + agenda) | 30 hrs/mes |
| Marketing | Creación de contenido | 40–50% |
| Ventas | Propuestas y seguimiento | 30–40% |
| Legal | Revisión de contratos y research | 40–50% |

**Promedio real neto** (descontando retrabajo): **30–50% de ahorro** en tareas elegibles.

---

## 🔑 Takeaways del Bloque 4

1. **Árbol de decisión primero** — no toda tarea merece IA
2. **3 patrones universales**: Investigar→Borradora, Reunión→Acciones, Datos→Reporte
3. **HITL para alto riesgo**, automatización solo para lo reversible
4. **Máximo 3 rondas de refinamiento**, luego edita manual
5. **40% del tiempo ahorrado se pierde en retrabajo** — siempre reserva tiempo de revisión
6. **Obsidian conecta todo esto** → [[bloque_05_obsidian_cerebro_claude]]

---

## 💡 Demo sugerida (en vivo)

**Demo — Reunión → Plan de acción en tiempo real:**

1. Toma 5 líneas de notas de una reunión reciente
2. Usa el prompt del Patrón B:
```
Extrae compromisos de estas notas.
Formato tabla: | Acción | Responsable | Fecha | Prioridad |
Si falta dato → "No definido"
Solo compromisos. Sin contexto.

--- NOTAS ---
[notas aquí]
```
3. Muestra el resultado en 30 segundos
4. Pregunta al equipo: ¿cuánto tardaban antes?

---

> [!info] Navegación
> ← [[bloque_03_optimizacion_tokens]] | Siguiente → [[bloque_05_obsidian_cerebro_claude]]

> [!tip] Siguiente nivel — automatiza estos flujos con agentes
> Cuando los patrones de trabajo ya son rutina, despliega agentes que los ejecuten solos: [[Construyendo con IA/Indice de agentes IA|Índice de agentes IA]] · [[Construyendo con IA/Equipos Multi-agente|Equipos Multi-agente]]

*Fuentes: HBR "Workslop" (2025), CIO "40% rework" (2025), McKinsey AI Workflows, Federal Reserve Productivity Research, Anthropic Productivity Study, MindStudio HITL Guide*
