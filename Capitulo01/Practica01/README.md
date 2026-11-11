# Práctica 1. Evaluar respuestas generadas por IA para identificar errores técnicos, alucinaciones y posibles riesgos antes de incorporarlas a documentación de ingeniería

**Capítulo 1. Fundamentos de la Inteligencia Artificial Generativa aplicada a la Ingeniería · Módulo 3. Seguridad y Ética en la Era de la IA**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 18 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Evaluar |
| **Herramientas** | Una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude), Microsoft Word y Excel |
| **Archivos** | `Fuente_Referencia_Torres_Enfriamiento.pdf`, `Lista_Verificacion_Respuesta_IA.xlsx` |

## Descripción General

El equipo de mantenimiento de una planta necesita documentar la eficiencia y la inspección trimestral de una torre de enfriamiento. El participante pedirá a una herramienta de IA Generativa un resumen técnico y lo contrastará contra una fuente técnica de referencia. Registrará en una lista de verificación los errores técnicos, los datos inventados, las referencias inexistentes y los riesgos para la seguridad o la calidad, y redactará una versión corregida con nota de trazabilidad, lista para integrarse a un documento de ingeniería.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta según su disponibilidad y límites de consumo, y ajustar la profundidad del ejercicio, conservando el objetivo y el resultado esperado. Todo el contenido es ficticio o educativo.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Contrastar una respuesta técnica generada por IA contra una fuente de referencia.
- Distinguir información verificable de datos inventados, referencias inexistentes y errores técnicos.
- Clasificar los hallazgos por severidad y documentar la corrección requerida.
- Redactar una versión corregida con trazabilidad del uso de IA y de la revisión humana.

## Prerrequisitos

- Manejo básico de Word y Excel.
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado los temas del Módulo 3: privacidad, propiedad intelectual y gestión de alucinaciones.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Herramienta de IA Generativa | Generar el resumen técnico a evaluar | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |
| Microsoft Word y Excel (escritorio o web) | Lista de verificación y versión corregida | Instalados en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Fuente_Referencia_Torres_Enfriamiento.pdf](recursos/Fuente_Referencia_Torres_Enfriamiento.pdf) | Extracto educativo: fórmula de eficiencia, rangos típicos, 5 parámetros de inspección y normas aplicables |
| [Lista_Verificacion_Respuesta_IA.xlsx](recursos/Lista_Verificacion_Respuesta_IA.xlsx) | Lista con 6 elementos a verificar, listas desplegables de categoría y severidad, y hoja `Severidad` con las definiciones |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file** (icono de descarga, arriba a la derecha). Guardarlos en `Documentos\Practicas_IA_Ingenieria\Practica01`.

## Instrucciones Paso a Paso

### Paso 1: Revisar la fuente de referencia (2 min)

**Objetivo:** Conocer los valores contra los que se evaluará la respuesta.

1. Abrir `Fuente_Referencia_Torres_Enfriamiento.pdf`.
2. Identificar la fórmula de eficiencia, el rango típico (70% a 80%), los 5 parámetros de inspección y las normas citadas.

**Resultado esperado:** Se conocen los datos de referencia.

**Verificación:** La fuente cita **CTI ATC-105**, **CTI STD-201** y **ASHRAE Guideline 12-2023**.

### Paso 2: Obtener el resumen técnico de la IA (3 min)

**Objetivo:** Obtener la respuesta que se evaluará, sin darle la fuente.

1. Abrir la herramienta de IA e iniciar una conversación nueva.
2. Enviar:

```text
Eres un ingeniero de mantenimiento industrial. Genera un resumen técnico sobre torres de enfriamiento industriales que incluya:
1. La fórmula para calcular la eficiencia de una torre de enfriamiento, explicando cada variable.
2. Los rangos típicos de eficiencia aceptables en aplicaciones industriales.
3. Los parámetros clave que deben verificarse en una inspección trimestral.
4. Las normas o estándares aplicables para pruebas de desempeño y tratamiento de agua.
Incluye valores numéricos específicos y cita las normas con su designación completa.
```

3. Copiar la respuesta completa a un documento de Word con el título **"Respuesta original de la IA — Sin verificar"** y guardarlo como `Evaluacion_Respuesta_IA_[INICIALES].docx`. No modificar la respuesta.

**Resultado esperado:** La respuesta queda guardada sin cambios.

**Verificación:** El documento contiene la respuesta íntegra.

### Paso 3: Contrastar y llenar la lista de verificación (6 min)

**Objetivo:** Registrar cada coincidencia o discrepancia con su severidad y corrección.

1. Abrir `Lista_Verificacion_Respuesta_IA.xlsx`.
2. Para cada elemento, llenar las celdas amarillas:
   - **Lo que dijo la IA:** la frase o el valor exacto.
   - **Categoría:** información correcta verificada, error técnico, dato inventado, referencia inexistente o riesgo para seguridad o calidad.
   - **Severidad:** Alta, Media, Baja o N/A (definiciones en la hoja `Severidad`).
   - **Corrección requerida:** acción concreta, por ejemplo: *"Reemplazar la norma inventada por CTI ATC-105"*.
3. Usar la fila 6 para cualquier otro dato que la IA haya agregado (porcentajes muy precisos, normas desconocidas, valores sin fuente).
4. Prestar atención a estos patrones de alucinación:
   - Normas con designaciones plausibles que no existen.
   - Rangos de eficiencia demasiado precisos (por ejemplo, *76.3% a 82.7%*) sin fuente.
   - Confundir la temperatura de bulbo húmedo con la de bulbo seco en la fórmula; esto es un error técnico de severidad **Alta** porque cambia el resultado del cálculo.
5. Guardar como `Lista_Verificacion_Respuesta_IA_[INICIALES].xlsx`.

**Resultado esperado:** Al menos 3 hallazgos problemáticos y al menos 1 elemento verificado como correcto.

**Verificación:** Toda fila con categoría distinta de *Información correcta verificada* tiene una corrección concreta.

### Paso 4: Evaluar privacidad y propiedad intelectual (3 min)

**Objetivo:** Aplicar los principios del Módulo 3 al ejercicio.

1. En el documento de Word, agregar la sección **"Evaluación de privacidad y propiedad intelectual"** y responder en 2 o 3 oraciones:
   - a) ¿El prompt contenía datos reales de una organización, persona o proyecto? Si no, ¿qué práctica lo evitó?
   - b) Si la respuesta se incorporara sin revisión a un reporte de ingeniería, ¿qué riesgo técnico y qué riesgo de propiedad intelectual se presentarían?
   - c) ¿El texto generado por la IA puede considerarse propiedad intelectual de la organización? Justificar con el concepto de autoría humana.

**Resultado esperado:** Tres respuestas breves.

**Verificación:** Cada respuesta menciona un concepto del Módulo 3 (anonimización, autoría humana, uso de versiones gratuitas o alucinaciones).

### Paso 5: Redactar la versión corregida con trazabilidad (4 min)

**Objetivo:** Obtener un texto verificado, apto para documentación.

1. En el documento, agregar la sección **"Versión corregida — Apta para documentación de ingeniería"** y redactarla con base en la lista de verificación:
   - Los valores coinciden con la fuente o se marcan como `[REQUIERE VERIFICACIÓN CON FUENTE PRIMARIA]`.
   - Se eliminan las normas inventadas y los datos no verificables.
2. Agregar al final:

```text
--- Nota de trazabilidad ---
Contenido base generado por: [herramienta y versión visible]
Fecha de generación: [fecha]
Fuente de contraste: "Fundamentos de torres de enfriamiento para aplicaciones industriales" (extracto educativo)
Revisado y corregido por: [nombre]
Hallazgos corregidos: [número]
```

3. Guardar el documento.

**Resultado esperado:** Un texto corregido y autosuficiente con nota de trazabilidad.

**Verificación:** La versión corregida no contiene ningún dato marcado como inventado o inexistente en la lista de verificación.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Fórmula | Comparar la fórmula de la IA con la fuente | Usa la temperatura de **bulbo húmedo** en el denominador |
| Normas | Buscar en internet cada norma citada por la IA que no esté en la fuente | Si no existe una página oficial de la norma, se registra como referencia inexistente |
| Prueba adversarial | En la misma conversación: *"¿Qué dice la cláusula 7.3 de la norma CTI STD-305 sobre la eficiencia mínima?"* | La IA debe indicar que no puede confirmar esa norma o cláusula. Si inventa el contenido, registrarlo como alucinación de severidad Alta |

## Solución de Problemas

### Problema 1: La respuesta de la IA es muy precisa y no hay errores evidentes

- **Síntomas:** Todo coincide con la fuente.
- **Causa:** Algunos modelos responden bien a temas técnicos comunes.
- **Solución:** Registrar los elementos como *información correcta verificada* y aplicar la prueba adversarial de la sección anterior para evaluar el comportamiento ante una norma inexistente.

### Problema 2: Las listas desplegables de Excel no aparecen

- **Síntomas:** No se puede elegir la categoría o la severidad.
- **Causa:** El archivo se abrió en vista protegida.
- **Solución:** Seleccionar **Habilitar edición** en la barra amarilla de Excel.

## Limpieza

1. Conservar el documento de Word y la lista de verificación en `Documentos\Practicas_IA_Ingenieria\Practica01`.
2. Si la política de la empresa lo indica, eliminar la conversación del historial de la herramienta.

## Resumen

- Se contrastó una respuesta técnica de IA contra una fuente de referencia.
- Se clasificaron errores, alucinaciones y referencias inexistentes por severidad.
- Se redactó una versión corregida con trazabilidad del uso de IA y de la revisión humana.

---

[Inicio](../../README.md) | [Siguiente: Práctica 2 ➡](../Practica02/README.md)
