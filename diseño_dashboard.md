# README — Formato Visual de Dashboards "Práctica Calificada 4"

Este documento es el **prompt maestro reutilizable** que describe cómo debe verse, estructurarse y comportarse cualquier dashboard HTML generado para la Práctica Calificada 4 (Control de Calidad Estadístico). Úsalo como referencia o pégalo directamente al pedir un nuevo dashboard.

---

## 🎯 Prompt maestro (copiar y pegar)

```
Crea un dashboard HTML autocontenido (una sola página, sin dependencias externas
salvo Google Fonts) para un problema de la Práctica Calificada 4 de Control de
Calidad Estadístico. Debe verse así:

IDENTIDAD VISUAL
- Paleta de colores en tonalidades MORADAS: 
  · Fondo hero: degradado morado oscuro (#1e1040 → #3b1f6b → #5c3ba0)
  · Fondo general de página: gris muy claro lavanda (#f7f5fb)
  · Tarjetas resumen (stat-cards): degradado morado medio (#7a5fc4 → #3f2478)
  · Acentos dorados (#d4af37 / #f1d98b) para bordes, badges y bullets
- Tipografía: 'Playfair Display' (serif) para títulos, 'Inter' (sans) para texto
  general, 'JetBrains Mono' para valores numéricos, fórmulas y etiquetas técnicas
- Tarjetas ("cards") blancas, esquinas redondeadas (14px), sombra suave

HEADER (hero)
- Título principal: "Práctica Calificada 4"
- Justo debajo del título: nombre del autor en mayúsculas, monoespaciado,
  color lavanda claro (NO solo en el footer)
- Subtítulo: nombre del curso + tema específico del problema
- Caja "📊 Contexto del Análisis" con fondo semitransparente y borde dorado
- Badges (píldoras) con: tema general, tipo de carta/índice elegido, tamaño de muestra

NAVEGACIÓN
- Pestañas (tabs) horizontales, NO scroll único de secciones apiladas
- Estructura de pestañas según el tema:
  · Si es UN SOLO problema/tema: Parte 1 (Enunciado + Minitab) | Parte 2 (Excel) |
    Parte 3 (Análisis Estadístico) | Verificación
  · Si son TRES temas en una misma práctica: Tab por tema (Variables / Atributos /
    Capacidad), cada uno con sub-bloques Minitab y Excel dentro
- Pestaña activa: subrayado dorado, texto en color morado oscuro
- Verificación SIEMPRE como pestaña separada e independiente (nunca mezclada
  con el análisis estadístico)

PARTE 1 (Enunciado)
- Contexto del análisis (texto)
- "Se pide" (las preguntas literales del enunciado)
- Imagen del enunciado tal cual (captura original, embebida en base64)
- Tarjeta "🔍 Clasificación del tema y justificación": explica con 2-3 preguntas
  clave por qué se eligió esa carta/índice específico y por qué se descartan
  las demás opciones del tema, cerrando con una tabla pregunta → respuesta →
  conclusión

GRÁFICAS (Minitab y Excel) — SOLO SVG RECREADO, NUNCA CAPTURAS
- REGLA ABSOLUTA: en las Partes 2 (Gráficas de Control) y 3 (Capacidad de
  Procesos) las gráficas se RECREAN íntegramente en SVG/HTML a partir del
  procedimiento seguido y de los valores calculados manualmente. Está PROHIBIDO
  pegar aquí capturas/imágenes de Minitab o Excel: esas van únicamente en la
  pestaña Verificación.
- Cada gráfica SVG debe ser NUMÉRICAMENTE CORRECTA y fiel a los valores
  calculados: los puntos, los límites (LCS/LC/LCI), las escalas de los ejes y
  la posición relativa de cada dato deben coincidir exactamente con la tabla de
  cálculo manual. Una gráfica bonita pero con valores mal ubicados es un error.
- Antes de dibujar, derivar los puntos y límites del procedimiento (fórmulas de
  la sección correspondiente del documento maestro) y verificar que el SVG los
  respeta punto por punto.
- Colores de líneas de control:
  · Minitab: LCS/LCI en rojo, LC en verde
  · Excel: LCS/LCI en verde, LC en naranja
- Etiqueta de herramienta arriba de cada gráfica: pastilla de color con
  "● MINITAB" (azul #2D6FE0) o "● EXCEL" (verde #1E8E4E)
- Debajo de cada gráfica: caja de interpretación con teoría aplicada
  (causas comunes vs. asignables, reglas de control, rachas, tendencias, etc.)
- Ruta de Minitab explicada paso a paso (menú → submenú → opción)
- Fórmulas usadas en Excel explicadas paso a paso

ANÁLISIS ESTADÍSTICO
- Fila de "stat-cards" con los valores clave (medias, límites, metas, etc.)
  en tarjetas moradas con degradado
- Respuestas a cada pregunta del enunciado, una por tarjeta, con conclusión
  resaltada (flag verde si "cumple/en control", flag rojo si "no cumple/fuera
  de control")
- Tabla comparativa Minitab vs. Excel con columna "¿Coinciden?"
- Gráfico de barras de los datos crudos de todas las muestras
- Conclusiones (lista con bullets ◆ dorados)
- Recomendaciones (lista con flechas → verdes)

VERIFICACIÓN (pestaña independiente) — ÚNICO LUGAR PARA CAPTURAS
- Es la ÚNICA pestaña donde se adjuntan capturas/imágenes de las gráficas
  generadas por el software. Ninguna otra sección de análisis (Partes 2 y 3)
  lleva capturas.
- Solo las capturas ORIGINALES que el usuario proporcionó (Minitab, Excel,
  tablas de Excel), embebidas en base64, comprimidas a JPEG calidad ~78 y
  ancho máximo 900px para no inflar el tamaño del archivo
- Sirve para CONTRASTAR: las gráficas SVG recreadas en las Partes 2 y 3 deben
  coincidir con estas capturas originales; si no coinciden, la recreación está
  mal y debe corregirse.
- NO incluir aquí la imagen del enunciado (esa va en Parte 1)

REGLA TRANSVERSAL SOBRE IMÁGENES (dónde va cada cosa)
- Imágenes/capturas ORIGINALES → solo en dos lugares:
  · Parte 1: la imagen del enunciado tal cual.
  · Verificación: las capturas de Minitab/Excel.
- Partes 2 y 3 → SIEMPRE gráficas recreadas en SVG/HTML (a partir del
  procedimiento y los valores calculados), NUNCA capturas.

FOOTER
- Fondo morado oscuro, texto centrado
- "Práctica Calificada 4 · Control de Calidad Estadístico | Elaborado por
  [Nombre del autor]"

REGLAS TÉCNICAS
- Un solo archivo .html, JS mínimo (solo para cambiar de pestaña)
- Todas las imágenes en base64 dentro del propio HTML (sin archivos externos)
- Debe abrir y verse igual sin conexión a internet (salvo la tipografía web)
```

---

## 🎨 Paleta de referencia rápida

| Elemento | Color |
|---|---|
| Hero (fondo) | `#1e1040` → `#3b1f6b` → `#5c3ba0` |
| Fondo de página | `#f7f5fb` |
| Tarjetas stat (degradado) | `#7a5fc4` → `#3f2478` |
| Acento dorado | `#d4af37` / `#f1d98b` |
| Minitab (línea LCS/LCI) | `#c0392b` (rojo) |
| Minitab (línea LC) | `#2e9e4a` (verde) |
| Minitab (etiqueta/pastilla) | `#2D6FE0` (azul) |
| Excel (línea LCS/LCI) | `#1E8E4E` (verde) |
| Excel (línea LC) | `#e08300` (naranja) |
| Flag "en control / cumple" | fondo `#dcf3e3`, texto `#1E8E4E` |
| Flag "fuera de control / no cumple" | fondo `#fde2e2`, texto `#b3261e` |

## 🔤 Tipografías

| Uso | Fuente |
|---|---|
| Títulos | Playfair Display (600–800) |
| Texto general | Inter (400–700) |
| Valores/fórmulas/etiquetas técnicas | JetBrains Mono (400–600) |

## 📐 Estructura de pestañas (según el caso)

**Un solo problema de un solo tema:**
```
Parte 1: Enunciado + Minitab → Parte 2: Excel → Parte 3: Análisis Estadístico → Verificación
```

**Práctica con los 3 temas (Variables, Atributos, Capacidad):**
```
Tab 1: Gráfica de Control por Variables (Minitab + Excel)
Tab 2: Gráfica de Control por Atributos (Minitab + Excel)
Tab 3: Capacidad de Procesos (Minitab + Excel)
Tab 4: Verificación
```

---

*Este README refleja el formato acordado y usado en los dashboards de Rubi Quispe Sierra para la Práctica Calificada 4. Actualízalo si el formato cambia.*
