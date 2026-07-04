# PROMPT PARA GENERAR DASHBOARD — Ejercicio Municipalidad de Heredia

Soy Rubi Quispe Sierra, estudiante de Control de Calidad Estadístico. Ya analicé el siguiente ejercicio siguiendo el flujo de mi README maestro (decision_Control_Calidad_Estadistico.md). Quiero que generes un dashboard HTML con toda la información que detallo a continuación, sin volver a recalcular nada — solo organizando y presentando visualmente lo que ya está resuelto.

---

## 1. Contexto del ejercicio

La Municipalidad de Heredia recibió quejas de vecinos colindantes a un taller de soldadura por ruido en horas nocturnas. Se recomendó a la empresa contratar un técnico y hacer un estudio de decibeles (dB). Se tomaron 5 muestras por hora, desde la medianoche hasta las 4:00 a.m.

**Datos (subgrupos n=5):**

| Hora | Lecturas (dB) |
|---|---|
| 12:00 a.m. | 24, 33, 29, 30, 28 |
| 1:00 a.m. | 25, 28, 27, 28, 30 |
| 2:00 a.m. | 32, 31, 30, 29, 30 |
| 3:00 a.m. | 18, 24, 21, 23, 38 |
| 4:00 a.m. | 30, 26, 33, 27, 25 |

**Preguntas del ejercicio:**

a) ¿Se presentan causas asignables de variación? ¿Está el proceso bajo control estadístico?

b) Con especificación de 29 ± 2 dB y 3% de no conformes: ¿puede el proceso cumplir la especificación? ¿En qué situación se encuentra? ¿Puede trabajar un tercer turno?

---

## 2. Clasificación y justificación (para incluir tal cual en el dashboard)

| Pregunta clave | Respuesta | Conclusión |
|---|---|---|
| ¿La medición es continua? | Sí, dB es continuo | Rama de **variables** (se descarta atributos) |
| ¿n>1 constante, tamaño pequeño-moderado? | Sí, n=5 constante | **X̄-R** (se descarta X̄-S y X-Rm) |
| ¿Hay límites de especificación? | Sí, 29±2 dB | Se activa **Capacidad de Procesos** |

**Decisión final:** Carta de control **X̄-R** + **Análisis de Capacidad de Procesos**.

---

## 3. Resultados a mostrar (dos iteraciones)

### Iteración 1 — con los 5 subgrupos:
- X̄̄ = 27.96, R̄ = 9
- Carta X̄: LCS=33.15, LC=27.96, LCI=22.77
- Carta R: LCS=19.03, LC=9, LCI=0
- Hallazgo: el subgrupo de 3:00 a.m. tiene R=20, que **excede el LCS (19.03)** → causa asignable detectada

### Iteración 2 — depurada, sin el subgrupo de 3:00 a.m.:
- X̄̄ = 28.75, R̄ = 6.25
- Carta X̄: LCS=32.36, LC=28.75, LCI=25.14
- Carta R: LCS=13.21, LC=6.25, LCI=0
- Todos los puntos restantes caen dentro de control → proceso estable

### Índices de capacidad (con datos depurados):
- σ̂ = 2.687
- Cp = 0.248 → **Clase 4, No adecuado**
- Cpi = 0.217, Cps = 0.279, Cpk = 0.217
- K = −12.5% (aceptable, |K|<20%)
- Cpm: bajo, pese a buen centrado, por alta dispersión

---

## 4. Conclusiones (sección separada y nombrada en el dashboard)

1. El proceso presenta una causa asignable de variación en el subgrupo de las 3:00 a.m., por lo que inicialmente **no está bajo control estadístico**.
2. Al remover ese subgrupo, el proceso se vuelve **estable**, pero su capacidad es **insuficiente** (Cp=0.248, Clase 4).
3. Clasificación final combinada: **No capaz y estable**.

---

## 5. Recomendaciones (sección separada y nombrada en el dashboard)

1. Investigar y documentar la causa raíz del evento atípico de las 3:00 a.m. antes de excluirlo formalmente.
2. Continuar monitoreando con carta X̄-R para confirmar estabilidad en el tiempo.
3. Implementar mejoras (aislamiento acústico, mantenimiento de maquinaria, revisión de procedimientos nocturnos) para reducir variabilidad antes de un tercer turno.
4. No autorizar el tercer turno hasta que Cp y Cpk superen al menos 1.0 (idealmente ≥1.33).

---

## 6. Estructura del dashboard (según mi README, sección 6)

- Archivo HTML autocontenido, paleta morada, título "Práctica Calificada 4", con "Rubi Quispe Sierra" debajo del título principal.
- 4 pestañas por tema (no por herramienta):
  1. **Contexto y Enunciado** (imagen del enunciado + tarjeta de clasificación)
  2. **Gráfica de Control** (Minitab + Excel — ambas iteraciones, X̄ y R)
  3. **Capacidad de Procesos** (gráfica + tabla de cálculo + clasificación Cp + Conclusiones y Recomendaciones como secciones separadas)
  4. **Verificación** (capturas originales mías, embebidas en base64, separadas del resto)
- Gráficas recreadas como SVG/HTML, no como imagen simple.
- Colores: Minitab = rojo (LCS/LCI) / verde (LC). Excel = verde (LCS/LCI) / naranja (LC).
- Tarjetas resumen: Media Global, Desv. Estándar, LCS, LCI, sobre fondo morado degradado + gráfico de barras de datos crudos.