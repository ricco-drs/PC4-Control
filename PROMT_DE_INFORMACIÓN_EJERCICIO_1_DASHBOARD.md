# README — Contenido del Dashboard: Práctica Calificada 4 (Control de Calidad Estadístico)

**Autora:** Rubi Quispe Sierra ("Pixie")
**Propósito de este documento:** definir exclusivamente **qué información debe contener el dashboard**, organizada en 4 partes secuenciales. (Para reglas de cálculo, fórmulas y procedimientos de Minitab/Excel, ver el README general del curso.)

---

## PARTE 1 — Contexto y Enunciado

Debe incluir, en este orden:

1. **Enunciado del ejercicio redactado** — transcripción en texto del problema completo (contexto, condición del proceso, especificaciones si las hay, y qué se pide: a), b), c)...).
2. **Imagen original del enunciado** — la captura/foto que Pixie proporciona, embebida en base64.
3. **🔍 Tarjeta de Clasificación del tema y justificación** — tabla con formato:

   | Pregunta clave | Respuesta según el enunciado | Conclusión |
   |---|---|---|

   Debe descartar explícitamente las alternativas del árbol de decisión (no solo afirmar la rama elegida), cubriendo: variables vs. atributos, tipo específico de carta dentro de la rama elegida, y si corresponde activar el bloque de Capacidad de Procesos.

4. **Tabla de datos originales** — los datos crudos del ejercicio, en el orden y formato en que se usarán para los cálculos (con numeración N° | Valor, o la estructura de subgrupos si aplica).

---

## PARTE 2 — Gráficas de Control (Minitab y Excel)

Aplica según el tema del ejercicio: **Variables** (X̄-R, X̄-S, o Individuales-Rango Móvil) o **Atributos** (p, np, c, u). Debe incluir:

1. **Gráfica(s) en Minitab** — recreada(s) como SVG/HTML manteniendo la apariencia visual de Minitab (colores: LCS/LCI = rojo, LC = verde).
2. **Gráfica(s) en Excel** — recreada(s) como SVG/HTML (colores: LCS/LCI = verde, LC = naranja).
3. **Interpretación individual de cada gráfica** — texto explicando: ¿hay puntos fuera de límites de control? ¿se observan patrones no aleatorios (rachas, tendencias, ciclos)? ¿el proceso se muestra estable en esa carta específica?
4. **Cuadro comparativo Minitab vs. Excel** — tabla que contraste ambos resultados (límites calculados, decisión final por punto, coincidencias/discrepancias), resaltando en color ámbar/dorado cualquier celda donde los valores difieran, con columna "¿Coinciden?".

> Nota: si el ejercicio es de Individuales-Rango Móvil, van dos pares de gráficas (Individuales + Rango Móvil), cada una con su propia interpretación y su propio cuadro comparativo (o uno combinado, según la extensión).

---

## PARTE 3 — Capacidad de Procesos

Debe incluir, en este orden:

1. **Gráfica de Capacidad de Procesos** — histograma (Minitab y/o Excel, recreado como SVG/HTML) con las líneas de especificación (EI, N/Objetivo, ES) superpuestas sobre la distribución de los datos originales.
2. **Tabla de cálculo detallado con todos los parámetros base**, como mínimo:

   | Parámetro | Símbolo | Valor |
   |---|---|---|
   | Media del proceso | X̄ (o μ) | |
   | Rango móvil promedio (si aplica) | R̄m | |
   | Desviación estándar estimada | σ̂ | |
   | Límite de especificación inferior | EI | |
   | Límite de especificación superior | ES | |
   | Valor nominal / objetivo | N | |

3. **Tabla de índices de capacidad** — Cp, Cpi, Cps y Cpk, cada uno con su fórmula aplicada y su resultado numérico.
4. **Clasificación de capacidad** — según la tabla de clases del curso (Clase Mundial/Seis Sigma, Clase 1 Adecuado, Clase 2 Parcialmente adecuado, Clase 3 No adecuado, Clase 4 No adecuado), indicando en qué clase cae el Cp (y el Cpk) del ejercicio.
5. **Cuadro comparativo Capacidad vs. Estabilidad** — tabla que cruce el resultado de capacidad (Parte 3) con el resultado de estabilidad (Parte 2), con su diagnóstico final en una de las 4 categorías:
   - Capaz y estable
   - Capaz y no estable
   - No capaz y estable
   - No capaz y no estable

   Debe incluir la razón/justificación estadística de por qué cae en esa categoría.

---

## PARTE 4 — Conclusiones, Recomendaciones y Verificación

Debe incluir, como secciones separadas y explícitamente nombradas:

1. **Conclusiones** — síntesis de los hallazgos de estabilidad (Parte 2) y capacidad (Parte 3), redactada de forma integral (no solo repetir los cuadros, sino explicar qué significan en términos del proceso real).
2. **Recomendaciones generales** — acciones concretas y priorizadas para mejorar el proceso (causas especiales a investigar, reducción de variabilidad, centrado del proceso, re-evaluación posterior, etc.).
3. **Sección de Verificación** — las fotos/capturas **originales** que Pixie envió de las gráficas generadas en Minitab y en Excel, embebidas en base64 tal cual, **sin recrear ni modificar** (esta sección es independiente de las gráficas recreadas en SVG/HTML de la Parte 2 y Parte 3 — sirve para verificar que el procedimiento manual coincide con lo que arrojó el software).

---

## Reglas transversales de formato (aplican a las 4 partes)

- Archivo HTML autocontenido, imágenes embebidas en base64.
- Paleta de colores: tonos morados (hero, tarjetas resumen, acentos).
- Encabezado con título "Práctica Calificada 4" + subtítulo + caja de "Contexto del Análisis"; nombre de la autora (Rubi Quispe Sierra) debajo del título principal en el hero.
- Tarjetas resumen (Media Global / Desv. Estándar / LCS / LCI) sobre fondo degradado morado + gráfico de barras de datos crudos.
- Las 4 partes pueden navegarse como secuencia continua (scroll) o como pestañas — pero el **orden y agrupación de contenido** dentro de cada parte debe respetar exactamente esta estructura.
