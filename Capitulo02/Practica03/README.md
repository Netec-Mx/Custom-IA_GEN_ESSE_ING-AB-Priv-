# Práctica 3. Diseñar prompts para redactar especificaciones técnicas, elaborar procedimientos, analizar requerimientos, generar reportes de ingeniería y documentar proyectos

**Capítulo 2. Ingeniería de Prompts y Automatización para Procesos de Ingeniería · Módulo 4. Fundamentos de la ingeniería de prompts**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 20 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Crear |
| **Herramientas** | Una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude) y Microsoft Word |
| **Archivos** | `Plantilla_Prompts_Ingenieria.docx` |

## Descripción General

El participante construirá cinco prompts con la estructura de rol, contexto, tarea, formato de salida y restricciones, e incorporará las técnicas Few-Shot y Chain of Thought según la actividad: especificación técnica, procedimiento, análisis de requerimientos, reporte de ingeniería y documentación de proyecto. Todos usan el escenario anonimizado de la torre de enfriamiento de la Práctica 2. Refinará al menos dos prompts a partir de los resultados y conservará las versiones finales como plantillas reutilizables para su área.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta y reducir el número de plantillas si hay límites de uso, conservando el objetivo y el resultado esperado.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Diseñar prompts con rol, contexto, tarea, formato de salida y restricciones para actividades de ingeniería.
- Aplicar Few-Shot para fijar estructura y Chain of Thought para tareas que requieren razonamiento técnico.
- Refinar un prompt a partir de los problemas observados en la respuesta.
- Integrar una biblioteca de plantillas reutilizables.

## Prerrequisitos

- Haber completado la [Práctica 2](../../Capitulo01/Practica02/README.md) (escenario anonimizado).
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado los temas del Módulo 4: estructura de un prompt, Chain of Thought y Few-Shot.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Herramienta de IA Generativa | Probar y refinar los prompts | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |
| Microsoft Word (escritorio o web) | Documentar las plantillas | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Plantilla_Prompts_Ingenieria.docx](recursos/Plantilla_Prompts_Ingenieria.docx) | Escenario anonimizado y una tabla por plantilla: técnica, variables, prompt versión 1, problema observado, prompt final y resultado |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Ingenieria\Practica03`.

**Escenario anonimizado:** `[EMPRESA_PRINCIPAL]` opera una torre de enfriamiento modelo CT-4500X (fabricante `[FABRICANTE_EQUIPO]`) en `[UBICACION_PLANTA_A]`, con capacidad nominal de 4,000 a 5,000 GPM, mantenimiento preventivo trimestral e incremento de vibración en el motor del ventilador principal durante los últimos dos ciclos.

## Instrucciones Paso a Paso

### Paso 1: Preparar el documento de plantillas (1 min)

1. Abrir `Plantilla_Prompts_Ingenieria.docx` y guardarlo como `Plantillas_Prompts_Ingenieria_[INICIALES].docx`.
2. Abrir la herramienta de IA en otra pestaña.

**Resultado esperado:** El documento y la herramienta están listos.

**Verificación:** El documento tiene 5 tablas, una por plantilla.

### Paso 2: Plantilla 1, especificación técnica con Few-Shot (3 min)

**Objetivo:** Fijar la estructura de la especificación con un ejemplo.

1. Enviar:

```text
ROL: Eres un ingeniero de mantenimiento industrial especializado en equipos rotativos y sistemas de enfriamiento.

CONTEXTO: En [EMPRESA_PRINCIPAL], la torre de enfriamiento CT-4500X (fabricante [FABRICANTE_EQUIPO]) requiere reemplazar el motor del ventilador principal por incremento sostenido de vibración. Capacidad nominal: 4,000 a 5,000 GPM.

EJEMPLO (Few-Shot):
Entrada: "Especificación para reemplazo de bomba centrífuga de recirculación"
Salida:
1. Descripción: bomba centrífuga horizontal de una etapa.
2. Parámetros de operación: caudal 200 GPM, presión 45 psi, temperatura máxima 80 °C.
3. Material del impulsor: acero inoxidable 316.
4. Norma aplicable: API 610.
5. Criterio de aceptación: prueba hidrostática a 1.5 veces la presión de diseño.

TAREA: Redacta la especificación técnica para adquirir el motor de reemplazo del ventilador principal.

FORMATO DE SALIDA: (1) Descripción, (2) Parámetros eléctricos y mecánicos, (3) Materiales y protección ambiental, (4) Normas aplicables, (5) Criterios de aceptación y pruebas, (6) Condiciones de entrega.

RESTRICCIONES: Sin nombres reales. Unidades del Sistema Internacional con equivalencia imperial. Usa NEMA MG 1 e IEC 60034 como marco normativo. Si falta un dato (potencia, voltaje), escribe [POR DEFINIR] en lugar de suponerlo. Máximo 400 palabras.
```

2. Registrar en la tabla de la Plantilla 1: variables, prompt versión 1 y problema observado (si lo hay).

**Resultado esperado:** Una especificación con 6 secciones.

**Verificación:** Los datos no proporcionados aparecen como `[POR DEFINIR]` y no como valores inventados.

### Paso 3: Plantilla 2, procedimiento con Chain of Thought (3 min)

1. Enviar:

```text
ROL: Eres un supervisor de mantenimiento predictivo con experiencia en análisis de vibraciones de equipos rotativos.

CONTEXTO: El motor del ventilador principal de la torre CT-4500X en [UBICACION_PLANTA_A] registra incremento de vibración en los últimos dos ciclos. [RESPONSABLE_MANTENIMIENTO] necesita un procedimiento de inspección por análisis de vibraciones antes de la parada programada.

TAREA: Antes de redactar, razona paso a paso sobre: (a) los puntos de medición críticos en un motor de ventilador axial, (b) los parámetros a medir y sus zonas de severidad según ISO 20816-3, y (c) la secuencia que minimiza el tiempo de intervención. Después, redacta el procedimiento.

FORMATO DE SALIDA: Sección 1, razonamiento técnico (máximo 150 palabras). Sección 2, procedimiento numerado con responsable, equipo requerido y criterio de aceptación por paso.

RESTRICCIONES: Máximo 12 pasos. Incluye al menos una advertencia de seguridad (bloqueo y etiquetado). Sin datos reales de personas ni empresas.
```

2. Registrar la Plantilla 2.

**Resultado esperado:** Primero el razonamiento y después el procedimiento.

**Verificación:** El procedimiento incluye bloqueo y etiquetado antes de intervenir el motor.

### Paso 4: Plantilla 3, análisis de requerimientos con Few-Shot y Chain of Thought (3 min)

1. Enviar:

```text
ROL: Eres un ingeniero de proyectos especializado en modernización de sistemas de enfriamiento industrial.

CONTEXTO: [EMPRESA_PRINCIPAL] evalúa modernizar el control de la torre CT-4500X. Requerimientos de [DIVISION_CLIENTE_INTERNO]: (R1) monitoreo remoto de temperatura de agua de retorno, (R2) alarma automática por vibración excesiva del ventilador, (R3) integración con el SCADA existente, (R4) registro histórico de al menos 12 meses, (R5) interfaz de operador en español.

EJEMPLO (Few-Shot):
Requerimiento: "El sistema debe operar de −10 °C a 50 °C"
Análisis: Clasificación: no funcional (ambiental). Verificable: sí, con prueba en cámara climática. Riesgo: medio. Dependencia: gabinete IP65 como mínimo.

TAREA: Para cada requerimiento, razona paso a paso: (a) clasificación, (b) si es verificable tal como está redactado, (c) riesgos, (d) dependencias. Al final, entrega una tabla resumen y recomendaciones para mejorar los requerimientos no verificables.

FORMATO DE SALIDA: análisis por requerimiento, tabla | ID | Clasificación | Verificable | Riesgo | Dependencias |, y máximo 5 recomendaciones.

RESTRICCIONES: Analiza solo R1 a R5. Máximo 500 palabras.
```

2. Registrar la Plantilla 3.

**Resultado esperado:** Análisis de los 5 requerimientos y tabla resumen.

**Verificación:** R2 se señala como no verificable tal como está redactado, porque no define el umbral de "vibración excesiva".

### Paso 5: Plantilla 4, reporte de ingeniería con Chain of Thought (3 min)

1. Enviar:

```text
ROL: Eres un ingeniero de confiabilidad que elabora reportes de diagnóstico de equipos críticos.

CONTEXTO: Datos de la inspección trimestral de la torre CT-4500X:
- Vibración del motor del ventilador: 7.2 mm/s RMS (valor previo: 4.1 mm/s RMS).
- Temperatura de rodamientos: 78 °C (límite operativo: 85 °C).
- Corriente del motor: 32 A (nominal: 28 A).
- Aspas del ventilador: desgaste visible en 2 de 6.
- Última intervención mayor: hace 18 meses.

TAREA: Antes de redactar, razona paso a paso sobre: (a) qué indica la vibración según las zonas de ISO 20816-3, (b) la relación entre el aumento de corriente y un posible desbalance, (c) la prioridad de intervención por la cercanía al límite de temperatura. Después, redacta el reporte.

FORMATO DE SALIDA: (1) Resumen ejecutivo, (2) Datos de inspección en tabla, (3) Análisis técnico, (4) Conclusiones, (5) Recomendaciones con prioridad Alta, Media o Baja.

RESTRICCIONES: Usa solo los datos proporcionados. Indica qué datos faltan para un diagnóstico definitivo (por ejemplo, potencia del motor y tipo de soporte). Máximo 450 palabras.
```

2. Registrar la Plantilla 4.

**Resultado esperado:** Un reporte con razonamiento previo y recomendaciones priorizadas.

**Verificación:** El reporte declara que la clasificación exacta en ISO 20816-3 depende de la potencia y del tipo de soporte, que no se proporcionaron.

### Paso 6: Plantilla 5, documentación de proyecto con Few-Shot (3 min)

1. Enviar:

```text
ROL: Eres un coordinador de proyectos de ingeniería que documenta con buenas prácticas del PMI.

CONTEXTO: Se aprobó el proyecto de modernización del control de la torre CT-4500X (código PRY-XXXX-XXXX): sensores de vibración en línea, comunicación con SCADA y actualización del panel de operador. Duración: 16 semanas. Solicitante: [DIVISION_CLIENTE_INTERNO].

EJEMPLO (Few-Shot):
Entrada: "Acta de inicio del reemplazo de tubería de proceso"
Salida: 1. Nombre: Reemplazo de tubería — Sección A. 2. Justificación: reducir fugas y cumplir ASME B31.3. 3. Objetivo: reemplazar 120 m en 8 semanas. 4. Alcance: incluye desmontaje, suministro, instalación y prueba; excluye obra civil. 5. Interesados: gerente de planta, jefe de mantenimiento, contratista. 6. Riesgos: retraso de materiales, interferencia con producción.

TAREA: Genera el acta de inicio del proyecto.

FORMATO DE SALIDA: (1) Nombre y código, (2) Justificación, (3) Objetivo, (4) Alcance (incluye/excluye), (5) Interesados (roles), (6) Hitos, (7) Riesgos, (8) Supuestos y restricciones.

RESTRICCIONES: Solo identificadores anonimizados. Sin presupuestos. Máximo 400 palabras.
```

2. Registrar la Plantilla 5.

**Resultado esperado:** Un acta de inicio con 8 secciones.

**Verificación:** Los hitos suman 16 semanas.

### Paso 7: Refinar dos prompts y consolidar las plantillas (4 min)

**Objetivo:** Mejorar los prompts con resultados menos satisfactorios.

1. Elegir las 2 respuestas con más oportunidades de mejora (formato no respetado, contenido genérico, datos supuestos).
2. Ajustar cada prompt con al menos una estrategia: restricción más específica, más contexto, tarea reformulada o formato más claro.
3. Reenviar el prompt refinado y comparar.
4. En las tablas del documento, llenar **Problema observado**, **Prompt versión final** y **¿Resultado utilizable?**. En el prompt final, reemplazar los datos del caso por variables entre corchetes (por ejemplo, `[EQUIPO]`, `[DATOS_DE_INSPECCION]`).
5. Guardar el documento.

**Resultado esperado:** 5 plantillas con versión final y 2 registros de refinamiento.

**Verificación:** Cada registro de refinamiento indica el problema, el cambio aplicado y la mejora observada.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Reutilización | Usar la Plantilla 4 con otro equipo: una bomba con vibración de 3.0 mm/s y temperatura de 60 °C | El reporte cambia la prioridad según los nuevos datos |
| Few-Shot | Comparar las salidas de las plantillas 1 y 5 con sus ejemplos | Siguen la misma estructura |
| Prueba adversarial | En la Plantilla 1, pedir: *"Incluye el número de parte exacto del fabricante"* | La IA indica que no tiene ese dato o lo marca como [POR DEFINIR], sin inventarlo |

## Solución de Problemas

### Problema 1: La IA omite el razonamiento de Chain of Thought

- **Síntomas:** Entrega directamente el procedimiento o el reporte.
- **Causa:** El modelo resume el razonamiento.
- **Solución:** Agregar al inicio de la tarea: *"Primero escribe la sección 'Razonamiento' y después la sección 'Resultado'"*.

### Problema 2: La IA inventa valores técnicos

- **Síntomas:** Aparecen potencias, voltajes o números de parte no proporcionados.
- **Causa:** El modelo completa la información faltante.
- **Solución:** Reforzar la restricción: *"Si un dato no está en el contexto, escribe [POR DEFINIR]"*.

## Limpieza

1. Conservar `Plantillas_Prompts_Ingenieria_[INICIALES].docx` en `Documentos\Practicas_IA_Ingenieria\Practica03`.
2. Si la política de la empresa lo indica, eliminar las conversaciones.

## Resumen

- Se construyeron 5 plantillas de prompts para actividades de ingeniería.
- Se aplicaron Few-Shot y Chain of Thought según la tarea.
- Se refinaron los prompts a partir de los resultados y se integró una biblioteca reutilizable.

---

[⬅ Anterior: Práctica 2](../../Capitulo01/Practica02/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 4 ➡](../Practica04/README.md)
