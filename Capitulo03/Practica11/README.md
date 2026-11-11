# Práctica 11. Analizar una base de datos de producción, mantenimiento o calidad utilizando Advanced Data Analysis para identificar tendencias, anomalías y oportunidades de optimización, generando posteriormente un informe técnico en Canvas

**Capítulo 3. Plataformas de Inteligencia Artificial para la Ingeniería · Módulo 6. Aplicación de plataformas de IA en proyectos de ingeniería (Canvas, Advanced Data Analysis y GPTs)**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 14 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Analizar |
| **Herramientas** | ChatGPT (versión gratuita, con análisis de datos y Canvas) y Microsoft Word |
| **Archivos** | `Calidad_Produccion_PH400.csv` |

## Descripción General

El participante cargará en ChatGPT 120 registros de inspección de la prensa hidráulica PH-400 (presión hidráulica y temperatura del aceite de enero a marzo de 2026). Usará el análisis de datos (Advanced Data Analysis) para limpiar los datos, obtener estadísticas descriptivas y gráficas, identificar anomalías y tendencias, y hacer una aproximación al análisis predictivo. Con los hallazgos, redactará y refinará un informe técnico en Canvas con conclusiones y recomendaciones.

La práctica se realiza con ChatGPT en su versión gratuita, ya que forma parte de los objetivos del módulo. El instructor puede reducir el número de consultas o de gráficas según los límites disponibles. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Limpiar una base de datos técnica con instrucciones en lenguaje natural.
- Obtener estadísticas descriptivas y gráficas por parámetro, turno y mes.
- Identificar anomalías contra los límites del manual y tendencias con una aproximación predictiva.
- Redactar y refinar un informe técnico en Canvas.

## Prerrequisitos

- Cuenta gratuita de ChatGPT (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber completado la [Práctica 9](../Practica09/README.md) (límites de operación de la PH-400).

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| ChatGPT | Análisis de datos, gráficas y Canvas | [chatgpt.com](https://chatgpt.com/) |
| Microsoft Word (escritorio o web) | Guardar el informe final | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Calidad_Produccion_PH400.csv](recursos/Calidad_Produccion_PH400.csv) | 120 registros con fecha, parámetro, valor, unidad, turno, operador y estado. Contiene valores vacíos y anomalías intencionales |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Ingenieria\Practica11`.

**Límites del manual MOP-2026-001:** presión de trabajo de 180 a 250 bar (alarma: más de 260 bar; paro: más de 270 bar). Temperatura del aceite de 35 a 55 °C (alarma: más de 60 °C; paro: más de 65 °C).

## Instrucciones Paso a Paso

### Paso 1: Cargar la base y auditar su calidad (3 min)

1. Abrir ChatGPT, iniciar una conversación nueva y adjuntar `Calidad_Produccion_PH400.csv` con el botón **+** o el clip.
2. Enviar:

```text
Actúa como ingeniero de confiabilidad. Usa la herramienta de análisis de datos para revisar el archivo adjunto:
1. Número de registros, periodo y parámetros.
2. Registros con Valor vacío (muestra fecha y parámetro).
3. Registros fuera de los límites: presión mayor a 260 bar o temperatura mayor a 60 °C.
No modifiques los datos todavía.
```

**Resultado esperado:** 120 registros del 5 de enero al 27 de marzo de 2026, con 3 valores vacíos y 4 registros fuera de límites.

**Verificación:**

| Problema | Registros |
| :--- | :--- |
| Valor vacío | 2026-01-08 (temperatura), 2026-01-16 (presión), 2026-02-24 (temperatura) |
| Fuera de límites | 2026-01-14: 280.3 bar y 68.5 °C; 2026-02-18: 266.2 bar; 2026-03-11: 271.8 bar |

### Paso 2: Limpiar y obtener estadísticas (3 min)

1. Enviar:

```text
Excluye los registros con Valor vacío. Calcula por parámetro: media, mediana, desviación estándar, mínimo y máximo, y la media de temperatura por mes excluyendo las anomalías mayores a 60 °C. Genera una gráfica de líneas de la temperatura del aceite por fecha con líneas horizontales en 55 °C y 60 °C.
```

**Resultado esperado:** Estadísticas por parámetro y una gráfica con tendencia ascendente de temperatura.

**Verificación:** La media mensual de temperatura es de aproximadamente **52.6 °C en enero, 54.0 °C en febrero y 55.7 °C en marzo**.

### Paso 3: Identificar anomalías y estimar la tendencia (3 min)

1. Enviar:

```text
1. Clasifica las 4 anomalías según los límites del manual (alarma o paro de emergencia).
2. Ajusta una tendencia lineal a la temperatura del aceite (sin anomalías) e indica cuántos °C sube por mes y en qué fecha aproximada la media alcanzaría 60 °C si la tendencia continúa. Indica las limitaciones de esta estimación.
3. Propón 3 oportunidades de optimización basadas en los datos.
```

**Resultado esperado:** 280.3 bar, 271.8 bar y 68.5 °C superan los límites de paro de emergencia; 266.2 bar está en alarma. La temperatura sube cerca de **1.5 a 1.6 °C por mes** y la media alcanzaría 60 °C hacia **junio de 2026** (con una regresión lineal por fecha, alrededor del 9 de junio).

**Verificación:** ChatGPT aclara que la estimación es una extrapolación lineal con solo 3 meses de datos y no sustituye un modelo predictivo validado.

### Paso 4: Redactar el informe técnico en Canvas (3 min)

1. Enviar:

```text
Abre Canvas y redacta un informe técnico titulado "Análisis de presión y temperatura de la PH-400, enero a marzo de 2026" con: 1. Resumen ejecutivo, 2. Datos y limpieza, 3. Estadísticas, 4. Anomalías, 5. Tendencia y estimación predictiva, 6. Recomendaciones. Usa las cifras exactas del análisis.
```

2. Si Canvas no se abre, seleccionar **Canvas** en las herramientas del cuadro de mensaje y repetir.

**Resultado esperado:** El informe aparece en Canvas con 6 secciones.

**Verificación:** El resumen ejecutivo menciona la tendencia ascendente de temperatura y las 4 anomalías.

### Paso 5: Refinar y guardar el informe (2 min)

1. En Canvas, seleccionar la sección **6. Recomendaciones** y escribir en el cuadro que aparece:

```text
Reescribe esta sección con 3 acciones: revisión del intercambiador de calor y del radiador (MOP-2026-001, sección 5.3), análisis de aceite inmediato y criterio de paro cuando la temperatura supere 60 °C. Incluye responsable y plazo.
```

2. Copiar el contenido de Canvas a Word y guardarlo como `Informe_Tecnico_PH400_[INICIALES].docx`.
3. Opcional: en el menú lateral de ChatGPT, abrir **GPT** y buscar asistentes de *mantenimiento* o *confiabilidad*. Antes de usarlos con datos de la empresa, revisar quién los creó y su política de datos.

**Resultado esperado:** Informe guardado en Word.

**Verificación:** La sección 6 tiene 3 acciones con responsable y plazo.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Calidad de datos | Paso 1 | 3 vacíos y 4 anomalías detectados |
| Cifras verificables | Paso 2 | Medias mensuales cercanas a 52.6, 54.0 y 55.7 °C |
| Prueba adversarial | Preguntar: *"¿Cuál fue la vibración de la prensa en febrero?"* | ChatGPT indica que la base no contiene vibración |

## Solución de Problemas

### Problema 1: ChatGPT no ejecuta el análisis

- **Síntomas:** Solo describe el archivo, sin tablas ni gráficas.
- **Causa:** La carga falló o se alcanzó el límite de análisis del plan gratuito.
- **Solución:** Volver a adjuntar el archivo y comenzar con *"Usa la herramienta de análisis de datos para calcular..."*. Si se alcanzó el límite, esperar o continuar con el instructor.

### Problema 2: Canvas no está disponible

- **Síntomas:** No aparece la opción Canvas.
- **Causa:** Disponibilidad variable en el plan gratuito.
- **Solución:** Pedir el informe en la conversación y refinar la sección 6 con un mensaje que indique qué cambiar.

## Limpieza

1. Conservar el informe en `Documentos\Practicas_IA_Ingenieria\Practica11`.
2. Si la política de la empresa lo indica, eliminar la conversación del historial de ChatGPT.

## Resumen

- Se limpió y analizó una base de 120 registros con instrucciones en lenguaje natural.
- Se identificaron anomalías contra los límites del manual y una tendencia ascendente de temperatura con una estimación predictiva básica.
- Se redactó y refinó un informe técnico en Canvas.

---

[⬅ Anterior: Práctica 10](../Practica10/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 12 ➡](../Practica12/README.md)
