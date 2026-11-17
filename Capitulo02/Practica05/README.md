# Práctica 5. Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán **n8n Cloud** y su asistente de inteligencia artificial en la pantalla principal para construir un flujo automatizado **escribiendo una sola instrucción en lenguaje natural**. No necesitarán hacer clic en ningún bloque, configurar ajustes avanzados ni programar; el sistema generará y conectará todo automáticamente para recibir reportes, clasificarlos mediante IA, crear resúmenes ejecutivos y redactar notificaciones.

---

## Sección 0: Acceso a la Interfaz y Conceptos Básicos

1. **Paso a paso para ingresar a n8n Cloud:**
   * Ingresa a la plataforma n8n con tus credenciales institucionales.
   * Al iniciar sesión, verás de forma predeterminada la pantalla principal del asistente con la barra de texto central bajo la pregunta **What do you want to automate?**.
   * Todo el trabajo se realiza directamente en este chat, dejando que la inteligencia artificial dibuje y conecte los bloques por ti.

2. **Conceptos clave en lenguaje sencillo:**
   * **Automatización Conversacional:** Creación de flujos de trabajo dictando órdenes directas por escrito a la IA, sin manipular componentes visuales uno por uno.
   * **Chat de Prueba Integrado:** Ventana de conversación directa que permite enviar mensajes normales para verificar el funcionamiento del flujo al instante.

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Creación automática del flujo mediante una orden directa:**
   * El instructor se ubica en la barra de chat del asistente (**What do you want to automate?**) y escribe un único comando maestro:
     ```text
     Crea un flujo automatizado completo que inicie con un chat de prueba para escribir un reporte técnico,
     luego use inteligencia artificial para clasificar el tipo de incidencia (Mecánica o Eléctrica),
     genere un resumen ejecutivo corto y redacte una notificación automática para el responsable del área.
     ```

2. **Verificación visual del flujo generado por la IA:**
   * El instructor muestra cómo la pantalla de n8n se llena automáticamente con los bloques conectados sin haber tenido que abrir ni configurar ningún nodo de forma manual.

3. **Prueba inmediata escribiendo un mensaje:**
   * El instructor abre el chat lateral, escribe un reporte normal *"La bomba de agua principal vibra demasiado y subió su temperatura"*, y muestra cómo la IA responde al instante con la clasificación, el resumen y la alerta redactada.

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Acceso al chat principal del asistente en n8n Cloud:**
   * Desde tu panel principal de n8n Cloud, mantén la vista en la barra de texto central con la pregunta **What do you want to automate?** (o haz clic en **Assistant** en el menú izquierdo).

2. **Envío del prompt maestro para que la IA haga todo el trabajo:**
   * Copia y envía la siguiente instrucción detallada dentro del chat de la inteligencia artificial:
     ```text
     Construye un flujo automatizado de punta a punta que haga lo siguiente:
     1. Inicie con un nodo de Chat (Chat Trigger) para recibir reportes técnicos en texto normal.
     2. Conecte un nodo de inteligencia artificial encargado de analizar el mensaje.
     3. Clasifique la incidencia en: Mecánica, Eléctrica, Instrumentación o Control.
     4. Genere un resumen ejecutivo de dos líneas con la urgencia y redacte un correo formal de notificación listo para el jefe de mantenimiento.
     Genera todo el flujo automáticamente en mi pantalla.
     ```

3. **Verificación visual del flujo generado por la IA:**
   * Observa cómo el asistente de n8n despliega instantáneamente los bloques conectados en tu lienzo de trabajo sin requerir que hagas clic en ninguno de ellos para configurarlos.

4. **Apertura del chat de prueba para enviar un reporte real:**
   * En la parte inferior o lateral de tu pantalla, haz clic en el botón de prueba o en **Open chat**.
   * Escribe y envía el siguiente reporte técnico en lenguaje cotidiano (sin códigos ni formatos especiales):
     ```text
     Hola, reporto que en la Planta Norte el motor principal de la faja transportadora comenzó a emitir chispas y un fuerte olor a quemado, lo que puede detener toda la operación si no se revisa de inmediato.
     ```

5. **Verificación del resultado instantáneo:**
   * Revisa la ventana de conversación y observa cómo el sistema procesa tu mensaje de forma autónoma, entregando la clasificación de la incidencia como **Eléctrica**, el resumen ejecutivo de la falla y el mensaje de notificación listo para el responsable.

## Resultado esperado
Un flujo automatizado completo en **n8n Cloud**, construido enteramente mediante una orden en lenguaje natural en el asistente de inteligencia artificial, capaz de recibir reportes técnicos en texto normal, clasificarlos y generar resúmenes con alertas automáticas sin necesidad de abrir ni configurar ningún bloque manualmente.
