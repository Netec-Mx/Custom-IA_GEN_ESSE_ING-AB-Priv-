# Práctica 4. Comparar los resultados obtenidos mediante prompts genéricos frente a prompts correctamente estructurados para evaluar su impacto en la calidad de la información técnica

**Capítulo 2. Ingeniería de Prompts y Automatización para Procesos de Ingeniería · Módulo 4. Fundamentos de la ingeniería de prompts**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 16 minutos |
| **Complejidad** | Fácil |
| **Nivel de Bloom** | Evaluar |
| **Herramientas** | Una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude) y Microsoft Excel |
| **Archivos** | `Matriz_Evaluacion_Prompts_Tecnicos.xlsx` |

## Descripción General

El participante resolverá un mismo cálculo de ingeniería, el caudal de agua de reposición de una torre de enfriamiento, con un prompt genérico y con un prompt estructurado que incluye rol, contexto, datos técnicos, tarea, formato de salida y criterios de calidad. Comparará ambas respuestas en una matriz con criterios de precisión técnica, completitud, claridad, uso de unidades y terminología, y facilidad de uso en un documento de ingeniería, verificará el cálculo en Excel y concluirá qué elementos del prompt generan la mayor mejora.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta y ajustar la extensión del ejercicio, conservando el objetivo y el resultado esperado.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Medir con una escala de 1 a 5 la diferencia de calidad entre un prompt genérico y uno estructurado.
- Verificar un cálculo técnico generado por IA con una hoja de cálculo.
- Identificar qué elementos del prompt aportan la mayor mejora en la información técnica.

## Prerrequisitos

- Haber completado la [Práctica 3](../Practica03/README.md).
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Herramienta de IA Generativa | Ejecutar ambos prompts | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |
| Microsoft Excel (escritorio o web) | Evaluar y verificar el cálculo | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Matriz_Evaluacion_Prompts_Tecnicos.xlsx](recursos/Matriz_Evaluacion_Prompts_Tecnicos.xlsx) | Hojas `Matriz` (5 criterios con diferencia y promedio calculados), `Elementos_del_prompt` y `Verificacion_calculo` (cálculo de referencia con fórmulas) |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Ingenieria\Practica04`.

## Instrucciones Paso a Paso

### Paso 1: Revisar la matriz (1 min)

1. Abrir `Matriz_Evaluacion_Prompts_Tecnicos.xlsx` y leer los 5 criterios de la hoja `Matriz`.

**Resultado esperado:** Se conocen los criterios antes de ver las respuestas.

**Verificación:** La hoja calcula sola la diferencia y el promedio.

### Paso 2: Ejecutar el prompt genérico (3 min)

1. Iniciar una conversación nueva y enviar exactamente:

```text
Explícame cómo calcular el caudal de agua de reposición en una torre de enfriamiento.
```

2. Copiar la respuesta a un documento de Word con el título **Prueba A** y guardarlo como `Comparacion_Prompts_[INICIALES].docx`.

**Resultado esperado:** Una explicación general, posiblemente con fórmulas, pero sin cálculo aplicado a un equipo concreto.

**Verificación:** Anotar si la respuesta incluye unidades, valores numéricos y normas.

### Paso 3: Ejecutar el prompt estructurado (4 min)

1. Iniciar **otra conversación nueva** y enviar:

```text
## Rol
Eres un ingeniero de procesos con experiencia en sistemas de enfriamiento industrial y tratamiento de agua.

## Contexto
[EMPRESA_PRINCIPAL] opera una torre de enfriamiento CT-4500X. Se requiere el caudal de agua de reposición para planificar el suministro y dimensionar el tratamiento químico del reporte trimestral.

## Datos técnicos
- Caudal de recirculación: 4,500 GPM
- Rango de enfriamiento (ΔT): 10 °F
- Temperatura de bulbo seco: 95 °F
- Temperatura de bulbo húmedo: 78 °F
- Ciclos de concentración objetivo: 5

## Tarea
Calcula el caudal de reposición total desglosando evaporación, arrastre (drift) y purga (blowdown). Muestra fórmulas, valores intermedios y resultado.

## Formato de salida
Tabla | Componente | Fórmula | GPM | m³/h |, seguida de una sección de supuestos y otra de referencias.

## Criterios de calidad
- Resultados con dos decimales.
- Conversión 1 GPM = 0.2271 m³/h.
- Declarar el factor de evaporación y el porcentaje de arrastre supuestos.
- Referencias: ASHRAE Handbook — HVAC Systems and Equipment (capítulo de torres de enfriamiento) o documentación del CTI.
```

2. Copiar la respuesta al documento con el título **Prueba B**.

**Resultado esperado:** Una tabla con los tres componentes, fórmulas, supuestos y referencias.

**Verificación:** La respuesta declara el factor de evaporación que usó.

### Paso 4: Evaluar y verificar el cálculo (5 min)

**Objetivo:** Calificar con evidencia y comprobar el resultado numérico.

1. Abrir la hoja `Verificacion_calculo`: muestra la reposición de referencia con la regla de 1% de evaporación por cada 10 °F: evaporación de **45.00 GPM** y reposición total de **56.25 GPM (12.77 m³/h)**.
2. Comparar con la Prueba B. Si la IA usó otro factor de evaporación (por ejemplo, 0.0008 por °F, que da 36 GPM), el resultado es válido siempre que el factor esté declarado y la reposición cumpla: **reposición = evaporación × C / (C − 1)**.
3. En la hoja `Matriz`, calificar de 1 a 5 cada criterio para ambas pruebas y escribir la evidencia en **Observaciones**.
4. En la hoja `Elementos_del_prompt`, anotar qué aportó cada elemento y su impacto.
5. Guardar como `Matriz_Evaluacion_Prompts_Tecnicos_[INICIALES].xlsx`.

**Resultado esperado:** La matriz completa con el promedio de cada prueba.

**Verificación:** El promedio de la Prueba B es mayor. Normalmente los **datos técnicos** y los **criterios de calidad** tienen el mayor impacto en la precisión.

### Paso 5: Aplicar una prueba adversarial (2 min)

1. En la conversación de la Prueba B, enviar:

```text
Recalcula considerando que los ciclos de concentración son 1.
```

2. Anotar la respuesta en el documento.

**Resultado esperado:** La IA advierte que con 1 ciclo de concentración la fórmula de purga se indetermina (división entre cero) y que el valor no es físicamente válido para operar la torre.

**Verificación:** Si la IA entrega un número sin advertir el problema, registrarlo como error de precisión técnica.

### Paso 6: Redactar la conclusión (1 min)

1. En el documento, escribir 3 líneas: qué elementos del prompt generaron la mayor mejora y por qué.
2. Guardar ambos archivos.

**Resultado esperado:** Una conclusión respaldada por la matriz.

**Verificación:** La conclusión menciona al menos 2 elementos del prompt.

## Validación y Pruebas

| Caso | Acción | Resultado esperado |
| :--- | :--- | :--- |
| Cálculo verificable | Comparar la Prueba B con la hoja `Verificacion_calculo` | Coincide, o la diferencia se explica por un factor de evaporación declarado |
| Unidades | Revisar la conversión a m³/h | 1 GPM = 0.2271 m³/h aplicado correctamente |
| Prueba adversarial | Paso 5 | La IA detecta la condición no válida |

## Solución de Problemas

### Problema 1: Los valores de la Prueba B no coinciden con la referencia

- **Síntomas:** Evaporación distinta de 45 GPM.
- **Causa:** Existen varios factores empíricos de evaporación.
- **Solución:** Verificar que el factor esté declarado y recalcular en Excel con ese factor; calificar la precisión según la coherencia interna del cálculo.

### Problema 2: La matriz no calcula el promedio

- **Síntomas:** Las celdas de promedio aparecen vacías.
- **Causa:** Faltan calificaciones.
- **Solución:** Llenar las 5 calificaciones de cada prueba con valores de 1 a 5.

## Limpieza

1. Conservar el documento y la matriz en `Documentos\Practicas_IA_Ingenieria\Practica04`.
2. Si la política de la empresa lo indica, eliminar las conversaciones.

## Resumen

- Se resolvió el mismo cálculo con un prompt genérico y uno estructurado.
- Se verificó el resultado técnico con una hoja de cálculo.
- Se identificaron los elementos del prompt que más mejoran la información técnica.

---

[⬅ Anterior: Práctica 3](../Practica03/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 5 ➡](../Practica05/README.md)
