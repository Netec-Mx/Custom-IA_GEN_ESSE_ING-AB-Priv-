# Práctica 5. Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán **n8n Cloud** y su asistente de inteligencia artificial integrado en la pantalla principal para construir un flujo automatizado mediante instrucciones en lenguaje natural. El sistema recibirá un reporte técnico, utilizará un modelo de inteligencia artificial para clasificar el tipo de incidencia, generará un resumen ejecutivo y redactará una notificación automática para el responsable correspondiente.

---

## Sección 0: Acceso a la Interfaz y Configuración con Inteligencia Artificial

1. **Paso a paso para ingresar a n8n Cloud:**
   * Ingresa a la plataforma n8n mediante tu navegador web con tus credenciales institucionales.
   * Al iniciar sesión, la interfaz te mostrará de forma predeterminada la pantalla del asistente de inteligencia artificial con la barra de texto central bajo la pregunta **What do you want to automate?**.
   * Utilizarás directamente este chat conversacional de inteligencia artificial tanto para la demostración como para la práctica, sin necesidad de arrastrar nodos manualmente.

2. **Explicación de conceptos clave para la automatización:**
   * **Plataforma de bajo código:** Espacio visual que permite integrar aplicaciones y modelos de inteligencia artificial mediante flujos lógicos conectados, reduciendo la necesidad de programación tradicional.
   * **Estructura JSON:** Formato estándar basado en texto estructurado mediante llaves y pares de clave y valor, utilizado para intercambiar datos organizados entre sistemas.
   * **Webhook:** Mecanismo de integración que permite a una aplicación enviar información en tiempo real hacia otra plataforma cada vez que se genera un evento técnico o incidencia operativa.

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Creación del flujo automatizado mediante instrucción a la inteligencia artificial en n8n:**
   * El instructor se ubica en la barra de chat del asistente y le pide generar el flujo completo escribiendo lo siguiente:
     ```text
     Crea un flujo automatizado que reciba un reporte técnico por webhook,
     clasifique el tipo de incidencia mediante inteligencia artificial,
     genere un resumen ejecutivo y redacte una notificación automática para el responsable.
     ```

2. **Validación del esquema de datos y variables procesadas:**
   * El instructor verifica que la estructura generada automáticamente contenga los datos del equipo, la planta y la descripción de la falla listos para ser procesados.

3. **Prueba de ejecución y verificación de la salida técnica:**
   * El instructor hace clic en el botón de prueba o ejecución dentro de la misma interfaz generada por la inteligencia artificial y observa cómo el sistema entrega la clasificación de la incidencia, el resumen ejecutivo y la notificación ya listos.

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Acceso al panel principal y preparación del asistente de inteligencia artificial:**
   * Desde tu panel principal de n8n Cloud donde visualizas la barra de chat con la pregunta **What do you want to automate?**, mantén seleccionada la opción **Assistant** en el menú lateral izquierdo.

2. **Ingreso del prompt maestro para la generación automática del flujo:**
   * Escribe y envía la siguiente instrucción detallada en varias líneas dentro de la barra de chat de la inteligencia artificial de n8n:
     ```text
     Construye un flujo automatizado completo de gestión de incidencias técnicas que realice lo siguiente:
     1. Inicie con un nodo de Webhook preparado para recibir peticiones POST con reportes técnicos de planta.
     2. Integre un nodo de procesamiento de inteligencia artificial que analice el reporte recibido.
     3. Clasifique el tipo de incidencia estrictamente en Mecánica, Eléctrica, Instrumentación o Control basándote en los síntomas.
     4. Genere un resumen ejecutivo de dos líneas con la criticidad operativa y redacte una notificación formal para el responsable del área.
     ```

3. **Configuración de los datos de prueba en formato JSON dentro del flujo generado:**
   * Una vez que la inteligencia artificial genere la estructura visual del flujo, abre el nodo de entrada y configura un reporte técnico de prueba utilizando la siguiente estructura JSON:
     ```json
     {
       "reporte_id": "INC-4092",
       "planta_operativa": "Planta Petroquímica Norte",
       "equipo_afectado": "Bomba Centrífuga de Alta Presión P-104",
       "operador_reporta": "Ing. Javier Morales",
       "detalle_incidencia": "Se detecta incremento súbito de vibración axial y aumento de temperatura en el rodamiento principal por encima de los noventa grados Celsius, generando riesgo inminente de parada no programada en la línea de bombeo."
     }
     ```

4. **Ajuste de la instrucción interna del nodo de inteligencia artificial:**
   * Dentro del nodo de inteligencia artificial creado automáticamente en tu lienzo, verifica y ajusta la directriz interna para garantizar una salida limpia y estructurada mediante el siguiente comando multilineal:
     ```text
     Actúa como un Ingeniero Analista de Operaciones y Mantenimiento.
     Procesa el JSON recibido y devuelve obligatoriamente:
     Tipo de Incidencia: (Mecánica, Eléctrica, Instrumentación o Control).
     Resumen Ejecutivo: (Diagnóstico técnico y criticidad operativa en dos líneas).
     Notificación al Responsable: (Mensaje formal de alerta técnica dirigido al jefe de mantenimiento del área correspondiente).
     ```

5. **Ejecución y verificación del flujo automatizado:**
   * Haz clic en el botón de prueba o ejecución manual en tu lienzo de n8n, verifica en el panel de resultados que la inteligencia artificial procese el JSON de prueba, determine el tipo de incidencia como **Mecánica** y entregue el resumen ejecutivo junto con la notificación lista para el responsable técnico.

## Resultado esperado
Un flujo automatizado completo construido mediante el asistente de inteligencia artificial de **n8n Cloud**, capaz de recibir reportes técnicos mediante estructuras JSON, clasificarlos según el tipo de incidencia y generar resúmenes ejecutivos con notificaciones automáticas para el personal responsable.
