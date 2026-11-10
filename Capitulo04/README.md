# Práctica: Diseñar prompts para redactar especificaciones técnicas, elaborar procedimientos, analizar requerimientos, generar reportes de ingeniería y documentar proyectos

## Metadatos

| Campo | Valor |
|---|---|
| **Duración** | 20 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Crear |
| **Módulo** | 4.0 — Ingeniería de Prompts para Actividades de Ingeniería |

## Descripción General

En este laboratorio el participante diseñará cinco prompts estructurados —uno por cada actividad de ingeniería declarada— aplicando la estructura de cinco componentes (rol, contexto, tarea, formato de salida y restricciones) e incorporando las técnicas Few-Shot y Chain of Thought. Cada prompt se ejecutará en la herramienta de IA Generativa, se evaluará la respuesta, se refinará al menos una vez y se documentará la versión final en un documento de plantillas reutilizables. Todo el ejercicio utiliza exclusivamente información técnica ficticia o anonimizada, continuando las prácticas del Módulo 3.0.

## Objetivos de Aprendizaje

- [ ] Construir prompts aplicando la estructura completa de cinco componentes: rol, contexto, tarea, formato de salida y restricciones.
- [ ] Incorporar las técnicas Few-Shot y Chain of Thought en prompts según el tipo de tarea de ingeniería.
- [ ] Refinar prompts a partir de los resultados obtenidos y conservar las versiones más consistentes como plantillas reutilizables.
- [ ] Diseñar prompts para cinco actividades de ingeniería: especificación técnica, procedimiento operativo, análisis de requerimientos, reporte de ingeniería y documentación de proyecto.

## Prerrequisitos

**Conocimientos previos:**

- Haber completado los labs 03-00-01 y 03-00-02 del Módulo 3.0 (anonimización de información técnica).
- Haber revisado los contenidos teóricos del Módulo 4.0 sobre estructura básica de un prompt, técnicas Few-Shot y Chain of Thought.
- Familiaridad básica con documentación de ingeniería (especificaciones, procedimientos, reportes).

**Acceso y cuentas:**

- Cuenta activa en la herramienta de IA Generativa seleccionada por el instructor:
  - **ChatGPT (OpenAI)** — modelo GPT-4o, versión gratuita: [https://chat.openai.com](https://chat.openai.com)
  - **Claude (Anthropic)** — modelo Claude 3.5 Sonnet, versión gratuita: [https://claude.ai](https://claude.ai)
  - **Google Gemini** — modelo Gemini 1.5 Flash, versión gratuita: [https://gemini.google.com](https://gemini.google.com)
- Procesador de texto para el entregable: Google Docs (web), Microsoft Word (Microsoft 365, versión 2405 o superior) o LibreOffice Writer 24.2.3.

**Materiales:**

- Caso de ingeniería ficticio proporcionado en este laboratorio (sistema de enfriamiento industrial, continuación del contexto anonimizado del lab 03-00-02).

## Entorno de Laboratorio

| Componente | Detalle |
|---|---|
| **Navegador** | Google Chrome 124.0+, Firefox 125.0+ o Microsoft Edge 124.0+ |
| **Conexión** | Mínimo 10 Mbps |
| **Resolución** | Mínimo 1366 × 768 (recomendado 1920 × 1080 para dos pestañas simultáneas) |
| **Herramienta de IA** | ChatGPT GPT-4o / Claude 3.5 Sonnet / Gemini 1.5 Flash (según indicación del instructor) |
| **Procesador de texto** | Google Docs (web) / Microsoft Word 2405+ / LibreOffice Writer 24.2.3 |

**Preparación inicial:** Abrir dos pestañas en el navegador — una con la herramienta de IA Generativa y otra con el procesador de texto. En el procesador de texto, crear un documento nuevo con el título indicado a continuación.

```text
Nombre del documento: Plantillas_Prompts_Ingenieria_[TuNombre].docx
```

Dentro del documento, crear la siguiente estructura inicial:

```text
PLANTILLAS DE PROMPTS PARA ACTIVIDADES DE INGENIERÍA
Autor: [Tu nombre]
Fecha: [Fecha actual]
Herramienta de IA utilizada: [ChatGPT / Claude / Gemini]

---
1. Especificación Técnica
2. Procedimiento Operativo
3. Análisis de Requerimientos
4. Reporte de Ingeniería
5. Documentación de Proyecto
---
```

### Contexto técnico ficticio del laboratorio

Todos los prompts se basarán en el siguiente escenario anonimizado (continuación del lab 03-00-02):

> **Escenario:** [EMPRESA_PRINCIPAL] opera una torre de enfriamiento modelo CT-4500X (fabricante: [FABRICANTE_EQUIPO]) en [UBICACION_PLANTA_A] — [NAVE_1], [LINEA_PRODUCCION_01]. El equipo tiene capacidad nominal en el rango 4,000–5,000 GPM, requiere mantenimiento preventivo trimestral y ha presentado incremento de vibración en el motor del ventilador principal durante los últimos dos ciclos de operación. [RESPONSABLE_MANTENIMIENTO] coordina las actividades de mantenimiento y [SUPERVISOR_TURNO] supervisa la operación diaria.

## Instrucciones Paso a Paso

### Paso 1: Construir el prompt para redactar una especificación técnica (con Few-Shot)

**Objetivo:** Diseñar un prompt con los cinco componentes y la técnica Few-Shot para generar una especificación técnica de repuesto.

**Instrucciones:**

1. En la herramienta de IA Generativa, ingresar el siguiente prompt. Este prompt incorpora **Few-Shot** al incluir un ejemplo de entrada-salida antes de la tarea principal:

```text
ROL: Eres un ingeniero de mantenimiento industrial especializado en equipos rotativos y sistemas de enfriamiento.

CONTEXTO: En [EMPRESA_PRINCIPAL], la torre de enfriamiento modelo CT-4500X (fabricante: [FABRICANTE_EQUIPO]) ubicada en [UBICACION_PLANTA_A] — [NAVE_1], [LINEA_PRODUCCION_01] requiere el reemplazo del motor del ventilador principal debido a incremento sostenido de vibración en los últimos dos ciclos de operación. El equipo opera con capacidad nominal en el rango 4,000–5,000 GPM.

EJEMPLO (Few-Shot):
- Entrada: "Especificación para reemplazo de bomba centrífuga de recirculación"
- Salida esperada:
  1. Descripción del componente: Bomba centrífuga horizontal, etapa simple.
  2. Parámetros de operación: Caudal 200 GPM, presión 45 PSI, temperatura máxima 80 °C.
  3. Material del impulsor: Acero inoxidable 316.
  4. Norma aplicable: API 610.
  5. Criterio de aceptación: Prueba hidrostática a 1.5x presión de diseño.

TAREA: Redacta una especificación técnica para la adquisición del motor de reemplazo del ventilador principal de la torre de enfriamiento CT-4500X.

FORMATO DE SALIDA: Documento estructurado con las siguientes secciones: (1) Descripción del componente, (2) Parámetros eléctricos y mecánicos requeridos, (3) Materiales y protección ambiental, (4) Normas y estándares aplicables, (5) Criterios de aceptación y pruebas, (6) Condiciones de entrega.

RESTRICCIONES:
- No incluir nombres reales de personas, empresas o ubicaciones.
- Utilizar unidades del Sistema Internacional con equivalencias en unidades imperiales donde aplique.
- Referir normas NEMA MG-1 e IEC 60034 como marco normativo.
- Máximo 400 palabras.
```

2. Enviar el prompt y esperar la respuesta completa.
3. Leer la respuesta generada y verificar que contenga las seis secciones solicitadas.

**Resultado esperado:** Una especificación técnica estructurada en seis secciones con parámetros eléctricos y mecánicos del motor, referencias normativas NEMA MG-1 e IEC 60034, y criterios de aceptación definidos.

**Verificación:** Confirmar que la respuesta incluye las seis secciones del formato solicitado y que no contiene nombres reales ni información confidencial.

### Paso 2: Construir el prompt para elaborar un procedimiento operativo (con Chain of Thought)

**Objetivo:** Diseñar un prompt con los cinco componentes y la técnica Chain of Thought para generar un procedimiento de inspección.

**Instrucciones:**

1. En la misma conversación o una nueva (según preferencia), ingresar el siguiente prompt. Este prompt incorpora **Chain of Thought** al instruir al modelo a razonar paso a paso antes de generar el procedimiento:

```text
ROL: Eres un supervisor de mantenimiento predictivo con 15 años de experiencia en análisis de vibraciones de equipos rotativos industriales.

CONTEXTO: La torre de enfriamiento CT-4500X en [UBICACION_PLANTA_A] ha registrado incremento de vibración en el motor del ventilador principal durante los últimos dos ciclos de operación. [RESPONSABLE_MANTENIMIENTO] necesita un procedimiento de inspección por análisis de vibraciones para ejecutar antes de la parada programada.

TAREA: Elabora un procedimiento operativo de inspección por análisis de vibraciones del motor del ventilador principal. Antes de redactar el procedimiento, razona paso a paso sobre: (a) qué puntos de medición son críticos en un motor de ventilador axial de torre de enfriamiento, (b) qué parámetros de vibración deben medirse y sus valores de alerta según ISO 10816-3, y (c) qué secuencia lógica de pasos minimiza el tiempo de intervención sin comprometer la calidad del diagnóstico. Después de ese razonamiento, genera el procedimiento final.

FORMATO DE SALIDA:
- Sección 1: Razonamiento técnico (máximo 150 palabras).
- Sección 2: Procedimiento con pasos numerados, responsable de cada paso, equipo requerido y criterio de aceptación/rechazo por paso.

RESTRICCIONES:
- Referir la norma ISO 10816-3 para los umbrales de vibración.
- No incluir datos reales de personas ni empresas.
- El procedimiento no debe exceder 12 pasos.
- Incluir al menos una advertencia de seguridad.
```

2. Enviar el prompt y esperar la respuesta completa.
3. Verificar que la respuesta contenga primero el razonamiento explícito (Chain of Thought) y luego el procedimiento estructurado.

**Resultado esperado:** Una respuesta en dos secciones: primero el razonamiento técnico sobre puntos de medición, parámetros y secuencia; después el procedimiento con pasos numerados, responsables, equipo y criterios.

**Verificación:** Confirmar que el razonamiento aparece antes del procedimiento y que los umbrales de vibración referencian ISO 10816-3.

### Paso 3: Construir el prompt para análisis de requerimientos (con Few-Shot y Chain of Thought)

**Objetivo:** Diseñar un prompt que combine ambas técnicas para analizar requerimientos de un proyecto de modernización.

**Instrucciones:**

1. Ingresar el siguiente prompt, que combina **Few-Shot** (ejemplo de análisis) y **Chain of Thought** (instrucción de razonamiento secuencial):

```text
ROL: Eres un ingeniero de proyectos especializado en modernización de sistemas de enfriamiento industrial.

CONTEXTO: [EMPRESA_PRINCIPAL] está evaluando la modernización del sistema de control de la torre de enfriamiento CT-4500X. Los requerimientos preliminares del cliente interno ([DIVISION_CLIENTE_INTERNO]) son: (R1) monitoreo remoto de temperatura de agua de retorno, (R2) alarma automática por vibración excesiva del ventilador, (R3) integración con el sistema SCADA existente, (R4) registro histórico de datos de al menos 12 meses, (R5) interfaz de operador en español.

EJEMPLO (Few-Shot):
- Requerimiento analizado: "Sistema debe operar en temperaturas de -10 °C a 50 °C"
- Análisis: Clasificación: funcional/ambiental. Verificable: sí, mediante prueba en cámara climática. Riesgo: medio — requiere validar compatibilidad de componentes electrónicos con rango extremo. Dependencia: selección de gabinete con grado de protección IP65 mínimo.

TAREA: Analiza cada uno de los cinco requerimientos (R1 a R5). Para cada uno, razona paso a paso sobre: (a) clasificación del requerimiento (funcional, no funcional, de interfaz, de desempeño), (b) si es verificable tal como está redactado, (c) riesgos asociados, y (d) dependencias con otros requerimientos. Al final, genera una tabla resumen y una lista de recomendaciones para completar o mejorar los requerimientos que lo necesiten.

FORMATO DE SALIDA:
- Análisis individual por requerimiento (razonamiento paso a paso).
- Tabla resumen con columnas: ID | Clasificación | Verificable (Sí/No) | Riesgo | Dependencias.
- Lista de recomendaciones (máximo 5).

RESTRICCIONES:
- No inventar requerimientos adicionales; analizar solo R1 a R5.
- No incluir datos reales de personas ni empresas.
- Máximo 500 palabras en total.
```

2. Enviar el prompt y revisar la respuesta.

**Resultado esperado:** Análisis individual de cada requerimiento con razonamiento visible, tabla resumen de cinco filas y lista de recomendaciones.

**Verificación:** Confirmar que los cinco requerimientos están analizados, que la tabla tiene las cinco columnas solicitadas y que las recomendaciones no exceden cinco.

### Paso 4: Construir el prompt para generar un reporte de ingeniería (con Chain of Thought)

**Objetivo:** Diseñar un prompt para generar un reporte técnico de diagnóstico aplicando Chain of Thought.

**Instrucciones:**

1. Ingresar el siguiente prompt:

```text
ROL: Eres un ingeniero de confiabilidad responsable de elaborar reportes de diagnóstico de equipos críticos.

CONTEXTO: Durante la inspección trimestral de la torre de enfriamiento CT-4500X en [UBICACION_PLANTA_A], se obtuvieron los siguientes datos ficticios:
- Vibración del motor del ventilador: 7.2 mm/s RMS (valor previo: 4.1 mm/s RMS).
- Temperatura de rodamientos: 78 °C (límite operativo: 85 °C).
- Corriente del motor: 32 A (nominal: 28 A).
- Estado de aspas del ventilador: desgaste visible en 2 de 6 aspas.
- Última intervención mayor: hace 18 meses.

TAREA: Genera un reporte de diagnóstico de ingeniería. Antes de redactar el reporte, razona paso a paso sobre: (a) qué indican los valores de vibración comparados con ISO 10816-3, (b) la relación entre el incremento de corriente y el posible desbalance del ventilador, y (c) la prioridad de intervención considerando la proximidad al límite de temperatura de rodamientos. Después, redacta el reporte.

FORMATO DE SALIDA: Reporte con secciones: (1) Resumen ejecutivo, (2) Datos de inspección (tabla), (3) Análisis técnico, (4) Conclusiones, (5) Recomendaciones con prioridad (alta/media/baja).

RESTRICCIONES:
- Basar el análisis exclusivamente en los datos proporcionados.
- No asumir datos no proporcionados.
- Referir ISO 10816-3 para clasificación de severidad de vibración.
- Máximo 450 palabras.
```

2. Enviar el prompt y revisar la respuesta.

**Resultado esperado:** Reporte con razonamiento previo, cinco secciones, tabla de datos de inspección y recomendaciones priorizadas.

**Verificación:** Confirmar que el análisis referencia ISO 10816-3, que la tabla incluye los cinco datos proporcionados y que las recomendaciones tienen prioridad asignada.

### Paso 5: Construir el prompt para documentación de proyecto (con Few-Shot)

**Objetivo:** Diseñar un prompt con Few-Shot para generar un acta de inicio de proyecto de modernización.

**Instrucciones:**

1. Ingresar el siguiente prompt:

```text
ROL: Eres un coordinador de proyectos de ingeniería con experiencia en documentación bajo metodología PMI.

CONTEXTO: [EMPRESA_PRINCIPAL] ha aprobado el proyecto de modernización del sistema de control de la torre de enfriamiento CT-4500X (código de proyecto: PRY-XXXX-XXXX). El proyecto incluye instalación de sensores de vibración en línea, módulo de comunicación SCADA y actualización del panel de operador. Duración estimada: 16 semanas. Área solicitante: [DIVISION_CLIENTE_INTERNO].

EJEMPLO (Few-Shot):
- Entrada: "Acta de inicio para proyecto de reemplazo de tubería de proceso"
- Salida esperada (estructura):
  1. Nombre del proyecto: Reemplazo de tubería de proceso — Sección A.
  2. Justificación: Reducción de fugas recurrentes y cumplimiento de ASME B31.3.
  3. Objetivo: Reemplazar 120 m de tubería de acero al carbono en 8 semanas.
  4. Alcance: Incluye desmontaje, suministro, instalación y prueba hidrostática. Excluye: obra civil.
  5. Interesados clave: Gerente de planta, Jefe de mantenimiento, Contratista.
  6. Riesgos preliminares: Retraso en suministro de materiales, interferencia con producción.

TAREA: Genera un acta de inicio (Project Charter simplificado) para el proyecto de modernización del sistema de control de la torre CT-4500X.

FORMATO DE SALIDA: Documento con secciones: (1) Nombre y código del proyecto, (2) Justificación, (3) Objetivo, (4) Alcance (incluye/excluye), (5) Interesados clave (roles genéricos), (6) Hitos principales, (7) Riesgos preliminares, (8) Supuestos y restricciones.

RESTRICCIONES:
- Usar únicamente identificadores anonimizados.
- No incluir presupuestos específicos.
- Máximo 400 palabras.
```

2. Enviar el prompt y revisar la respuesta.

**Resultado esperado:** Acta de inicio con ocho secciones, roles genéricos (sin nombres reales), hitos del proyecto y riesgos preliminares identificados.

**Verificación:** Confirmar que el documento tiene las ocho secciones, que no incluye nombres reales ni presupuestos específicos, y que los hitos son coherentes con la duración de 16 semanas.

### Paso 6: Refinar al menos dos prompts a partir de la evaluación de resultados

**Objetivo:** Iterar sobre los prompts que produjeron resultados menos satisfactorios, documentar los cambios y evaluar la mejora.

**Instrucciones:**

1. Revisar las cinco respuestas obtenidas en los pasos 1 a 5. Identificar los **dos prompts** cuyas respuestas presentaron mayor oportunidad de mejora (respuesta incompleta, formato no respetado, contenido genérico o falta de precisión técnica).

2. Para cada uno de los dos prompts seleccionados, aplicar al menos una de las siguientes estrategias de refinamiento:
   - **Agregar restricciones más específicas** (por ejemplo, "No uses viñetas genéricas; cada punto debe incluir un valor numérico o referencia normativa").
   - **Mejorar el contexto** (agregar un dato técnico relevante que estaba ausente).
   - **Reformular la tarea** para reducir ambigüedad.
   - **Ajustar el formato de salida** si la estructura no fue respetada.

3. Reenviar cada prompt refinado a la herramienta de IA y comparar la nueva respuesta con la anterior.

4. En el documento de plantillas, registrar para cada prompt refinado:

```text
PROMPT [N] — REGISTRO DE REFINAMIENTO
Versión original: [Copiar el prompt original]
Problema detectado: [Describir qué aspecto de la respuesta no fue satisfactorio]
Cambio aplicado: [Describir la modificación específica al prompt]
Versión refinada: [Copiar el prompt modificado]
Mejora observada: [Describir cómo mejoró la respuesta]
```

**Resultado esperado:** Dos registros de refinamiento documentados con evidencia clara de la mejora entre la versión original y la refinada.

**Verificación:** Confirmar que cada registro incluye los cinco campos (versión original, problema, cambio, versión refinada, mejora observada) y que la mejora es identificable.

### Paso 7: Consolidar las plantillas reutilizables en el documento final

**Objetivo:** Organizar los cinco prompts (en su versión final refinada) en el documento de plantillas como entregable del laboratorio.

**Instrucciones:**

1. En el documento de plantillas, para cada una de las cinco secciones (Especificación Técnica, Procedimiento Operativo, Análisis de Requerimientos, Reporte de Ingeniería, Documentación de Proyecto), registrar la siguiente información:

```text
PLANTILLA [N]: [Nombre de la actividad de ingeniería]
Técnica aplicada: [Few-Shot / Chain of Thought / Ambas]
Prompt final (versión refinada si aplica):
[Copiar el texto completo del prompt en su versión final]

Componentes del prompt:
- ROL: [Resumen en una línea]
- CONTEXTO: [Resumen en una línea]
- TAREA: [Resumen en una línea]
- FORMATO DE SALIDA: [Resumen en una línea]
- RESTRICCIONES: [Resumen en una línea]

Notas de uso: [Indicar qué partes del prompt deben personalizarse para reutilización en otros casos]
```

2. Verificar que el documento contenga las cinco plantillas completas y los dos registros de refinamiento del Paso 6.

3. Guardar el documento final.

**Resultado esperado:** Documento consolidado con cinco plantillas de prompts organizadas por tipo de actividad, cada una con los cinco componentes identificados, técnica aplicada y notas de reutilización.

**Verificación:** El documento contiene: (a) cinco plantillas completas, (b) al menos dos con técnica Few-Shot, (c) al menos dos con Chain of Thought, (d) dos registros de refinamiento, y (e) notas de personalización para reutilización.

## Validación y Pruebas

Para considerar el laboratorio completado exitosamente, verificar los siguientes criterios:

**Criterio 1 — Estructura de cinco componentes:**
Cada uno de los cinco prompts debe contener explícitamente los cinco componentes (rol, contexto, tarea, formato de salida, restricciones). Revisar el documento de plantillas y confirmar que ningún componente está ausente en ninguna plantilla.

**Criterio 2 — Aplicación de técnicas:**
Verificar en el documento que:
- Al menos dos prompts utilizan la técnica **Few-Shot** (incluyen ejemplo de entrada-salida antes de la tarea).
- Al menos dos prompts utilizan **Chain of Thought** (instruyen al modelo a razonar paso a paso antes de generar el resultado final).

**Criterio 3 — Refinamiento documentado:**
Los dos registros de refinamiento deben incluir los cinco campos (versión original, problema detectado, cambio aplicado, versión refinada, mejora observada). La mejora debe ser concreta y verificable (no genérica como "mejoró la respuesta").

**Criterio 4 — Protección de información:**
Ninguno de los cinco prompts ni sus respuestas debe contener nombres reales de personas, empresas, ubicaciones, números de serie o datos confidenciales. Todos los identificadores deben ser ficticios o usar los tokens anonimizados del lab 03-00-02 (por ejemplo, `[EMPRESA_PRINCIPAL]`, `[RESPONSABLE_MANTENIMIENTO]`).

**Criterio 5 — Caso adverso (limitaciones de la IA):**
Seleccionar uno de los cinco prompts y modificarlo para incluir un dato contradictorio. Por ejemplo, en el prompt del reporte de ingeniería (Paso 4), cambiar la temperatura de rodamientos a **92 °C** (por encima del límite operativo de 85 °C declarado) y simultáneamente agregar la frase "El equipo opera en condiciones normales sin anomalías". Enviar este prompt modificado y evaluar:

```text
[Modificación al prompt del Paso 4 — Caso adverso]
Cambiar en los datos de inspección:
- Temperatura de rodamientos: 92 °C (límite operativo: 85 °C).
Agregar al final del contexto:
- "El equipo opera en condiciones normales sin anomalías."
```

- ¿El modelo detecta la contradicción entre el dato de temperatura y la afirmación de operación normal?
- ¿El modelo prioriza los datos numéricos o la afirmación textual?
- Registrar el hallazgo en el documento de plantillas como nota de limitación:

```text
NOTA DE LIMITACIÓN DE IA:
Caso probado: [Describir la contradicción introducida]
Comportamiento observado: [¿Detectó la contradicción? ¿Cómo la manejó?]
Lección aprendida: [Importancia de la supervisión humana en resultados de IA]
```

> **Importante:** Este caso adverso demuestra que los modelos de IA pueden no detectar inconsistencias en los datos de entrada. El profesional de ingeniería debe siempre validar los resultados generados antes de utilizarlos en decisiones técnicas.

## Solución de Problemas

**Problema 1: La herramienta de IA no respeta el formato de salida solicitado**

| Elemento | Detalle |
|---|---|
| **Síntoma** | La respuesta se genera como texto corrido en lugar de respetar las secciones, tablas o estructura solicitada en el componente "formato de salida" del prompt. |
| **Causa probable** | El modelo interpreta el formato como sugerencia y no como requisito. Esto es más frecuente cuando el prompt tiene múltiples instrucciones largas y el formato queda diluido al final. |
| **Solución** | Mover la instrucción de formato al inicio del prompt, inmediatamente después del rol, y reforzarla con una restricción explícita. Ejemplo: agregar en RESTRICCIONES la línea `"Es obligatorio respetar la estructura de secciones indicada en FORMATO DE SALIDA. No fusionar secciones ni omitir ninguna."` Si persiste, dividir la solicitud en dos prompts: primero generar el contenido y después solicitar el reformateo. |

**Problema 2: Se alcanzan los límites de uso gratuito de la herramienta de IA durante el laboratorio**

| Elemento | Detalle |
|---|---|
| **Síntoma** | La herramienta muestra un mensaje de límite alcanzado (por ejemplo, "Has alcanzado el límite de mensajes" en ChatGPT, o "Usage limit reached" en Claude) antes de completar los cinco prompts. |
| **Causa probable** | Las cuentas gratuitas de ChatGPT GPT-4o, Claude 3.5 Sonnet y Gemini 1.5 Flash tienen límites de mensajes por periodo que varían según la demanda del servicio. Prompts extensos consumen más capacidad. |
| **Solución** | (a) Cambiar temporalmente a otra herramienta de IA gratuita disponible (si el instructor lo autoriza). (b) Esperar el periodo de reinicio del límite (generalmente entre 1 y 3 horas según la plataforma). (c) Para completar el laboratorio dentro del tiempo: redactar los prompts restantes en el documento de plantillas sin ejecutarlos y marcarlos como "pendiente de ejecución", ejecutándolos al restablecerse el acceso. El entregable sigue siendo válido si los prompts están correctamente construidos. |

## Limpieza

Este laboratorio no genera recursos en la nube, contenedores ni bases de datos que requieran eliminación. Las acciones de limpieza son:

1. **Conversaciones en la herramienta de IA:** Si se desea mantener la privacidad, eliminar las conversaciones creadas durante el laboratorio desde el panel lateral de la herramienta (ChatGPT: ícono de eliminar en la conversación; Claude: menú de la conversación → Delete; Gemini: menú de tres puntos → Borrar).

2. **Documento de plantillas:** Guardar la versión final del documento `Plantillas_Prompts_Ingenieria_[TuNombre]` en una ubicación accesible. Este documento se utilizará directamente en el **lab 04-00-02**.

## Resumen

En este laboratorio se construyeron cinco prompts estructurados para actividades de ingeniería, aplicando sistemáticamente los cinco componentes (rol, contexto, tarea, formato de salida y restricciones) y las técnicas Few-Shot y Chain of Thought. Los puntos clave son:

- **La estructura de cinco componentes** transforma un prompt genérico en una instrucción precisa que produce respuestas técnicamente útiles y alineadas con la necesidad real.
- **Few-Shot** es especialmente efectiva cuando se necesita que el modelo siga un formato o nivel de detalle específico (como en especificaciones técnicas y documentación de proyectos).
- **Chain of Thought** es especialmente efectiva cuando la tarea requiere análisis o diagnóstico, ya que fuerza al modelo a explicitar su razonamiento antes de generar conclusiones (como en procedimientos y reportes).
- **El refinamiento iterativo** es una práctica esencial: el primer prompt rara vez produce el resultado óptimo, y documentar los cambios permite construir plantillas cada vez más consistentes.
- **La supervisión humana es indispensable:** como se demostró en el caso adverso, los modelos de IA pueden no detectar contradicciones en los datos de entrada.

**Entregable:** El documento `Plantillas_Prompts_Ingenieria_[TuNombre]` con cinco plantillas, dos registros de refinamiento y una nota de limitación de IA. Este documento se utilizará en el lab 04-00-02 para comparar la calidad de respuestas entre prompts estructurados y prompts genéricos.

**Nota sobre el tiempo:** Los cinco prompts y sus refinamientos están diseñados para completarse en 20 minutos. Si algún participante no alcanza a ejecutar los cinco prompts por límites de la herramienta gratuita, se recomienda priorizar la construcción correcta de los prompts en el documento (el diseño es el objetivo principal) y ejecutar los pendientes fuera del horario del laboratorio.

### Recursos adicionales

- OpenAI — Guía de ingeniería de prompts: [https://platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)
- Anthropic — Documentación de diseño de prompts para Claude: [https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- Google — Guía de prompts para Gemini: [https://ai.google.dev/gemini-api/docs/prompting-intro](https://ai.google.dev/gemini-api/docs/prompting-intro)
- ISO 10816-3 — Evaluación de vibraciones mecánicas en máquinas industriales (referencia normativa utilizada en los prompts del laboratorio).

---

# Práctica: Comparar los resultados obtenidos mediante prompts genéricos frente a prompts correctamente estructurados para evaluar su impacto en la calidad de la información técnica.

## Metadatos

| Campo | Valor |
|---|---|
| **Duración** | 16 minutos |
| **Complejidad** | Fácil |
| **Nivel Bloom** | Aplicar |

## Descripción General

El participante resolverá un mismo caso de ingeniería con un prompt genérico y con un prompt estructurado que incluya rol, contexto, datos técnicos, formato de salida y criterios de calidad. Comparará ambas respuestas en una matriz de evaluación con criterios como precisión técnica, completitud, claridad, uso correcto de unidades y terminología, y facilidad de uso en un documento de ingeniería, y concluirá qué elementos del prompt generan la mayor mejora. La práctica está planteada para realizarse con versiones gratuitas; el instructor podrá seleccionar la herramienta de IA Generativa más adecuada según su disponibilidad y límites de consumo, así como ajustar la profundidad, la complejidad y la extensión del ejercicio, conservando el objetivo y el resultado esperado. Se recomienda utilizar información técnica ficticia o previamente anonimizada.

## Objetivos de Aprendizaje

- [ ] Resolver un mismo caso de ingeniería utilizando primero un prompt genérico y después un prompt estructurado con rol, contexto, datos técnicos, formato de salida y criterios de calidad.
- [ ] Evaluar ambas respuestas en una matriz de evaluación con criterios de precisión técnica, completitud, claridad, uso correcto de unidades y terminología, y facilidad de uso en documentación de ingeniería.
- [ ] Identificar y concluir qué elementos del prompt generan la mayor mejora en la calidad de la respuesta técnica.
- [ ] Comparar los resultados obtenidos mediante prompts genéricos frente a prompts correctamente estructurados para evaluar su impacto en la calidad de la información técnica.

## Prerrequisitos

### Conocimientos previos

| Requisito | Detalle |
|---|---|
| Lab 04-00-01 completado | Contar con el documento de plantillas de prompts estructurados generado en ese laboratorio, incluyendo el contexto técnico ficticio de la torre de enfriamiento CT-4500X |
| Módulo 4.0 — Teoría | Haber revisado los contenidos sobre estructura básica de un prompt (tarea, contexto, restricciones), técnicas Few-Shot y Chain of Thought |
| Conceptos de ingeniería básicos | Familiaridad con términos como caudal, presión, temperatura, eficiencia térmica y unidades del Sistema Internacional |

### Acceso a herramientas

| Herramienta | Versión / Tier | Verificación |
|---|---|---|
| Herramienta de IA Generativa (una de las siguientes, según indicación del instructor) | ChatGPT — GPT-4o (tier gratuito) / Claude — Claude 3.5 Sonnet (tier gratuito) / Google Gemini — Gemini 1.5 Flash (tier gratuito) | Sesión activa con capacidad de enviar al menos 4 mensajes durante el laboratorio |
| Hoja de cálculo | Microsoft Excel (Microsoft 365, versión 2405+) / Google Sheets (web) / LibreOffice Calc 24.2.3 | Archivo nuevo o existente abierto y editable |
| Procesador de texto (opcional) | Microsoft Word (Microsoft 365, versión 2405+) / Google Docs (web) / LibreOffice Writer 24.2.3 | Para redactar conclusiones si se prefiere sobre la hoja de cálculo |

> **Nota sobre la herramienta de IA:** El instructor comunicará con anticipación cuál herramienta utilizar. Los prompts de este laboratorio funcionan en cualquiera de las tres opciones. Las respuestas variarán entre modelos; esto es esperado y no afecta el ejercicio de comparación.

## Entorno de Laboratorio

Este laboratorio no requiere instalación de software adicional ni configuración de servidores. El entorno consiste en:

1. **Navegador web** con sesión activa en la herramienta de IA Generativa seleccionada.
2. **Hoja de cálculo** (nueva pestaña o archivo) para construir la matriz de evaluación.
3. **Documento de plantillas del lab 04-00-01** abierto como referencia (el documento que contiene el contexto técnico ficticio de la torre de enfriamiento CT-4500X en [UBICACION_PLANTA_A]).

### Caso de ingeniería para la comparación

Todos los pasos de este laboratorio utilizan el siguiente caso ficticio, derivado del escenario establecido en el lab 04-00-01:

> **Caso:** Calcular el caudal de agua de reposición (*make-up water*) necesario para la torre de enfriamiento CT-4500X, considerando pérdidas por evaporación, arrastre (*drift*) y purga (*blowdown*). La torre opera con un caudal de recirculación de 4,500 GPM, una diferencia de temperatura (rango) de 10 °F, condiciones ambientales de 95 °F de bulbo seco y 78 °F de bulbo húmedo, y se requiere mantener 5 ciclos de concentración. El resultado debe expresarse en GPM y en m³/h.

> **Importante:** Si el instructor proporcionó un caso de ingeniería diferente, utilice ese caso en lugar del anterior, adaptando los prompts de los Pasos 1 y 2 de forma correspondiente.

## Instrucciones Paso a Paso

### Paso 1: Enviar el prompt genérico a la herramienta de IA

**Objetivo:** Obtener una respuesta del modelo utilizando un prompt sin estructura, sin rol, sin contexto técnico específico y sin formato de salida definido, para establecer la línea base de comparación.

**Instrucciones:**

1. Abrir la herramienta de IA Generativa seleccionada por el instructor e iniciar una **conversación nueva** (no reutilizar la conversación del lab 04-00-01).
2. Copiar y pegar el siguiente prompt genérico exactamente como aparece:

```text
Explícame cómo calcular el caudal de agua de reposición en una torre de enfriamiento.
```

3. Enviar el mensaje y esperar a que el modelo genere la respuesta completa.
4. **No cerrar** esta conversación. Leer la respuesta completa y tomar nota mental de los siguientes aspectos:
   - ¿La respuesta incluye valores numéricos específicos o solo fórmulas generales?
   - ¿Menciona unidades concretas (GPM, m³/h)?
   - ¿Referencia normas o estándares de ingeniería?
   - ¿El formato es directamente utilizable en un documento técnico?

**Resultado esperado:** Una respuesta de carácter general que explique el concepto de agua de reposición y posiblemente incluya fórmulas genéricas (evaporación ≈ 0.001 × ΔT × caudal de recirculación, etc.), pero sin cálculos aplicados al caso específico de la CT-4500X, sin formato estructurado para documentación y probablemente sin referencias normativas.

**Verificación:** Confirmar que la respuesta se generó correctamente y que la conversación permanece abierta para referencia posterior. No se requiere que la respuesta sea de alta calidad — precisamente se espera que sea genérica.

---

### Paso 2: Enviar el prompt estructurado para el mismo caso

**Objetivo:** Obtener una respuesta del modelo utilizando un prompt con los cinco componentes (rol, contexto, datos técnicos, formato de salida y criterios de calidad) para el mismo caso de ingeniería, aplicando la estructura aprendida en el lab 04-00-01.

**Instrucciones:**

1. Iniciar una **conversación nueva** en la herramienta de IA (separada de la del Paso 1, para evitar que el contexto previo influya en la respuesta).
2. Copiar y pegar el siguiente prompt estructurado:

```text
## Rol
Eres un ingeniero de procesos con 15 años de experiencia en sistemas de enfriamiento industrial y tratamiento de agua. Manejas normativas CTI (Cooling Technology Institute) y ASHRAE.

## Contexto
[EMPRESA_PRINCIPAL] opera una torre de enfriamiento modelo CT-4500X en [UBICACION_PLANTA_A] — [NAVE_1], [LINEA_PRODUCCION_01]. Se requiere calcular el caudal de agua de reposición (make-up water) para planificar el suministro y dimensionar el sistema de tratamiento químico. [RESPONSABLE_MANTENIMIENTO] necesita este cálculo para el reporte trimestral de operación.

## Datos técnicos
- Caudal de recirculación: 4,500 GPM
- Rango de enfriamiento (ΔT): 10 °F
- Temperatura de bulbo seco: 95 °F
- Temperatura de bulbo húmedo: 78 °F
- Ciclos de concentración objetivo: 5
- Capacidad nominal del equipo: 4,000–5,000 GPM

## Tarea
Calcula el caudal de agua de reposición total, desglosando los tres componentes: pérdidas por evaporación, pérdidas por arrastre (drift) y caudal de purga (blowdown). Muestra las fórmulas utilizadas, los valores intermedios y el resultado final.

## Formato de salida
Presenta el resultado en una tabla resumen con las siguientes columnas: Componente | Fórmula utilizada | Valor calculado (GPM) | Valor calculado (m³/h). Después de la tabla, incluye una sección de supuestos y una sección de referencias normativas aplicables.

## Criterios de calidad
- Expresar todos los resultados numéricos con dos decimales.
- Incluir conversión de unidades GPM a m³/h (1 GPM = 0.2271 m³/h).
- Referenciar CTI ATC-105 o ASHRAE Handbook — HVAC Systems and Equipment para las fórmulas de evaporación.
- Indicar claramente los supuestos asumidos (porcentaje de drift, factor de evaporación).
- No utilizar nombres reales de personas ni ubicaciones reales.
```

3. Enviar el mensaje y esperar a que el modelo genere la respuesta completa.
4. Leer la respuesta y verificar que contenga:
   - Tabla con las cuatro columnas solicitadas.
   - Desglose de los tres componentes (evaporación, arrastre, purga).
   - Sección de supuestos.
   - Sección de referencias normativas.
   - Valores con dos decimales y conversión de unidades.

**Resultado esperado:** Una respuesta estructurada que incluya una tabla con los tres componentes calculados (evaporación ≈ 45 GPM, drift ≈ 0.45–0.90 GPM, blowdown ≈ 11.25 GPM aproximadamente, con variaciones según supuestos del modelo), valores en GPM y m³/h, fórmulas explícitas, supuestos declarados y al menos una referencia normativa CTI o ASHRAE.

> **Nota:** Los valores numéricos exactos pueden variar entre modelos de IA y entre ejecuciones. Lo relevante para la evaluación es la presencia de estructura, fórmulas, unidades y referencias, no la coincidencia numérica exacta.

**Verificación:** Confirmar que la respuesta contiene los cinco elementos solicitados (tabla, desglose, fórmulas, supuestos, referencias). Si falta algún elemento, anotar cuál falta — esto será un dato útil para la matriz de evaluación.

---

### Paso 3: Crear la matriz de evaluación comparativa

**Objetivo:** Construir la herramienta de evaluación que permitirá comparar de forma objetiva ambas respuestas.

**Instrucciones:**

1. Abrir la hoja de cálculo (Google Sheets, Excel o LibreOffice Calc).
2. En la primera hoja (o pestaña), asignar el nombre `Matriz_Comparacion_Lab04-02`.
3. Crear la siguiente estructura de tabla a partir de la celda A1:

```
| Celda | Contenido                                              |
|-------|--------------------------------------------------------|
| A1    | Criterio de Evaluación                                 |
| B1    | Puntuación Prompt Genérico (1-5)                       |
| C1    | Puntuación Prompt Estructurado (1-5)                   |
| D1    | Diferencia (C-B)                                       |
| E1    | Observaciones                                          |
| A2    | 1. Precisión técnica                                   |
| A3    | 2. Completitud de la respuesta                         |
| A4    | 3. Claridad y organización                             |
| A5    | 4. Uso correcto de unidades y terminología             |
| A6    | 5. Facilidad de uso en documento de ingeniería         |
| A7    | PROMEDIO                                               |
```

4. En la celda D2, ingresar la fórmula para calcular la diferencia automáticamente:

```
=C2-B2
```

5. Copiar la fórmula de D2 hacia abajo hasta D6 (para los cinco criterios).
6. En la celda B7, ingresar la fórmula de promedio:

```
=AVERAGE(B2:B6)
```

7. Copiar la fórmula equivalente en C7 y D7:

```
=AVERAGE(C2:C6)
```

```
=AVERAGE(D2:D6)
```

**Resultado esperado:** Una tabla con 5 criterios de evaluación, columnas para puntuación de cada tipo de prompt (escala 1-5), diferencia calculada automáticamente y columna de observaciones. Las celdas de puntuación (B2:C6) y observaciones (E2:E6) estarán vacías, listas para el siguiente paso.

**Verificación:** Confirmar que las fórmulas de diferencia y promedio funcionan correctamente ingresando valores de prueba temporales (por ejemplo, 3 y 4) en B2 y C2, y verificando que D2 muestra 1 y que B7/C7 calculan correctamente. Borrar los valores de prueba antes de continuar.

---

### Paso 4: Evaluar ambas respuestas con la escala de rúbrica

**Objetivo:** Aplicar criterios de evaluación objetivos a ambas respuestas, asignando puntuaciones en la escala 1-5 y documentando observaciones específicas.

**Instrucciones:**

1. Consultar la siguiente rúbrica de puntuación para cada criterio:

```text
Escala de puntuación (aplicar a cada criterio):
  1 = Ausente o completamente inadecuado
  2 = Presente pero con errores significativos o muy incompleto
  3 = Parcialmente correcto, falta profundidad o tiene omisiones notables
  4 = Correcto y útil, con mejoras menores posibles
  5 = Excelente: preciso, completo y directamente utilizable
```

2. Con ambas conversaciones de IA abiertas (Paso 1 y Paso 2), evaluar la respuesta del **prompt genérico** para cada criterio y registrar la puntuación en la columna B (celdas B2 a B6).
3. Evaluar la respuesta del **prompt estructurado** para cada criterio y registrar la puntuación en la columna C (celdas C2 a C6).
4. Para cada criterio, redactar una observación concreta en la columna E que justifique la diferencia de puntuación. Ejemplos de observaciones útiles:

```text
Criterio: Precisión técnica
Observación ejemplo: "El prompt genérico presenta la fórmula de evaporación
sin especificar el factor utilizado (0.001 vs 0.0008). El prompt estructurado
usa E = 0.001 × ΔT × Qrecirc referenciando CTI ATC-105 y declara el supuesto."
```

```text
Criterio: Uso correcto de unidades
Observación ejemplo: "El prompt genérico expresa resultados solo en GPM.
El prompt estructurado incluye conversión a m³/h con factor 0.2271 y
presenta ambas unidades en la tabla, facilitando uso internacional."
```

5. Verificar que la columna D (Diferencia) se haya calculado automáticamente para los cinco criterios y que la fila 7 (PROMEDIO) muestre los promedios correctos.

**Resultado esperado:** La matriz completada con 10 puntuaciones (5 por cada tipo de prompt), 5 diferencias calculadas y 5 observaciones justificadas. Es esperable que la diferencia promedio sea positiva (a favor del prompt estructurado), típicamente entre 1.5 y 3.0 puntos en la escala de 5.

**Verificación:** Confirmar que:
- Todas las celdas B2:B6 y C2:C6 contienen valores entre 1 y 5.
- Las celdas D2:D6 muestran diferencias coherentes (valores positivos si el prompt estructurado fue mejor evaluado).
- Cada celda E2:E6 contiene al menos una oración de observación con evidencia concreta de la respuesta evaluada.

---

### Paso 5: Caso adversarial — verificar limitaciones de ambas respuestas

**Objetivo:** Evaluar si alguna de las dos respuestas contiene información incorrecta, inventada o no verificable, para reforzar la importancia de la supervisión humana sobre los resultados de IA.

**Instrucciones:**

1. Revisar la respuesta del prompt estructurado (Paso 2) y verificar los siguientes elementos contra conocimiento de ingeniería o documentación de referencia:

```text
Lista de verificación adversarial:
□ ¿La fórmula de evaporación es consistente con CTI ATC-105 o ASHRAE?
  (Fórmula estándar: E ≈ 0.001 × ΔT(°F) × Qrecirc(GPM))
□ ¿El factor de drift utilizado es razonable?
  (Rango típico: 0.001%–0.005% del caudal de recirculación para torres modernas)
□ ¿La fórmula de blowdown es correcta?
  (B = E / (CoC - 1), donde CoC = ciclos de concentración)
□ ¿La conversión GPM a m³/h utiliza el factor correcto?
  (1 GPM = 0.22712 m³/h)
□ ¿Las referencias normativas citadas existen realmente?
  (Verificar que no sean inventadas por el modelo)
```

2. Si se identifica algún error o dato no verificable, agregar una fila adicional en la hoja de cálculo (fila 8) con el encabezado:

```text
A8: NOTA: Limitaciones identificadas
E8: [Describir el error o dato no verificable encontrado]
```

3. Si ambas respuestas son consistentes con las fórmulas de referencia, registrar igualmente en E8:

```text
E8: Ambas respuestas verificadas contra fórmulas estándar CTI. No se detectaron
errores factuales en esta revisión. Nota: esta verificación no sustituye la
validación por un ingeniero de procesos calificado.
```

**Resultado esperado:** Al menos un hallazgo documentado sobre la verificabilidad de las respuestas. Es común que el modelo invente códigos normativos específicos (por ejemplo, citar un número de sección inexistente de CTI ATC-105) o que utilice factores de drift fuera del rango típico.

**Verificación:** Confirmar que la fila 8 de la hoja de cálculo contiene una nota sobre limitaciones o sobre la verificación realizada.

---

### Paso 6: Redactar conclusiones y hallazgos

**Objetivo:** Sintetizar los resultados de la comparación en al menos tres hallazgos concretos que identifiquen qué elementos del prompt estructurado generaron la mayor mejora en calidad.

**Instrucciones:**

1. Debajo de la matriz de evaluación (a partir de la fila 10 de la hoja de cálculo, o en un documento de texto separado), redactar una sección titulada `Conclusiones — Lab 04-00-02`.
2. Incluir **al menos tres hallazgos** con la siguiente estructura para cada uno:

```text
Hallazgo [N]:
- Elemento del prompt que generó la mejora: [Rol / Contexto / Datos técnicos /
  Formato de salida / Criterios de calidad]
- Criterio de evaluación más impactado: [nombre del criterio]
- Evidencia: [descripción concreta de la diferencia observada entre ambas respuestas]
- Diferencia de puntuación: [valor de la columna D para ese criterio]
```

3. Después de los tres hallazgos, redactar un párrafo de cierre (3-5 oraciones) que responda a la pregunta: **¿Qué componente del prompt estructurado genera el mayor impacto en la calidad de la respuesta para aplicaciones de ingeniería?**

4. Guardar el archivo de la hoja de cálculo con el nombre:

```text
Matriz_Comparacion_Lab04-02_[INICIALES_PARTICIPANTE].xlsx
```

   (O el formato correspondiente: `.ods` para LibreOffice, o el archivo de Google Sheets con ese nombre.)

**Resultado esperado:** Un documento que contenga la matriz de evaluación completada, la nota de limitaciones y al menos tres hallazgos estructurados con evidencia concreta, más un párrafo de conclusión. Este documento constituye el entregable principal del laboratorio.

**Verificación:** Confirmar que:
- Existen al menos 3 hallazgos redactados, cada uno vinculando un elemento del prompt con un criterio de evaluación.
- Cada hallazgo incluye evidencia específica (no genérica) extraída de las respuestas reales obtenidas.
- El párrafo de cierre identifica explícitamente el componente de mayor impacto.
- El archivo está guardado con el nombre indicado.

## Validación y Pruebas

Utilizar la siguiente lista de verificación para confirmar que el laboratorio se completó satisfactoriamente:

| # | Criterio de validación | Evidencia requerida | ¿Cumple? |
|---|---|---|---|
| 1 | Prompt genérico enviado y respuesta obtenida | Conversación abierta en la herramienta de IA con el prompt del Paso 1 | ☐ |
| 2 | Prompt estructurado enviado y respuesta obtenida | Conversación separada con el prompt del Paso 2 (cinco componentes presentes) | ☐ |
| 3 | Matriz de evaluación con estructura correcta | Hoja de cálculo con 5 criterios, 4 columnas de datos y fórmulas funcionales | ☐ |
| 4 | Puntuaciones completas para ambos prompts | 10 valores numéricos (1-5) en celdas B2:C6 | ☐ |
| 5 | Observaciones justificadas | 5 observaciones en columna E con evidencia concreta de las respuestas | ☐ |
| 6 | Verificación adversarial realizada | Fila 8 con nota sobre limitaciones o verificación de las respuestas | ☐ |
| 7 | Tres hallazgos documentados | Cada hallazgo vincula un elemento del prompt con un criterio y presenta evidencia | ☐ |
| 8 | Párrafo de conclusión con componente de mayor impacto identificado | Texto de 3-5 oraciones respondiendo la pregunta del Paso 6 | ☐ |
| 9 | Diferencia promedio positiva a favor del prompt estructurado | Celda D7 con valor > 0 | ☐ |

### Caso adversarial — Validación de supervisión humana

El criterio 6 de la tabla anterior (verificación adversarial del Paso 5) es obligatorio. Este laboratorio no se considera completo si el participante no ha verificado al menos un dato técnico de la respuesta de IA contra una fuente o conocimiento de referencia. La IA generativa puede producir respuestas convincentes pero incorrectas (alucinaciones), especialmente en:

- Códigos normativos o números de sección específicos.
- Factores de conversión con decimales incorrectos.
- Valores de parámetros de diseño fuera de rangos estándar de la industria.

La capacidad de detectar estas limitaciones es un resultado de aprendizaje fundamental de este laboratorio.

## Solución de Problemas

### Problema 1: La herramienta de IA rechaza el mensaje o indica límite de uso alcanzado

**Síntoma:** Al enviar el prompt (genérico o estructurado), la herramienta muestra un mensaje como "Has alcanzado el límite de mensajes" (ChatGPT), "Usage limit reached" (Claude) o "Quota exceeded" (Gemini).

**Causa:** Las versiones gratuitas de las herramientas de IA tienen límites de mensajes por hora o por día. El prompt estructurado del Paso 2, al ser extenso, puede consumir más tokens y acercarse al límite más rápidamente.

**Solución:**
1. Esperar el tiempo indicado por la herramienta (generalmente 1-3 horas para ChatGPT gratuito, variable para otros).
2. Si el tiempo de espera excede la duración del laboratorio, cambiar a una herramienta alternativa:
   - ChatGPT: [https://chat.openai.com](https://chat.openai.com)
   - Claude: [https://claude.ai](https://claude.ai)
   - Gemini: [https://gemini.google.com](https://gemini.google.com)
3. Si ninguna herramienta está disponible, solicitar al instructor que comparta capturas de pantalla de respuestas pre-generadas para ambos prompts y completar la evaluación con esas respuestas.

---

### Problema 2: Las puntuaciones de ambos prompts son muy similares (diferencia promedio < 0.5)

**Síntoma:** Al completar la matriz de evaluación, la diferencia promedio en la celda D7 es menor a 0.5, sugiriendo que ambos prompts produjeron respuestas de calidad comparable.

**Causa:** Esto puede ocurrir por dos razones: (a) el modelo de IA utilizado tiene un comportamiento particularmente robusto ante prompts vagos para temas comunes como torres de enfriamiento, o (b) la evaluación no está diferenciando suficientemente entre respuestas genéricas y respuestas específicas al caso.

**Solución:**
1. Revisar la rúbrica del Paso 4 y re-evaluar específicamente el criterio "Facilidad de uso en documento de ingeniería": ¿la respuesta del prompt genérico podría copiarse directamente a un reporte trimestral de mantenimiento de la CT-4500X sin edición? Generalmente la respuesta es no.
2. Verificar el criterio "Precisión técnica": ¿la respuesta genérica calculó valores específicos para 4,500 GPM con 5 ciclos de concentración, o presentó solo fórmulas sin aplicar?
3. Si después de la re-evaluación la diferencia sigue siendo mínima, documentar esto como un hallazgo válido en las conclusiones: algunos modelos de IA compensan parcialmente la falta de estructura en el prompt para temas bien representados en sus datos de entrenamiento, pero esto no es generalizable a todos los casos de ingeniería.

## Limpieza

1. **Conversaciones de IA:** Las dos conversaciones (prompt genérico y prompt estructurado) pueden mantenerse abiertas como referencia para los laboratorios del Módulo 5.0 o eliminarse según preferencia del participante. No contienen información confidencial (se utilizó información ficticia).
2. **Archivo de hoja de cálculo:** Conservar el archivo `Matriz_Comparacion_Lab04-02_[INICIALES_PARTICIPANTE]` — es un entregable del laboratorio y servirá como referencia metodológica para los labs del Módulo 5.0.
3. **Documento de plantillas del lab 04-00-01:** Mantener accesible — se continuará utilizando en laboratorios posteriores.

## Resumen

En este laboratorio se aplicó de forma práctica la relación directa entre la calidad de un prompt y la calidad de la respuesta generada por un modelo de IA, concepto central de la lección 4.1. Al resolver el mismo caso de ingeniería (cálculo de agua de reposición para la torre CT-4500X) con un prompt genérico y un prompt estructurado con cinco componentes (rol, contexto, datos técnicos, formato de salida y criterios de calidad), se demostró de forma medible que:

- **La estructura del prompt** transforma una respuesta genérica en un resultado técnicamente utilizable.
- **Los elementos de mayor impacto** suelen ser el formato de salida (que determina la organización) y los datos técnicos específicos (que permiten cálculos aplicados en lugar de fórmulas generales).
- **La supervisión humana** es indispensable: incluso un prompt bien estructurado puede generar valores incorrectos, referencias normativas inventadas o supuestos no declarados.

La matriz de evaluación y las conclusiones generadas en este laboratorio constituyen una herramienta reutilizable para evaluar la calidad de cualquier interacción con IA generativa en contextos de ingeniería.

### Conexión con los siguientes laboratorios

Los entregables de este laboratorio (matriz de evaluación y conclusiones) servirán como referencia metodológica en el Módulo 5.0, donde se aplicarán prompts estructurados en herramientas específicas (ChatGPT Advanced Data Analysis, Claude para análisis de documentos) y en flujos automatizados con n8n.

### Recursos adicionales

| Recurso | URL |
|---|---|
| OpenAI — Guía de ingeniería de prompts | [https://platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering) |
| Anthropic — Diseño de prompts para Claude | [https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) |
| Google — Guía de prompts para Gemini | [https://ai.google.dev/gemini-api/docs/prompting-intro](https://ai.google.dev/gemini-api/docs/prompting-intro) |
| CTI — Cooling Technology Institute (referencia normativa del caso) | [https://www.cti.org](https://www.cti.org) |
