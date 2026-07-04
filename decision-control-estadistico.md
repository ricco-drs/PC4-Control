# README — Práctica Calificada: 

- **Autora:** Rubi Quispe Sierra
- **Curso:** Control Estadístico de procesos — Práctica Calificada 4
- **Herramientas permitidas:** Minitab y Excel únicamente. **R y Python quedan excluidos de todo entregable.**

---

## 1. Alcance del curso (árbol de decisión)

```
Control estadístico de procesos
│
├── Gráficas de control
│   ├── Por variables
│   │     ├── X̄-R
│   │     ├── X̄-S
│   │     └── Mediciones individuales / Rango móvil (X-Rm)
│   │
│   └── Por atributos
│         ├── p̄  (fracción defectuosa)
│         ├── np̄ (número de defectuosos)
│         ├── c̄  (número de defectos)
│         └── ū  (defectos por unidad)
│
└── Índices de capacidad de procesos
      ├── Cp
      ├── Cpi / Cps / Cpk
      ├── Cpm
      └── K
```

> **Nota:** Zi/Zs/Z y DPMO **no** se incluyen en el análisis de capacidad de este curso. Solo se trabaja hasta Cpm y K.

Un mismo ejercicio puede caer en **una sola rama** o ser una **combinación** (ej. X̄-R + Capacidad de Procesos, o carta-c + Capacidad).

---

## 2. Flujo de trabajo por ejercicio

Cada vez que el usuario envía un problema, Claude sigue este orden estricto:

1. **Transcripción del enunciado** — Claude transcribe el problema completo (contexto, datos, especificación) y **pregunta si la transcripción es correcta**. No avanza sin confirmación.
2. **Clasificación y justificación** — Una vez confirmado, Claude identifica la rama (o combinación de ramas) del árbol y arma la tarjeta:

   > 🔍 **Clasificación del tema y justificación**
   > Tabla: Pregunta clave → Respuesta según el enunciado → Conclusión
   > (descartando explícitamente las alternativas, no solo afirmando la elegida)

3. **Organización de datos** — formato listo para copiar/pegar en Minitab y Excel, con todas las variables necesarias que debe aparecer en el Excel.
4. **Cálculo manual** — de todos los límites/índices, para verificar contra el software.
5. **Generación de outputs en software** — instrucciones paso a paso para Minitab y Excel (rutas de menú exactas).
6. **Conclusiones y Recomendaciones** — siempre como **secciones separadas y nombradas**, fundamentadas estadísticamente.

---

## 3. Criterios de decisión (clasificación)

### 3.1 Variables vs. Atributos
| Pregunta | Si la respuesta es... | Conclusión |
|---|---|---|
| ¿La medición es continua (longitud, peso, tiempo, desgaste, etc.)? | Sí | Rama de **variables** |
| ¿La medición es pasa/no pasa, defecto/no defecto? | Sí | Rama de **atributos** |

### 3.2 Dentro de Variables
| Pregunta | Conclusión |
|---|---|
| ¿n > 1 constante por subgrupo, tamaño de muestra pequeño-moderado (≤8-10)? | **X̄-R** |
| ¿n > 1 pero tamaño de muestra grande (>10) o se requiere mayor precisión en dispersión? | **X̄-S** |
| ¿n = 1 (mediciones individuales, no hay forma de subagrupar)? | **X-Rm (individuales / rango móvil)** |

### 3.3 Dentro de Atributos
| Pregunta 1 | Pregunta 2 | Conclusión |
|---|---|---|
| ¿Se cuentan **unidades defectuosas** (la unidad completa pasa/falla)? | ¿Tamaño de muestra constante? | **np̄** (constante) / **p̄** (variable) |
| ¿Se cuentan **defectos** (una unidad puede tener varios defectos)? | ¿Unidad de inspección constante? | **c̄** (constante) / **ū** (variable) |

### 3.4 Activación de Capacidad de Procesos
| Pregunta | Conclusión |
|---|---|
| ¿El enunciado da límites de especificación (EI/ES, tolerancia, "especificación X±Y")? | Se agrega el bloque de **Índices de Capacidad** (Cp, Cpi, Cps, Cpk, Cpm, K) |
| ¿Pide evaluar si el proceso es "capaz"? | Ídem |

### 3.5 Clasificación final obligatoria (cuando hay capacidad)
Siempre cruzar **capacidad** (Cp/Cpk) con **estabilidad** (gráfica de control, ¿hay puntos fuera de límites o patrones no aleatorios?) para concluir en una de 4 categorías:
- Capaz y estable
- Capaz y no estable
- No capaz y estable
- No capaz y no estable

---

## 4. Fórmulas de referencia

### 4.1 Gráficas de control por variables

**X̄-R**
- Medias: LCS = X̄ + A₂·R̄ | LC = X̄ | LCI = X̄ − A₂·R̄
- Rangos: LCS = D₄·R̄ | LC = R̄ | LCI = D₃·R̄

**X̄-S**
- Medias: LCS = X̄ + A₃·S̄ | LCI = X̄ − A₃·S̄
- Desv. estándar: LCS = B₄·S̄ | LC = S̄ | LCI = B₃·S̄

**X-Rm (individuales)**
- Rm = |Xᵢ − Xᵢ₋₁| (el primer valor no se grafica)
- Individuales: LCS = X̄ + 3·R̄m/d₂ | LCI = X̄ − 3·R̄m/d₂
- Rango móvil: LCS = D₄·R̄m | LCI = D₃·R̄m

### 4.2 Gráficas de control por atributos

| Carta | LC | Límites |
|---|---|---|
| p | p̄ = Σnp / Σn | p̄ ± 3√(p̄(1−p̄)/n) |
| np | n·p̄ | n·p̄ ± 3√(n·p̄(1−p̄)) |
| c | c̄ = Σc / n_subgrupos | c̄ ± 3√c̄ |
| u | ū = Σc / Σn | ū ± 3√(ū/n) |

### 4.3 Índices de capacidad de procesos

- **Cp** = (ES − EI) / 6σ
- **Cr** = 6σ / (ES − EI)
- **Cpi** = (μ − EI) / 3σ
- **Cps** = (ES − μ) / 3σ
- **Cpk** = min(Cpi, Cps)
- **K** = [(μ − N) / (½(ES − EI))] × 100 → aceptable si |K| < 20%; positivo si μ > N
- **Cpm**: se calcula usando K; >1 significa que la media está dentro del tercio medio de la banda de especificación; >1.33 dentro del quinto medio

**Tabla de clasificación de Cp:**
| Rango de Cp | Clase |
|---|---|
| ≥ 2 | Clase Mundial / Seis Sigma |
| > 1.33 | Clase 1 — Adecuado |
| 1 < Cp < 1.33 | Clase 2 — Parcialmente adecuado |
| 0.67 < Cp < 1 | Clase 3 — No adecuado |
| < 0.67 | Clase 4 — No adecuado |

---

## 5. Particularidades de Minitab y Excel

- **Minitab (versión en español)**: no acepta datos pre-resumidos (medias y rangos) directamente en el diálogo de X̄-R. Workaround: `Gráfica → Gráfica de Series de Tiempo → Simple`, luego agregar manualmente 7 líneas de referencia (LCS, +2SL, +1SL, LC, −1SL, −2SL, LCI). Colores: LCS/LCI = rojo, LC = verde (vía doble clic → panel Atributos).
- **Excel**: se arma con dos tablas en formato largo (una por cada gráfica del par, ej. X y R), con columnas de límites repetidas por fila, listas para pegar y graficar como gráfico de línea. Colores: LCS/LCI = verde, LC = naranja.
- **Generación automática de tablas**: cada vez que un ejercicio involucre un par de cartas (ej. LC de X̄ y LC de R), Claude genera automáticamente, sin que se le pida:
  - 2 tablas para Minitab (formato "Línea | Valor" con las 7 referencias) + instrucciones paso a paso + guía de colores
  - 2 tablas para Excel (formato largo, listas para graficar)

---

## 6. Formato del Dashboard (HTML, "Práctica Calificada 4")

- Archivo HTML autocontenido, imágenes embebidas en base64.
- **Paleta de colores:** tonos morados en todo el dashboard (hero, tarjetas resumen, acentos).
- **Encabezado:** título "Práctica Calificada 4" + subtítulo + caja de "Contexto del Análisis". El nombre **Rubi Quispe Sierra** aparece directamente debajo del título principal en el hero (no solo en el pie de página).
- **Navegación por pestañas organizadas por TEMA** (no por herramienta). Ejemplo con 4 tabs por ejercicio:
  1. Contexto y Enunciado (imagen del enunciado + tarjeta de clasificación y justificación)
  2. Gráfica de control (Minitab + Excel, según el tema: variables o atributos)
  3. Capacidad de Procesos (si aplica) — con Conclusiones y Recomendaciones como secciones separadas
  4. Verificación (solo capturas originales de Pixie, embebidas en base64 — nunca mezcladas con las demás secciones)
- **Gráficas recreadas como SVG/HTML** cuando Pixie entrega capturas reales de Minitab/Excel — no se insertan como imagen simple, se recrean manteniendo consistencia visual.
- **Colores de gráficas:** Minitab = rojo (LCS/LCI) / verde (LC). Excel = verde (LCS/LCI) / naranja (LC).
- **Tarjetas resumen:** Media Global / Desv. Estándar / LCS / LCI sobre fondo degradado morado + gráfico de barras de datos crudos.
- Conclusiones y Recomendaciones siempre como secciones separadas y explícitamente nombradas.

---

## 7. Reglas de estilo transversales

- No usar R ni Python en ningún entregable.
- Toda elección de tipo de gráfica debe fundamentarse con la tabla pregunta→respuesta→conclusión, descartando alternativas.
- Todo ejercicio termina con Conclusiones + Recomendaciones + clasificación final (capaz/no capaz × estable/no estable, cuando aplique capacidad).
- Este documento es la referencia maestra reutilizable para todos los ejercicios de la Práctica Calificada 4 de Control de Calidad Estadístico.
