# Práctica 6. Diseñar un flujo automatizado que procese un archivo con indicadores de operación, identifique desviaciones mediante IA y genere automáticamente un reporte técnico para apoyar el monitoreo y control del proceso

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán **n8n Cloud** y su asistente de inteligencia artificial en la pantalla principal para construir un flujo automatizado **escribiendo una sola instrucción definitiva en lenguaje natural**. No necesitarán hacer clic en ningún bloque, subir archivos complejos ni programar; el sistema generará y conectará todo automáticamente para recibir datos de indicadores operativos, detectar desviaciones mediante IA y redactar un reporte técnico de monitoreo y control.

---

## Sección 0: Acceso a la Interfaz y Conceptos Básicos

1. **Paso a paso para ingresar a n8n Cloud:**
   * Ingresa a la plataforma n8n con tus credenciales institucionales.
   * Al iniciar sesión, verás de forma predeterminada la pantalla principal del asistente con la barra de texto central bajo la pregunta **What do you want to automate?**.
   * Todo el trabajo se realiza directamente en este chat, dejando que la inteligencia artificial dibuje y conecte los bloques por ti.

2. **Conceptos clave en lenguaje sencillo:**
   * **Automatización Conversacional:** Creación de flujos de trabajo dictando órdenes directas por escrito a la IA, sin manipular componentes visuales uno por uno ni escribir código.
   * **Chat de Prueba Integrado:** Ventana de conversación directa que permite pegar registros o indicadores en texto normal para verificar el análisis automático al instante.

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Creación automática del flujo mediante una orden definitiva:**
   * El instructor se ubica en la barra de chat del asistente (**What do you want to automate?**) y escribe el siguiente comando maestro definitivo:
     ```text
     Crea un flujo automatizado completo que inicie con un chat de prueba para pegar indicadores operativos,
     luego use inteligencia artificial para identificar desviaciones frente a las metas esperadas
     y genere automáticamente un reporte técnico breve para el monitoreo y control del proceso.
     ```

2. **Verificación visual del flujo generado por la IA:**
   * El instructor muestra cómo la pantalla de n8n se llena automáticamente con los bloques conectados sin haber tenido que abrir ni configurar ningún nodo de forma manual.

3. **Prueba inmediata con datos de control:**
   * El instructor abre el chat lateral, pega los indicadores operativos y muestra cómo la IA responde al instante con las desviaciones detectadas y el reporte técnico generado.

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Acceso al chat principal del asistente en n8n Cloud:**
   * Desde tu panel principal de n8n Cloud, mantén la vista en la barra de texto central con la pregunta **What do you want to automate?** (o haz clic en **Assistant** en el menú izquierdo).

2. **Envío del prompt maestro definitivo para que la IA haga todo el trabajo:**
   * Copia y envía la siguiente instrucción detallada dentro del chat de la inteligencia artificial:
     ```text
     Construye un flujo automatizado de monitoreo operativo de punta a punta que haga lo siguiente:
     1. Inicie con un nodo de Chat (Chat Trigger) para recibir datos y registros de indicadores de operación en texto normal.
     2. Conecte un nodo de inteligencia artificial encargado de analizar las métricas recibidas.
     3. Identifique claramente qué indicadores presentan desviaciones críticas respecto a sus valores esperados.
     4. Genere automáticamente un reporte técnico estructurado con el diagnóstico de las desviaciones y recomendaciones de control del proceso.
     Genera todo el flujo automáticamente en mi pantalla.
     ```

3. **Verificación visual del flujo generado por la IA:**
   * Observa cómo el asistente de n8n despliega instantáneamente los bloques conectados en tu lienzo de trabajo sin requerir que hagas clic en ninguno de ellos para configurarlos.

4. **Apertura del chat de prueba para enviar el registro de indicadores:**
   * En la parte inferior o lateral de tu pantalla, haz clic en el botón de prueba o en **Open chat**.
   * Copia y envía el siguiente bloque de indicadores operativos en texto cotidiano (simulando el contenido de un reporte de turno, sin códigos ni formatos complejos):
     ```text
     Registro de Indicadores - Turno Mañana Planta Empaque:
     - Disponibilidad de Línea: Meta 95% | Real obtenido 82% (2 paradas por atasco en etiquetadora).
     - Consumo Energético: Meta 450 kWh | Real obtenido 530 kWh.
     - Tasa de Desperdicio: Meta máxima 1.5% | Real obtenido 3.8%.
     - Velocidad de Envasado: Meta 120 botellas/min | Real obtenido 118 botellas/min.
     ```

5. **Verificación del resultado instantáneo:**
   * Revisa la ventana de conversación y observa cómo el sistema procesa los datos de forma autónoma, identificando las desviaciones en **Disponibilidad de Línea**, **Consumo Energético** y **Tasa de Desperdicio**, y entregando el reporte técnico listo para el monitoreo y control del proceso.

## Resultado esperado
Un flujo automatizado completo en **n8n Cloud**, construido enteramente mediante una orden en lenguaje natural en el asistente de inteligencia artificial, capaz de procesar indicadores de operación en texto normal, detectar desviaciones automáticamente y redactar reportes técnicos de control sin necesidad de abrir ni configurar ningún bloque manualmente.
