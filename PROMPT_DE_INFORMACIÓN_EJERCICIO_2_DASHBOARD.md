# README — Ejercicio: Carta p (Artículos Defectuosos)

**Curso:** Control de Calidad Estadístico — Práctica Calificada 4
**Autora:** Rubi Quispe Sierra
**Documento base usado:** `decision_Control_Calidad_Estadistico.md`

Este README documenta **todas las decisiones tomadas** y **toda la respuesta generada** para este ejercicio específico, siguiendo el flujo de trabajo definido en el documento maestro del curso.

---

## 1. Enunciado transcrito y confirmado

> Para analizar la estabilidad de la cantidad de artículos defectuosos en un proceso de producción y tratar de mejorarlo, se toma una muestra de 120 piezas cada cuatro horas, mediante el método del intervalo. Los datos obtenidos durante seis días se muestran en la tabla adjunta (20 muestras, n = 120 cada una).

**Preguntas del enunciado:**
a) ¿Cuál carta recomendaría?
b) Mediante una carta p, analice los datos y comente los resultados.
c) ¿Cómo explicaría los límites de control que obtuvo?
d) Si se sugiere fijar el LCS de la carta p en 0.10 (tolerancia de costos = 10%), ¿es correcta esta sugerencia?

**Datos clave identificados:** n = 120 constante, 20 muestras, se cuentan artículos defectuosos (unidades, no defectos).

Este paso siguió el punto 1 del flujo de trabajo del documento maestro: *"Transcripción del enunciado — Claude transcribe el problema completo y pregunta si la transcripción es correcta. No avanza sin confirmación."* La transcripción fue confirmada por Pixie antes de continuar.

---

## 2. Clasificación del tema y justificación (decisión tomada)

Siguiendo la sección 3 del documento maestro (árbol de decisión Variables vs. Atributos vs. Capacidad):

| Pregunta clave | Respuesta según el enunciado | Conclusión / alternativas descartadas |
|---|---|---|
| ¿Medición continua o de atributos? | Se cuentan "artículos defectuosos" (pasa/no pasa) | **Atributos** — se descarta la rama Variables (X̄-R, X̄-S, X-Rm) |
| ¿Se cuentan unidades defectuosas o defectos por unidad? | Cada pieza se clasifica como buena o mala (no hay conteo de múltiples defectos por pieza) | **Rama de unidades defectuosas (p/np)** — se descartan c y u |
| ¿n constante o variable? | n = 120 en las 20 muestras (constante) | Con n constante, p y np son matemáticamente equivalentes. Se elige **p** porque: (1) el enunciado la exige explícitamente en (b); (2) expresa el resultado como proporción, comparable directamente con la tolerancia del 10% de la parte (d). Se **descarta np** |
| ¿Se activa el bloque de Capacidad de Procesos (Cp/Cpk/Cpm)? | Se menciona una tolerancia del 10%, pero es un límite único sobre una proporción de atributo, no una especificación EI/ES sobre variable continua con σ | **No se activa** el bloque de capacidad — esos índices (sección 4.3 del documento maestro) requieren datos continuos. La tolerancia se usa solo conceptualmente en la parte (d) |

**Decisión final: Carta p.**

Esta es la única desviación notable respecto a una aplicación mecánica del árbol de decisión: aunque el criterio 3.4 del documento maestro (activación de capacidad) se dispara literalmente ante la palabra "tolerancia", se decidió **no** aplicar Cp/Cpk/Cpm porque las fórmulas de la sección 4.3 son estructuralmente incompatibles con datos de atributos (proporciones), y el enunciado en realidad está probando la distinción conceptual entre límite de control y límite de especificación, no pidiendo un cálculo de capacidad.

---

## 3. Organización de datos (tabla generada)

Se generó una tabla única de 20 filas (Muestra | np | n | p = np/n), en formato listo para copiar/pegar tanto en Minitab como en Excel, calculando p para cada muestra:

| Muestra | np | p | Muestra | np | p |
|---|---|---|---|---|---|
| 1 | 11 | 0.0917 | 11 | 8 | 0.0667 |
| 2 | 10 | 0.0833 | 12 | 7 | 0.0583 |
| 3 | 7 | 0.0583 | 13 | 9 | 0.0750 |
| 4 | 10 | 0.0833 | 14 | 6 | 0.0500 |
| 5 | 4 | 0.0333 | 15 | 6 | 0.0500 |
| 6 | 12 | 0.1000 | 16 | 11 | 0.0917 |
| 7 | 8 | 0.0667 | 17 | 9 | 0.0750 |
| 8 | 5 | 0.0417 | 18 | 7 | 0.0583 |
| 9 | 14 | 0.1167 | 19 | 6 | 0.0500 |
| 10 | 12 | 0.1000 | 20 | 10 | 0.0833 |

Σnp = 172, Σn = 2400 (n=120 × 20 muestras)

---

## 4. Cálculo manual (fórmulas aplicadas — sección 4.2 del documento maestro)

$$\bar{p} = \frac{\Sigma np}{\Sigma n} = \frac{172}{2400} = 0.0717 \;(7.17\%)$$

$$\sigma_p = \sqrt{\frac{\bar p(1-\bar p)}{n}} = \sqrt{\frac{0.0717 \times 0.9283}{120}} = 0.02355$$

| Línea | Valor calculado |
|---|---|
| LCS (p̄+3σp) | 0.1423 |
| +2σ | 0.1188 |
| +1σ | 0.0952 |
| LC (p̄) | 0.0717 |
| −1σ | 0.0481 |
| −2σ | 0.0246 |
| LCI (p̄−3σp) | 0.0010 (positivo → se conserva, no se trunca a cero) |

**Nota de precisión:** se mantuvo σp con 5–6 decimales (0.023546) durante todo el cálculo intermedio antes de redondear el resultado final a 4 decimales, para evitar arrastrar error de redondeo hacia LCS/LCI.

---

## 5. Visualización generada — decisión de diseño

**Decisión:** se generó un gráfico interactivo (Chart.js, vía la herramienta de visualización) en lugar de solo texto/tablas, porque:
- Este ejercicio trata literalmente sobre una carta de **control** — el juicio de estabilidad (parte b) es inherentemente visual (puntos dentro/fuera de límites, ausencia de rachas).
- Sirve como vista previa de referencia para que Pixie contraste contra su propia gráfica hecha en Minitab/Excel.

**Contenido del gráfico:**
- Línea de datos (p) en azul, con la muestra 9 (p = 0.1167, el valor más alto) resaltada en color distinto, ya que es el punto usado como ejemplo concreto en la respuesta de la parte (d).
- Líneas de referencia horizontales: LCS y LCI en rojo (punteado), LC en verde — replicando el esquema de colores de Minitab definido en el documento maestro (sección 5 y 6).
- Sin líneas de ±1σ/±2σ en el gráfico de vista previa (se mantuvieron solo en la tabla de referencia para Minitab), para no sobrecargar visualmente una vista de confirmación rápida.

**Resultado:** los 20 puntos cayeron dentro de LCI–LCS, sin rachas ni tendencias — confirmando visualmente la conclusión de estabilidad.

---

## 6. Instrucciones de software generadas

### Minitab 18 (workaround aplicado por la limitación de la versión — sección 5 del documento maestro)

Dado que Minitab 18 no genera la carta p nativa con datos resumidos, se aplicó el workaround estándar:
1. Ingresar columna **p** (calculada o pegada)
2. `Gráfica → Gráfica de Series de Tiempo → Simple` → Variable: p
3. Doble clic sobre la gráfica → clic derecho → `Agregar → Línea de referencia`
4. Pegar en "Valores de referencia para el eje Y": `0.1423 0.1188 0.0952 0.0717 0.0481 0.0246 0.0010`
5. Colorear: LCS/LCI = rojo, LC = verde, ±1SL/±2SL = negro o gris (vía pestaña Atributos)

### Excel

1. Tabla larga generada: Muestra | p | LCS | LC | LCI (20 filas, límites repetidos por fila)
2. `Insertar → Gráficos recomendados → Línea con marcadores`
3. Colores: p = azul, LCS/LCI = verde, LC = naranja (convención Excel del documento maestro)
4. Eje Y fijado de 0 a 0.16

---

## 7. Respuestas generadas a las preguntas del enunciado

**a) Carta recomendada:** p — justificada por atributos + unidades defectuosas + n constante, con preferencia sobre np por la comparabilidad porcentual requerida en (d).

**b) Análisis y comentario:** los 20 puntos (rango 0.0333–0.1167) están dentro de LCI (0.0010) y LCS (0.1423), sin rachas ni tendencias → proceso **estadísticamente estable**.

**c) Explicación de los límites:** LCS/LCI = p̄ ± 3σp representan la variación de causa común esperada dado el desempeño actual del proceso (p̄ = 7.17%, n = 120); un punto fuera de estos límites señalaría una causa asignable a investigar. LCI se conservó por ser positivo.

**d) ¿Es correcta la sugerencia de LCS = 0.10?** **No.** Se identificó como el error clásico de confundir un **límite de control** (voz del proceso, calculado de los datos: 0.1423) con un **límite de especificación/tolerancia** (voz del negocio: 0.10). Se usó la muestra 9 (p = 0.1167) como evidencia concreta: está dentro del LCS real, pero aparecería como "fuera de control" bajo el umbral sugerido de 0.10, generando una falsa alarma (error tipo I). Se recomendó mantener ambos análisis por separado (control de estabilidad vs. comparación de p̄ contra la tolerancia).

---

## 8. Conclusiones generadas

- Proceso estadísticamente estable en el periodo analizado (sin puntos fuera de control, sin patrones no aleatorios).
- p̄ = 7.17%, por debajo de la tolerancia de costos (10%) → desempeño promedio aceptable, análisis independiente de la estabilidad.
- La sugerencia de fijar LCS = 0.10 es estadísticamente incorrecta (mezcla límite de control con límite de especificación).

## 9. Recomendaciones generadas

- Monitorear con los límites calculados (0.1423 / 0.0717 / 0.0010), no con el umbral de costos.
- Tratar el 10% de tolerancia como KPI de negocio separado, comparado contra p̄.
- Si se busca reducir el nivel de defectuosos, iniciar un proyecto de mejora de proceso (no redefinir límites estadísticamente).
- Investigar informalmente las causas de la muestra 9 (máximo) y muestra 5 (mínimo) como buena práctica, sin tratarlas como señales de descontrol.
- Continuar recolectando datos para ampliar la base de 20 muestras.

---

## 10. Decisiones de formato pendientes / siguientes pasos

- **No se generó aún el dashboard HTML** (paso 7 del flujo de trabajo): se decidió preguntar primero si Pixie quiere consolidarlo con más ejercicios de la Práctica Calificada 4 o generarlo ya solo con este ejercicio, dado que el documento maestro especifica una estructura de dashboard multi-pestaña por tema, normalmente pensada para varios ejercicios juntos.
- Ninguna sección de Cp/Cpk/Cpm/K ni clasificación cruzada capacidad×estabilidad (sección 3.5 del documento maestro) aplica a este ejercicio, por las razones explicadas en la sección 2 de este README.
