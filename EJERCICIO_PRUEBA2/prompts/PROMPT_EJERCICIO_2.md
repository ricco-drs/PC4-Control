# Prompt para generación de Dashboard — Ejercicio 11 (Control X-Rm + Capacidad de Procesos)

Voy a pedirte que generes un dashboard HTML para el Ejercicio 11 de mi Práctica Calificada 4 de Control de Calidad Estadístico. Antes de que lo generes, te explico el razonamiento completo detrás de cada decisión que tomé, para que el dashboard refleje fielmente ese análisis y no solo los resultados finales.

---

## 1. Contexto del problema

Una empresa imprime láminas de acero que luego se convierten en recipientes. En una fase del proceso, un horno debe mantener una temperatura de **125°C ± 5°C** (EI = 120°C, N = 125°C, ES = 130°C). Se registró la temperatura del horno cada hora durante tres días, dando 24 mediciones individuales. Existe la sospecha de que al horno le falta una política de mantenimiento preventivo, y se pide usar la carta de control correspondiente para confirmar o descartar esa sospecha, complementando con un análisis de capacidad (Cp, Cpk, Cpm).

---

## 2. Decisión de clasificación y justificación

### 2.1 Variables vs. Atributos
La temperatura es una variable continua medida en °C con valores decimales, no un conteo de defectos ni una clasificación pasa/no pasa. Por lo tanto, descarté por completo la rama de atributos (p, np, c, u) y me quedé en la rama de **variables**.

### 2.2 Elección de la carta dentro de variables
Existen tres opciones dentro de variables: X̄-R, X̄-S, y X-Rm (Individuales/Rango Móvil). Las dos primeras requieren subgrupos con más de una observación (n>1) tomadas en el mismo instante, de forma que exista variabilidad *dentro* de cada subgrupo. En este caso, solo se toma **una lectura de temperatura por hora**: no hay repeticiones simultáneas que permitan formar un subgrupo. Por eso descarté X̄-R y X̄-S, y elegí **X-Rm (Individuales y Rango Móvil)**, que es la carta diseñada específicamente para mediciones individuales sucesivas en el tiempo, donde el rango móvil (diferencia absoluta entre observaciones consecutivas) sustituye al rango dentro de subgrupo.

### 2.3 Activación del bloque de capacidad
El enunciado entrega explícitamente límites de especificación (125°C ± 5°C) y pide evaluar la capacidad del proceso con Cp, Cpk y Cpm. Esto activa automáticamente el bloque de índices de capacidad, que de otra forma no se incluiría.

### 2.4 Cruce final: capacidad × estabilidad
Toda vez que se activa el bloque de capacidad, el curso exige cruzar dos dimensiones para llegar a una conclusión de una de cuatro categorías posibles: capaz y estable, capaz y no estable, no capaz y estable, no capaz y no estable. Esto es clave porque la respuesta a la sospecha del enunciado (falta de mantenimiento) depende de si el problema es de **estabilidad** (causas especiales, esperables si hay fallas intermitentes de mantenimiento) o de **capacidad** (causas comunes, inherentes al diseño u operación normal del proceso).

---

## 3. Resultados del análisis (para incluir en el dashboard)

### 3.1 Carta de Individuales (X)
- X̄ = 127.12
- σ̂ = R̄m/d₂ = 1.9581
- LCS = 132.99, +2SL = 131.03, +1SL = 129.07, LC = 127.12, −1SL = 125.16, −2SL = 123.20, LCI = 121.24
- Ningún punto fuera de los límites de control; sin rachas ni tendencias evidentes.

### 3.2 Carta de Rango Móvil (Rm)
- R̄m = 2.2087
- LCS = 7.22, LC = 2.21, LCI = 0.00
- Ningún punto fuera de los límites.

**Conclusión de estabilidad: proceso estadísticamente estable** (no hay evidencia de causas especiales bajo la regla de 3σ). Se observan tres puntos en zona de alerta (más allá de 2σ): muestras 3 (122.7), 10 (123.0) y 24 (131.9), que ameritan seguimiento aunque no constituyen señal de descontrol bajo el criterio de 3σ.

### 3.3 Índices de capacidad
- Cp = 0.85 → Clase 3, No adecuado
- Cpi = 1.21 / Cps = 0.49 → Cpk = 0.49
- K = 42.33% (positivo, fuera del rango aceptable de ±20%)
- Cpm = 0.58 (por debajo de 1, la media no está dentro del tercio medio de la especificación)

**Conclusión de capacidad: proceso NO capaz.** La variabilidad inherente del horno es demasiado alta para la tolerancia permitida, y además la temperatura promedio está corrida hacia arriba (127.12°C vs. 125°C nominal), acercándose peligrosamente al límite superior de especificación.

### 3.4 Clasificación final
**NO CAPAZ Y ESTABLE.** El proceso es consistente en el tiempo (no hay fallas esporádicas visibles en la carta), pero su variabilidad natural y su descentrado son intrínsecos al proceso tal como opera actualmente.

---

## 4. Conclusiones que debe incluir el dashboard

1. La carta de control X-Rm no muestra puntos fuera de límites ni patrones no aleatorios: el horno es estadísticamente estable en el periodo analizado.
2. El análisis de capacidad muestra que el proceso no cumple con la especificación de 125°C ± 5°C: Cp = 0.85, Cpk = 0.49, Cpm = 0.58, todos por debajo de los mínimos aceptables.
3. El indicador K = 42.33% confirma que el horno opera con una temperatura promedio desplazada significativamente por encima del valor nominal.
4. La sospecha de "falta de mantenimiento preventivo" no queda respaldada por la carta de control, ya que ese tipo de problema típicamente se manifiesta como inestabilidad (puntos fuera de control, rachas), y eso no se observa. El problema reportado por los clientes se explica mejor por causas comunes: variabilidad intrínseca del horno y descentrado sistemático de la temperatura.

## 5. Recomendaciones que debe incluir el dashboard

1. Recalibrar el horno para centrar la temperatura promedio en 125°C, lo que mejoraría Cpk y Cpm sin necesidad de reducir variabilidad.
2. Investigar las causas comunes de variabilidad (termostato, aislamiento térmico, calibración de sensores) mediante un diagrama de Ishikawa o un diseño de experimentos, dado que incluso centrado el proceso seguiría siendo limítrofe (Cp=0.85).
3. No descartar un plan de mantenimiento preventivo: reducir la variabilidad del horno probablemente sí requiera intervenciones (limpieza de resistencias, calibración periódica), aunque el motivo sea desgaste gradual y no fallas esporádicas.
4. Dar seguimiento a los puntos en zona de alerta (muestras 3, 10 y 24) en futuras corridas para descartar una tendencia de deriva ascendente.

---

## 6. Estructura y formato requerido del dashboard

- Archivo HTML autocontenido, con paleta de colores en tonos morados en todo el dashboard (hero, tarjetas resumen, acentos).
- Encabezado con el título "Práctica Calificada 4", subtítulo, y una caja de "Contexto del Análisis" con el resumen del problema del horno.
- Navegación por pestañas organizada por tema (no por herramienta), con estas pestañas:
  1. **Contexto y Enunciado**: imagen o transcripción del enunciado + tarjeta de clasificación y justificación (tabla pregunta → respuesta → conclusión, descartando explícitamente las alternativas).
  2. **Gráfica de Control**: cartas de Individuales y Rango Móvil recreadas como SVG/HTML (no como imagen), mostrando Minitab y Excel, con interpretación de cada carta (ausencia de puntos fuera de control, ausencia de rachas, mención de los puntos en zona de alerta).
  3. **Capacidad de Procesos**: gráfica de capacidad con líneas EI/N/ES sobre los datos originales, tabla de cálculo con todos los parámetros (X̄, σ̂, EI, ES, N, Cp, Cpi, Cps, Cpk, K, Cpm), clasificación según la tabla de clases de Cp, y el diagnóstico cruzado de capacidad × estabilidad (no capaz y estable). Conclusiones y Recomendaciones deben ir aquí como secciones separadas y explícitamente nombradas (nunca fusionadas en un solo bloque).
  4. **Verificación**: únicamente capturas originales de mis herramientas (Minitab/Excel), embebidas en base64, sin mezclarlas con las demás secciones.
- Colores de las gráficas: en Minitab, LCS/LCI en rojo y LC en verde; en Excel, LCS/LCI en verde y LC en naranja.
- Tarjetas resumen con Media Global, Desviación Estándar, LCS y LCI sobre fondo degradado morado, más un gráfico de barras de los datos crudos de temperatura.
- Nombre del autor visible directamente debajo del título principal en el hero, y también en el pie de página.
- No usar R ni Python en ningún entregable ni mención dentro del dashboard; solo Minitab y Excel.