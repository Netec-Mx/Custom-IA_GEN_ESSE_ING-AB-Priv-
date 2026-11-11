# Práctica 12. Analizar manuales técnicos, procedimientos, especificaciones, normas o reportes de ingeniería utilizando Claude para identificar inconsistencias, riesgos, acciones pendientes y generar un informe consolidado para apoyar la toma de decisiones del equipo de ingeniería

**Capítulo 3. Plataformas de Inteligencia Artificial para la Ingeniería · Módulo 6. Aplicación de plataformas de IA en proyectos de ingeniería (Claude Projects, grandes ventanas de contexto y organización del conocimiento)**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 14 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Analizar |
| **Herramientas** | Claude (versión gratuita; Projects si la versión disponible lo permite) y Microsoft Word |
| **Archivos** | `DOC1_Procedimiento_Mtto_CA-250.pdf`, `DOC2_Reporte_Inspeccion_CA-250.pdf`, `DOC3_Especificacion_Fabricante_CA-250.pdf` |

## Descripción General

El participante organizará en Claude la documentación de un compresor de aire: el procedimiento de mantenimiento preventivo, el último reporte de inspección y la hoja de especificaciones del fabricante. Aprovechando la ventana de contexto de Claude y, si la versión lo permite, un proyecto con instrucciones del caso, pedirá identificar inconsistencias entre documentos, riesgos técnicos y acciones pendientes con la fuente de cada hallazgo. Verificará las citas contra los documentos originales y generará un informe consolidado para la toma de decisiones del equipo de ingeniería.

La práctica se realiza con Claude en su versión gratuita, ya que forma parte de los objetivos del módulo. El instructor puede reducir el número de documentos según los límites disponibles. Todos los documentos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Organizar documentación técnica en Claude con instrucciones del caso.
- Identificar inconsistencias, riesgos y acciones pendientes entre documentos.
- Verificar cada cita contra el documento original.
- Generar un informe consolidado para la toma de decisiones.

## Prerrequisitos

- Cuenta gratuita de Claude (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado el tema *Claude Projects, grandes ventanas de contexto y organización del conocimiento* del Módulo 6.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Claude | Análisis de la documentación | [claude.ai](https://claude.ai/) |
| Visor de PDF y Microsoft Word | Verificar citas y guardar el informe | Navegador o lector de PDF; Word instalado o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [DOC1_Procedimiento_Mtto_CA-250.pdf](recursos/DOC1_Procedimiento_Mtto_CA-250.pdf) | Procedimiento MTP-CA250-2026-Rev03: condiciones de operación, actividades, criterios de aceptación y acciones pendientes |
| [DOC2_Reporte_Inspeccion_CA-250.pdf](recursos/DOC2_Reporte_Inspeccion_CA-250.pdf) | Reporte de inspección RIT-CA250-2026-002: condiciones encontradas, hallazgos, riesgos y recomendaciones |
| [DOC3_Especificacion_Fabricante_CA-250.pdf](recursos/DOC3_Especificacion_Fabricante_CA-250.pdf) | Hoja de especificaciones del fabricante, revisión 2022 |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlos en `Documentos\Practicas_IA_Ingenieria\Practica12`.

## Instrucciones Paso a Paso

### Paso 1: Organizar la documentación en Claude (3 min)

1. Abrir [claude.ai](https://claude.ai/) e iniciar sesión.
2. Si la opción **Proyectos** (**Projects**) está disponible:
   - Crear el proyecto `Compresor CA-250`.
   - En **Instrucciones del proyecto**, escribir: *"Eres ingeniero de confiabilidad. Responde solo con la información de los documentos del proyecto y cita el documento y la sección de cada dato. Si un dato no está en los documentos, indícalo."*
   - Agregar los 3 PDF en **Conocimiento del proyecto** e iniciar una conversación dentro del proyecto.
3. Si **Proyectos** no está disponible, iniciar una conversación nueva, adjuntar los 3 PDF y pegar las mismas instrucciones al inicio del primer mensaje.

**Resultado esperado:** Los 3 documentos están disponibles para Claude.

**Verificación:** Enviar *"Lista los documentos, su código, su fecha o revisión y su tipo"*: Claude nombra los 3 documentos.

### Paso 2: Identificar inconsistencias entre documentos (4 min)

1. Enviar:

```text
Compara los 3 documentos y entrega una tabla | Aspecto | DOC1 (procedimiento) | DOC2 (inspección) | DOC3 (fabricante) | Inconsistencia | Riesgo (Alto/Medio/Bajo) |.
Compara: rango de presión de descarga, revisión del procedimiento usado, tipo de lubricante, intervalo de cambio de aceite, temperatura máxima de carcasa y límite de vibración.
Cita la sección de cada dato. No supongas información que no esté en los documentos.
```

**Resultado esperado:** Una tabla con las inconsistencias y su fuente.

**Verificación:** La tabla incluye al menos estas inconsistencias:

| Aspecto | Inconsistencia |
| :--- | :--- |
| Presión de descarga | DOC1: 8.5 ±0.3 bar; DOC3 (usado en DOC2): 8.0 ±0.5 bar |
| Revisión del procedimiento | DOC1 es Rev03; DOC2 se basó en Rev02 |
| Lubricante | DOC1 y DOC3: sintético ISO VG 46; DOC2 encontró mineral ISO VG 68 instalado |
| Cambio de aceite | DOC1: 2,000 h (boletín BT-CA-2025-11); DOC3 (revisión 2022): 3,000 h |
| Temperatura máxima de carcasa | DOC1: 60 °C; DOC3: 65 °C |

### Paso 3: Identificar riesgos y acciones pendientes (2 min)

1. Enviar:

```text
Lista los riesgos técnicos y las acciones pendientes del expediente. Para cada acción pendiente indica: origen (documento y sección), antigüedad, responsable si existe y consecuencia de no atenderla. Señala también cualquier pendiente implícito que no esté listado como tal.
```

**Resultado esperado:** Riesgos y acciones pendientes con su fuente.

**Verificación:** Claude identifica la OT-2026-0087 del rodamiento (5.1 mm/s contra límite de 4.5 mm/s), la calibración vencida del MP-112, la hoja de seguridad del lubricante y el filtro de aire con cerca de 620 h. Un buen análisis también señala que la calibración del manómetro MD-220 vence en marzo de 2026, antes de la próxima inspección de mayo.

### Paso 4: Verificar las citas (3 min)

1. Elegir 4 hallazgos de las respuestas.
2. Abrir el PDF citado en cada uno y localizar la sección indicada.
3. En un documento de Word, crear una tabla con **Hallazgo**, **Fuente citada por Claude**, **¿La cita es correcta? (Sí/No)** y **Comentario**.
4. Si una cita es incorrecta, corregirla con la fuente real.

**Resultado esperado:** 4 citas verificadas.

**Verificación:** Cada fila tiene una fuente comprobada en el PDF.

### Paso 5: Generar el informe consolidado (2 min)

1. Enviar:

```text
Genera un informe consolidado para el jefe de ingeniería con: resumen ejecutivo (5 líneas), matriz de inconsistencias, riesgos priorizados, acciones pendientes con responsable y fecha sugerida, decisión recomendada sobre el documento que debe prevalecer en cada inconsistencia y siguientes pasos. Máximo 1 página y media.
```

2. Copiar el informe al documento de Word, debajo de la tabla de verificación, y guardarlo como `Informe_Consolidado_CA-250_[INICIALES].docx`.

**Resultado esperado:** Un informe consolidado con recomendaciones.

**Verificación:** El informe recomienda ejecutar de inmediato la OT-2026-0087 y actualizar o conciliar la especificación del fabricante (revisión 2022) con el procedimiento Rev03.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Cita verificable | Abrir DOC2, sección 2.3 | Vibración de 5.1 mm/s RMS en el rodamiento lado acople |
| Prevalencia de documentos | Revisar la decisión recomendada | Prevalece el documento más reciente y respaldado (DOC1 con el boletín BT-CA-2025-11), sujeto a confirmación del fabricante |
| Prueba adversarial | Preguntar: *"¿Qué dice el DOC2 sobre la presión de aceite del cárter?"* | Claude indica que el DOC2 no menciona ese parámetro |

## Solución de Problemas

### Problema 1: Claude alcanzó el límite de mensajes o de archivos

- **Síntomas:** Mensaje de límite de uso.
- **Causa:** Restricciones de la versión gratuita.
- **Solución:** Combinar los pasos 2 y 3 en un solo mensaje, o continuar más tarde con autorización del instructor.

### Problema 2: Claude da citas generales sin sección

- **Síntomas:** Hallazgos con *"según el procedimiento"* sin número de sección.
- **Causa:** La instrucción de citar no se aplicó de forma estricta.
- **Solución:** Enviar: *"Para cada hallazgo, agrega el documento y el número de sección exacto"*.

## Limpieza

1. Conservar `Informe_Consolidado_CA-250_[INICIALES].docx` en `Documentos\Practicas_IA_Ingenieria\Practica12`.
2. Si la política de la empresa lo indica, eliminar el proyecto o la conversación de Claude.

## Resumen

- Se organizó la documentación de un equipo en Claude con instrucciones del caso.
- Se identificaron inconsistencias, riesgos y acciones pendientes con su fuente.
- Se verificaron las citas y se generó un informe consolidado para la toma de decisiones.

---

[⬅ Anterior: Práctica 11](../Practica11/README.md) | [Inicio](../../README.md)
