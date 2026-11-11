# Práctica 8. Analizar indicadores de operación en Excel utilizando Copilot para identificar desviaciones, generar un informe técnico en Word y crear una presentación ejecutiva con recomendaciones de mejora

**Capítulo 3. Plataformas de Inteligencia Artificial para la Ingeniería · Módulo 6. Aplicación de plataformas de IA en proyectos de ingeniería (M365 Copilot Chat)**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 14 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Crear |
| **Herramientas** | Microsoft Copilot Chat (versión gratuita, con carga de archivos), Microsoft Word y PowerPoint |
| **Archivos** | `Indicadores_Operacion_PH400.xlsx` (y `Indicadores_Operacion_PH400.csv` como alternativa) |

## Descripción General

El participante cargará en Microsoft Copilot Chat un archivo de Excel con indicadores de operación de tres semanas (disponibilidad, OEE, scrap, MTBF, tiempo de ciclo y productividad) en las áreas de Ensamble, Inyección y Empaque. Pedirá identificar desviaciones, tendencias y posibles causas, y a partir del análisis obtendrá el contenido de un informe técnico para Word y la estructura de una presentación ejecutiva para PowerPoint con recomendaciones de mejora.

La práctica debe realizarse con Microsoft Copilot, ya que forma parte de los objetivos del módulo, usando Copilot Chat gratuito mediante la carga de archivos, sin licencia Premium ni Copilot integrado en las aplicaciones de Office. Copilot genera el contenido o los entregables descargables; Word y PowerPoint solo se usan para abrirlos o pegar el contenido. El instructor puede simplificar el escenario según los límites de la versión gratuita. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Analizar indicadores de operación con Copilot Chat para identificar desviaciones y tendencias.
- Detectar datos inconsistentes antes de usar el análisis.
- Generar con Copilot el contenido de un informe técnico y de una presentación ejecutiva.

## Prerrequisitos

- Cuenta Microsoft (personal, de trabajo o escuela) con acceso a Copilot Chat (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Conocer los indicadores disponibilidad, OEE, scrap, MTBF y tiempo de ciclo.
- Haber completado la [Práctica 7](../Practica07/README.md).

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Microsoft Copilot Chat | Analizar el archivo y generar el contenido | [copilot.microsoft.com](https://copilot.microsoft.com/) (cuenta personal) o [m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat) (cuenta de trabajo o escuela) |
| Microsoft Word y PowerPoint | Abrir o integrar el informe y la presentación | Instalados en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Indicadores_Operacion_PH400.xlsx](recursos/Indicadores_Operacion_PH400.xlsx) | 20 registros de las semanas S01 a S03 con indicador, área, valor real y meta. Incluye un dato capturado con error |
| [Indicadores_Operacion_PH400.csv](recursos/Indicadores_Operacion_PH400.csv) | Los mismos datos en CSV, por si Copilot no acepta el archivo de Excel |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlos en `Documentos\Practicas_IA_Ingenieria\Practica08`.

## Instrucciones Paso a Paso

### Paso 1: Cargar el archivo y analizar desviaciones (5 min)

**Objetivo:** Obtener el análisis automático de desviaciones y tendencias.

1. Abrir Copilot Chat, iniciar sesión y adjuntar `Indicadores_Operacion_PH400.xlsx` con el botón **+** o el clip. Si no se acepta, adjuntar el CSV.
2. Enviar:

```text
Rol: Eres un ingeniero de mejora continua en una planta de manufactura.
Contexto: El archivo adjunto tiene indicadores de operación de 3 semanas (S01 a S03) por área, con valor real y meta. En disponibilidad, OEE, MTBF y productividad, el valor debe ser mayor o igual a la meta; en scrap y tiempo de ciclo, menor o igual.
Tarea:
1. Antes de analizar, revisa la calidad de los datos e indica cualquier valor inconsistente.
2. Calcula la desviación porcentual de cada registro contra su meta.
3. Identifica las 5 desviaciones más severas y las tendencias de S01 a S03 por indicador.
4. Indica qué indicadores cumplen la meta.
Formato: tablas y viñetas. Usa solo los datos del archivo.
```

**Resultado esperado:** Copilot detecta el valor `12O0` (con letra O) en la productividad de S02 y analiza las desviaciones.

**Verificación:** Comparar con la referencia:

| Hallazgo | Valor correcto |
| :--- | :--- |
| Dato inconsistente | Productividad de S02 capturada como `12O0` |
| Scrap de Inyección | 3.8% → 4.1% → 4.5% contra meta de 2.5% (+80% en S03) |
| MTBF de Empaque | 120 → 115 → 108 h contra meta de 150 h (−28% en S03) |
| OEE de Ensamble | 78.5% → 76.3% → 74.1% contra meta de 85% (−12.8% en S03) |
| Disponibilidad de Ensamble | 94.2% → 91.0% → 89.5% contra meta de 95% |
| Cumple la meta | Disponibilidad de Inyección (96.1% y 95.8%) |

### Paso 2: Pedir causas probables y priorización (2 min)

1. Enviar:

```text
Para las 5 desviaciones más severas, propone 2 causas probables cada una (como hipótesis por verificar), la evidencia que confirmaría cada causa y una prioridad de atención (Alta, Media o Baja). Considera la relación entre MTBF, disponibilidad y OEE.
```

**Resultado esperado:** Causas como hipótesis, relacionadas entre indicadores (por ejemplo, la caída de MTBF y de disponibilidad reduce el OEE).

**Verificación:** Las causas no se presentan como hechos confirmados.

### Paso 3: Generar el informe técnico para Word (3 min)

1. Enviar:

```text
Con el análisis anterior, redacta un informe técnico con: título, resumen ejecutivo (5 líneas), alcance y datos analizados, tabla de desviaciones, análisis de tendencias, causas probables, recomendaciones de mejora con responsable y plazo, y conclusión. Si puedes generar un documento de Word descargable, hazlo.
```

2. Si Copilot ofrece un archivo de Word o un botón para exportar o descargar, descargarlo. Si no, copiar el contenido a un documento nuevo de Word.
3. Guardar como `Informe_Tecnico_Indicadores_[INICIALES].docx`.

**Resultado esperado:** Un informe técnico con las secciones solicitadas.

**Verificación:** La tabla de desviaciones coincide con la referencia del Paso 1.

### Paso 4: Generar la presentación ejecutiva (3 min)

1. Enviar:

```text
Crea una presentación ejecutiva de 6 diapositivas para la gerencia de planta: título, situación actual, 3 desviaciones críticas, tendencias, recomendaciones de mejora y siguientes pasos. Para cada diapositiva indica título, 3 a 4 viñetas y el gráfico sugerido. Si puedes generar un archivo de PowerPoint descargable, hazlo.
```

2. Si Copilot genera un archivo de PowerPoint, descargarlo. Si no, pegar el título y las viñetas de cada diapositiva en una presentación en blanco.
3. Guardar como `Presentacion_Ejecutiva_[INICIALES].pptx`.

**Resultado esperado:** Una presentación de 6 diapositivas con recomendaciones de mejora.

**Verificación:** La diapositiva de recomendaciones incluye responsable y plazo.

### Paso 5: Revisar los entregables (1 min)

1. Verificar que el informe y la presentación usan las mismas cifras.

**Resultado esperado:** Dos entregables consistentes.

**Verificación:** El scrap de Inyección en S03 aparece como 4.5% (+80%) en ambos.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Calidad de datos | Paso 1 | Copilot detecta el valor `12O0` |
| Cifras verificables | Comparar el informe con la tabla del Paso 1 | Coinciden |
| Prueba adversarial | Preguntar: *"¿Cuál fue el scrap de Empaque en S02?"* | Copilot debe indicar que el archivo no tiene scrap de Empaque |

## Solución de Problemas

### Problema 1: Copilot no permite adjuntar el archivo de Excel

- **Síntomas:** El archivo no se carga o el formato no se admite.
- **Causa:** La versión o el tipo de cuenta limita los formatos.
- **Solución:** Cargar el CSV. Si tampoco se acepta, abrir el CSV con el Bloc de notas, copiar el contenido y pegarlo al final del prompt.

### Problema 2: Copilot no genera archivos descargables

- **Síntomas:** Solo entrega texto.
- **Causa:** La función depende de la versión y la región.
- **Solución:** Copiar el contenido a Word y PowerPoint. El objetivo es que Copilot genere el contenido estructurado.

## Limpieza

1. Conservar el informe y la presentación en `Documentos\Practicas_IA_Ingenieria\Practica08`.
2. Si la política de la empresa lo indica, eliminar la conversación y el archivo cargado del historial de Copilot.

## Resumen

- Se analizaron indicadores de operación con Copilot Chat gratuito y se detectó un dato inconsistente.
- Se identificaron desviaciones, tendencias y causas probables.
- Se generaron un informe técnico y una presentación ejecutiva con recomendaciones de mejora.

---

[⬅ Anterior: Práctica 7](../Practica07/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 9 ➡](../Practica09/README.md)
