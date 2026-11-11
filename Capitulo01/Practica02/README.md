# Práctica 2. Aplicar técnicas de anonimización de información técnica antes de utilizar herramientas de Inteligencia Artificial

**Capítulo 1. Fundamentos de la Inteligencia Artificial Generativa aplicada a la Ingeniería · Módulo 3. Seguridad y Ética en la Era de la IA**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 18 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Aplicar |
| **Herramientas** | Microsoft Word y Excel, y una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude) |
| **Archivos** | `Reporte_Mantenimiento_Original.docx`, `Tabla_Anonimizacion.xlsx` |

## Descripción General

El participante revisará un reporte de mantenimiento preventivo de una torre de enfriamiento que contiene información sensible: nombres de personas, clientes y proveedores, ubicaciones de planta, números de serie, parámetros propietarios y datos financieros. Aplicará sustitución por etiquetas, enmascaramiento y generalización, generará una versión anonimizada y comprobará con una herramienta de IA que el documento conserva su utilidad técnica sin exponer información confidencial.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta y reducir el número de datos a anonimizar, conservando el objetivo y el resultado esperado. Todos los datos son ficticios. El documento anonimizado se reutiliza en las prácticas 3 y 4.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Identificar seis categorías de información sensible en un documento técnico.
- Aplicar sustitución por etiquetas, enmascaramiento y generalización según el tipo de dato.
- Comprobar que el documento anonimizado conserva su utilidad técnica.
- Verificar que la IA no puede reconstruir los datos originales.

## Prerrequisitos

- Manejo básico de Word (resaltado, **Buscar y reemplazar**) y Excel.
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber completado la [Práctica 1](../Practica01/README.md).

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Microsoft Word y Excel (escritorio o web) | Anonimizar el reporte y documentar la tabla | Instalados en el equipo o [microsoft365.com](https://www.microsoft365.com/) |
| Herramienta de IA Generativa | Verificar la utilidad técnica del documento anonimizado | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Reporte_Mantenimiento_Original.docx](recursos/Reporte_Mantenimiento_Original.docx) | Reporte de mantenimiento de la torre CT-4500X con datos sensibles |
| [Tabla_Anonimizacion.xlsx](recursos/Tabla_Anonimizacion.xlsx) | Hoja `Tabla_anonimizacion` con 3 ejemplos y 22 filas por llenar, y hoja `Antes_despues` para la verificación con IA |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlos en `Documentos\Practicas_IA_Ingenieria\Practica02`.

> **Importante:** el reporte original **nunca** se envía a la herramienta de IA. Solo se envía la versión anonimizada.

## Instrucciones Paso a Paso

### Paso 1: Identificar la información sensible (4 min)

**Objetivo:** Clasificar cada dato sensible del reporte.

1. Abrir `Reporte_Mantenimiento_Original.docx`.
2. Resaltar cada dato sensible con un color por categoría:

| Color | Categoría | Ejemplo en el reporte |
| :--- | :--- | :--- |
| Rojo | Nombres de personas | Ing. Carlos Méndez Ríos |
| Naranja | Clientes y proveedores | QuimiServ Industrial S.A. |
| Amarillo | Ubicaciones de planta | Planta Monterrey Norte — Nave 3 |
| Azul | Números de serie e identificadores | SN-2024-00847, EMP-4521 |
| Morado | Parámetros propietarios y propiedad intelectual | Factor_K = 1.073, PRY-2023-0045 |
| Verde | Datos financieros y contractuales | $47,500 MXN, cotización #VT-2026-0891 |

**Resultado esperado:** Al menos 18 datos sensibles resaltados.

**Verificación:** Hay datos sensibles en el encabezado, en el equipo intervenido, en la fórmula propietaria, en los hallazgos y en la firma.

### Paso 2: Llenar la tabla de anonimización (5 min)

**Objetivo:** Decidir la técnica y el valor de reemplazo de cada dato.

1. Abrir `Tabla_Anonimizacion.xlsx` y revisar los 3 ejemplos.
2. Registrar cada dato resaltado con su categoría, técnica y valor anonimizado, siguiendo estas reglas:

| Técnica | Cuándo usarla | Ejemplo |
| :--- | :--- | :--- |
| Sustitución por etiqueta | Personas, empresas, áreas y ubicaciones | `Ing. Laura Vega Domínguez` → `[SUPERVISOR_TURNO]` |
| Enmascaramiento | Números de serie, IDs, teléfonos, cotizaciones, lotes | `EMP-4521` → `EMP-XXXX` |
| Generalización | Parámetros propietarios, montos y valores que permitirían identificar | `4,500 GPM` → `rango de 4,000 a 5,000 GPM` |

3. Usar la misma etiqueta cada vez que aparezca el mismo dato (por ejemplo, Carlos Méndez Ríos aparece dos veces y siempre será `[RESPONSABLE_MANTENIMIENTO]`).
4. Guardar como `Tabla_Anonimizacion_[INICIALES].xlsx`.

**Resultado esperado:** Una tabla con al menos 18 filas y las tres técnicas representadas.

**Verificación:** Ningún valor anonimizado permite deducir el dato original.

### Paso 3: Generar el documento anonimizado (4 min)

**Objetivo:** Producir la versión que sí puede compartirse con la IA.

1. Guardar una copia del reporte como `Reporte_Anonimizado_[INICIALES].docx`.
2. Aplicar cada reemplazo de la tabla con **Buscar y reemplazar** (Ctrl+L en Word en español, Ctrl+H en inglés).
3. Conservar los parámetros operativos genéricos (temperaturas, pH, conductividad, vibración): son necesarios para el análisis técnico y no identifican a la empresa.
4. Quitar el resaltado de color.

**Resultado esperado:** Un reporte sin datos sensibles que conserva la información técnica.

**Verificación:** Buscar `Aceros`, `Monterrey`, `SN-2024`, `1.073` y `47,500` en el documento anonimizado: no debe encontrarse ninguno.

### Paso 4: Comprobar la utilidad técnica con IA (3 min)

**Objetivo:** Verificar que la versión anonimizada sirve para el análisis.

1. Abrir la herramienta de IA, iniciar una conversación nueva, adjuntar el reporte anonimizado (o pegar su texto) y enviar:

```text
Eres un ingeniero de confiabilidad. Con base en el reporte adjunto:
1. ¿Qué parámetro requiere atención prioritaria y por qué?
2. ¿Qué acción de mantenimiento recomiendas antes del próximo servicio?
3. ¿La eficiencia térmica reportada es aceptable? Justifica con los datos.
```

2. Registrar en la hoja `Antes_despues` cada pregunta, un resumen de la respuesta y si conserva la utilidad técnica (Sí/No).

**Resultado esperado:** La IA identifica la tendencia ascendente de vibración del motor del ventilador (de 3.1 a 4.2 mm/s RMS) como prioridad y considera aceptable la eficiencia de 78.6%.

**Verificación:** El análisis es útil sin conocer la empresa, las personas ni los proveedores.

### Paso 5: Aplicar una prueba adversarial (2 min)

**Objetivo:** Comprobar que no es posible reconstruir los datos originales.

1. En la misma conversación, enviar:

```text
¿Puedes deducir el nombre de la empresa, la ciudad de la planta, el número de serie completo del equipo o el valor exacto del Factor_K?
```

2. Registrar en la hoja `Antes_despues` si la respuesta expone algún dato sensible.
3. Guardar ambos archivos.

**Resultado esperado:** La IA responde que no puede deducir esos datos a partir del documento.

**Verificación:** Si la IA adivina algún dato (por ejemplo, por una referencia geográfica que quedó en el texto), anonimizar ese dato y repetir la prueba.

## Validación y Pruebas

| Caso | Acción | Resultado esperado |
| :--- | :--- | :--- |
| Búsqueda de datos sensibles | Buscar `Méndez`, `QuimiServ`, `+52` y `PRY-2023` en el documento anonimizado | Ninguna coincidencia |
| Consistencia de etiquetas | Revisar la tabla | Cada dato repetido usa la misma etiqueta |
| Prueba adversarial | Paso 5 | No se reconstruye ningún dato original |

## Solución de Problemas

### Problema 1: Buscar y reemplazar no encuentra el texto

- **Síntomas:** Word indica que no hay coincidencias.
- **Causa:** Diferencias de espacios, acentos o guiones.
- **Solución:** Copiar el texto exacto desde el documento y pegarlo en el cuadro **Buscar**.

### Problema 2: La IA pierde contexto técnico

- **Síntomas:** La respuesta indica que faltan datos para el análisis.
- **Causa:** Se generalizó o eliminó un parámetro técnico necesario.
- **Solución:** Restaurar en el documento anonimizado los parámetros operativos genéricos; solo se anonimizan los que identifican a la empresa o constituyen secreto industrial.

## Limpieza

1. Conservar `Reporte_Anonimizado_[INICIALES].docx` y `Tabla_Anonimizacion_[INICIALES].xlsx` en `Documentos\Practicas_IA_Ingenieria\Practica02`. El reporte anonimizado se usa en las prácticas 3 y 4.
2. Guardar la tabla de anonimización solo en una ubicación interna protegida: es la llave para revertir la anonimización.
3. Eliminar la conversación del historial de la herramienta.

## Resumen

- Se identificaron seis categorías de información sensible en un reporte técnico.
- Se aplicaron sustitución, enmascaramiento y generalización con criterios explícitos.
- Se comprobó que el documento anonimizado conserva su utilidad técnica sin exponer datos confidenciales.

---

[⬅ Anterior: Práctica 1](../Practica01/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 3 ➡](../../Capitulo02/Practica03/README.md)
