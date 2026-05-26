---
tags: [plantilla, prompt, RTFC, reutilizable]
tipo: template
relacionado: ["[[bloque_02_prompt_engineering]]", "[[00_MOC_Capacitacion_IA]]"]
---

# 📋 Plantilla Base de Prompt — Framework RTFC

> Copia, rellena los `___` y pega en Claude.  
> Elimina las secciones que no necesites para cada tarea.

---

## Versión completa

```
[ROL]
Actúa como Desarrollador senior de web

[TAREA]
Tu objetivo es construir una landing page de una empresa que se encarga de la venta de polimeros 
Específicamente debes crear una pagina moderna, colorida y que se apegue al archivo de contextp #contexto 

[CONTEXTO]
- Audiencia: ___
- Situación: ___
- Información relevante: ___

[FORMATO]
- Estructura: landing page
- Longitud máxima: un carrousel de 5 imagenes
- Tono: Profesional orientado a ventas
- Idioma: Español

[RESTRICCIONES]
- No incluir: nada que no sea nuestro #contexto 
- Evitar: crear ietraciones externas y llamadas a archivos que no esten indicados
- Supuestos a NO hacer: NO hacer servidor, No hacer un apartado de api, etc

--- INSUMO ---
[pega aquí el contenido a procesar]


---

## Versión rápida (tareas simples)

```
Actúa como ___.
Tu tarea: ___.
Formato: ___.
Restricción: ___.
```

---

## Versión XML (máximo control en Claude)

```xml
<rol>
___
</rol>

<tarea>
___
</tarea>

<contexto>
___
</contexto>

<formato>
___
</formato>

<insumo>
___
</insumo>
```

---

## Ejemplos rellenos

### Email profesional
```
[ROL] Redactor corporativo bilingüe, tono formal-cercano.
[TAREA] Escribe un email comunicando un cambio de política interna.
[CONTEXTO]
- Audiencia: 80 empleados, todos niveles
- Cambio: nuevo horario de reuniones (lunes 9am fijo)
- Razón: mejorar coordinación de equipos
[FORMATO] 3 párrafos. Asunto incluido. Máximo 150 palabras. Sin bullet points.
[RESTRICCIONES] No sonar autoritario. No pedir confirmación de lectura.
```

### Resumen ejecutivo
```
[ROL] Analista senior.
[TAREA] Resume el documento adjunto en 5 hallazgos clave.
[FORMATO] Lista numerada. Cada punto: 1 oración con verbo al inicio.
[CONTEXTO] Audiencia: directivos. Tiempo de lectura: 2 minutos máximo.
--- DOCUMENTO ---
[pega aquí]
```

### Plan de acción desde notas
```
[TAREA] Extrae todos los compromisos de estas notas de reunión.
[FORMATO] Tabla: | Acción | Responsable | Fecha | Prioridad |
[RESTRICCIONES] Solo compromisos concretos. Si falta dato, escribe "No definido".
--- NOTAS ---
[pega aquí]
```

---

> Ver teoría completa en [[bloque_02_prompt_engineering]]  
> Volver al mapa → [[00_MOC_Capacitacion_IA]]
