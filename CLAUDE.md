# Instrucciones del proyecto — PC4 Control de Calidad Estadístico

Este proyecto corresponde a la Práctica Calificada 4 de Control de Calidad Estadístico de **Allison Rubi**.

## Alcance de edición (obligatorio)

**Archivos/carpetas que SÍ puedes crear o modificar:**
- `css/` (estilos)
- `prompts/` (registro de prompts)
- `index.html`
- `README.md`

**Carpetas de SOLO LECTURA — nunca escribir, editar, renombrar ni borrar nada dentro de ellas:**
- `excel/`
- `img/`
- `minitab/`

Estas tres carpetas contienen los entregables originales (archivos de Excel, capturas/imágenes y proyectos de Minitab) que la autora sube manualmente. Solo puedes **leer** su contenido (por ejemplo, para embeber una imagen en base64 dentro del `index.html`, o para consultar un dato de una hoja de cálculo), pero jamás modificarlas, sobrescribirlas ni generar archivos nuevos dentro de ellas.

Si una tarea pareciera requerir tocar `excel/`, `img/` o `minitab/`, detente y pregunta a la usuaria en vez de escribir ahí.

## Archivos de referencia (guía de decisión — solo lectura)

Antes de generar o modificar cualquier contenido, consulta estos dos documentos como fuente de verdad:

1. **[decision_Control_Calidad_Estadistico.md](decision_Control_Calidad_Estadistico.md)**
   Define **qué** hacer: el árbol de decisión estadístico (variables vs. atributos, tipo de carta, activación de capacidad de procesos), el flujo de trabajo por ejercicio (transcripción → clasificación → cálculo manual → software → conclusiones → dashboard), las fórmulas de referencia y las particularidades de Minitab/Excel.

2. **[diseño_dashboard.md](diseño_dashboard.md)**
   Define **cómo** debe verse: el prompt maestro visual del dashboard HTML (paleta morada, tipografías, estructura de pestañas, colores de gráficas Minitab vs. Excel, secciones obligatorias como Verificación, Conclusiones y Recomendaciones).

Estos dos archivos son de solo lectura: se usan como referencia/guía, no se editan salvo que la usuaria lo pida explícitamente.

## Reglas transversales

- No usar R ni Python en ningún entregable (solo Excel y Minitab).
- Todo cambio en `index.html`, `css/` o `prompts/` debe ser consistente con ambos documentos de referencia.
- Cualquier imagen embebida en el HTML debe provenir de `img/` (leída, nunca modificada).
- Cualquier duda sobre clasificación estadística se resuelve con el árbol de decisión de `decision_Control_Calidad_Estadistico.md`, nunca por criterio propio.
