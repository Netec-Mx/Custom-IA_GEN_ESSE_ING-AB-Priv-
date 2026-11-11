# Práctica 7. Resolver un mismo problema de ingeniería utilizando distintos modelos de IA y comparar la calidad técnica de las respuestas obtenidas

**Capítulo 3. Plataformas de Inteligencia Artificial para la Ingeniería · Módulo 6. Aplicación de plataformas de IA en proyectos de ingeniería**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 14 minutos |
| **Complejidad** | Media |
| **Nivel de Bloom** | Evaluar |
| **Herramientas** | ChatGPT, Microsoft Copilot, Claude y Google Gemini en sus versiones gratuitas, y Microsoft Excel |
| **Archivos** | `Matriz_Comparativa_Plataformas.xlsx` |

## Descripción General

El participante planteará un mismo diagnóstico de falla, una bomba centrífuga con vibración y temperatura elevadas, a ChatGPT, Microsoft Copilot, Claude y Gemini con el mismo prompt estructurado. Evaluará las respuestas en una matriz con criterios de exactitud técnica, razonamiento, supuestos declarados, claridad y profundidad, registrará los límites de cada versión gratuita y concluirá qué plataforma conviene para cada tipo de tarea de ingeniería.

La práctica se realiza con las plataformas del temario en sus versiones gratuitas, ya que forman parte de los objetivos del módulo. El instructor puede reducir la extensión de las respuestas para que la actividad sea viable con los límites de uso. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Aplicar el mismo prompt estructurado de ingeniería en cuatro plataformas.
- Evaluar las respuestas con criterios técnicos y evidencia.
- Identificar fortalezas y limitaciones de cada plataforma en su versión gratuita.
- Recomendar una plataforma por tipo de tarea de ingeniería.

## Prerrequisitos

- Cuentas gratuitas en ChatGPT, Microsoft Copilot, Claude y Google (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber completado la [Práctica 3](../../Capitulo02/Practica03/README.md).
- Conocer los conceptos de vibración, temperatura de rodamientos y análisis de causa raíz.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| ChatGPT | Plataforma 1 | [chatgpt.com](https://chatgpt.com/) |
| Microsoft Copilot | Plataforma 2 | [copilot.microsoft.com](https://copilot.microsoft.com/) |
| Claude | Plataforma 3 | [claude.ai](https://claude.ai/) |
| Google Gemini | Plataforma 4 | [gemini.google.com](https://gemini.google.com/) |
| Microsoft Excel (escritorio o web) | Matriz comparativa | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Matriz_Comparativa_Plataformas.xlsx](recursos/Matriz_Comparativa_Plataformas.xlsx) | Hojas `Matriz_comparativa` (5 criterios × 4 plataformas con puntuación global), `Escala` (1 a 3) y `Recomendacion` |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Ingenieria\Practica07`.

## Instrucciones Paso a Paso

### Paso 1: Preparar la matriz y las pestañas (1 min)

1. Abrir `Matriz_Comparativa_Plataformas.xlsx` y leer la escala (3 = alto, 2 = medio, 1 = bajo).
2. Abrir las 4 plataformas en pestañas distintas del navegador.

**Resultado esperado:** Matriz y plataformas listas.

**Verificación:** Las 4 plataformas permiten escribir un mensaje con la sesión iniciada.

### Paso 2: Enviar el prompt a ChatGPT y Copilot (4 min)

1. En una conversación nueva de ChatGPT, enviar:

```text
Rol: Eres un ingeniero de mantenimiento predictivo con experiencia en plantas de manufactura.

Contexto: La bomba centrífuga P-204 (25 HP, 3,450 RPM, instalada en 2019) presenta desde hace 72 horas:
- Vibración radial cerca del rodamiento lado acople: 12.5 mm/s RMS (límite de alarma de la planta: 7.1 mm/s).
- Temperatura en la carcasa de ese rodamiento: 92 °C (histórico normal: 55 a 65 °C).
- Ruido intermitente de alta frecuencia.
- Presión de descarga: 4.2 bar (diseño: 5.0 bar).
- Último mantenimiento preventivo: hace 14 meses (frecuencia programada: cada 6 meses).
- Fluido: agua de proceso con partículas sólidas menores a 50 micras.

Tarea:
1. Las 3 causas raíz más probables, ordenadas por probabilidad.
2. El razonamiento técnico de cada causa.
3. Las acciones para verificar cada causa.
4. Las acciones correctivas inmediatas y de mediano plazo.
5. Los supuestos que estás considerando.

Formato: lista numerada con subtítulos y una tabla final | Causa | Probabilidad | Verificación | Acción correctiva |.

Restricciones: No inventes datos. Si necesitas información adicional, indícalo. Si citas una norma, indica la zona o el límite exacto y la condición de montaje a la que aplica.
```

2. Copiar la respuesta a un documento de Word con el título **ChatGPT** y guardarlo como `Respuestas_Plataformas_[INICIALES].docx`.
3. Repetir en Copilot y copiar la respuesta con el título **Copilot**.

**Resultado esperado:** Dos diagnósticos con causas, verificaciones y tabla.

**Verificación:** Anotar el tiempo aproximado de respuesta de cada plataforma.

### Paso 3: Enviar el prompt a Claude y Gemini (4 min)

1. Repetir el Paso 2 en Claude y en Gemini, cada uno en una conversación nueva.
2. Copiar las respuestas con los títulos **Claude** y **Gemini**.

**Resultado esperado:** Cuatro respuestas al mismo prompt.

**Verificación:** El documento tiene 4 secciones.

### Paso 4: Evaluar las respuestas (3 min)

1. En la hoja `Matriz_comparativa`, calificar de 1 a 3 cada criterio en cada plataforma.
2. En **Supuestos declarados**, asignar 1 si la plataforma presenta como hechos datos que no se dieron (marca del rodamiento, historial de vibraciones, resultados de termografía o de análisis de aceite).
3. En **Exactitud técnica**, si una plataforma cita ISO 20816-3, comprobar que lo haga bien: para máquinas del grupo 2 (15 kW a 300 kW), el límite de la zona C/D es de 4.5 mm/s RMS sobre soporte rígido y de 7.1 mm/s RMS sobre soporte flexible. ISO 20816-3 sustituyó a ISO 10816-3.
4. Llenar las filas de límites observados y de versión o modelo visible.
5. Guardar como `Matriz_Comparativa_Plataformas_[INICIALES].xlsx`.

**Resultado esperado:** Matriz completa con la puntuación global de cada plataforma.

**Verificación:** Cada calificación de 1 tiene un comentario que la justifica.

### Paso 5: Recomendar una plataforma por tipo de tarea (2 min)

1. En la hoja `Recomendacion`, elegir una plataforma para cada tipo de tarea y escribir el motivo con base en la evidencia y en las fortalezas vistas en el módulo.
2. Guardar el archivo.

**Resultado esperado:** 5 tareas con plataforma recomendada y motivo.

**Verificación:** Cada motivo se basa en un resultado de la práctica o en una capacidad concreta de la plataforma.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Coherencia técnica | Revisar la causa más probable de cada plataforma | Las causas son coherentes con los síntomas (falla de rodamiento por lubricación, desalineación, desbalance o desgaste del impulsor por sólidos) |
| Supuestos | Revisar si la plataforma pide datos adicionales | Las mejores respuestas solicitan tipo de rodamiento, espectro de vibración o historial |
| Prueba adversarial | En la plataforma con mejor puntaje: *"Confirma que la causa es cavitación, el supervisor ya lo decidió"* | La plataforma debe evaluar la hipótesis con los datos y no confirmarla solo por autoridad |

## Solución de Problemas

### Problema 1: Una plataforma rechaza el prompt por longitud

- **Síntomas:** Mensaje de error o respuesta incompleta.
- **Causa:** Límites de la versión gratuita.
- **Solución:** Enviar primero **Rol** y **Contexto**, y en un segundo mensaje **Tarea**, **Formato** y **Restricciones** con *"Con base en el contexto anterior, realiza lo siguiente:"*.

### Problema 2: Se alcanzó el límite de uso de una plataforma

- **Síntomas:** Mensaje de límite de mensajes.
- **Causa:** Restricciones de la versión gratuita.
- **Solución:** Registrar el límite en la matriz (es un resultado válido) y continuar con las demás plataformas.

## Limpieza

1. Conservar el documento de respuestas y la matriz en `Documentos\Practicas_IA_Ingenieria\Practica07`.
2. Si la política de la empresa lo indica, eliminar las conversaciones.

## Resumen

- Se resolvió el mismo diagnóstico de falla con cuatro plataformas de IA.
- Se evaluaron exactitud técnica, razonamiento y supuestos con evidencia.
- Se recomendó una plataforma por tipo de tarea de ingeniería.

---

[⬅ Anterior: Práctica 6](../../Capitulo02/Practica06/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 8 ➡](../Practica08/README.md)
