# Práctica 10. Configurar un asistente en Google AI Studio que utilice documentación técnica (manuales, especificaciones y procedimientos) como base de conocimiento para responder consultas del equipo de ingeniería, apoyar la resolución de incidencias y generar recomendaciones estandarizadas para el seguimiento y control de procesos

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán **Google AI Studio** para configurar un asistente especializado que integre documentación técnica como base de conocimiento, permitiendo procesar manuales, especificaciones y procedimientos para responder consultas operativas, resolver incidencias y generar recomendaciones estandarizadas para el control de procesos[cite: 5].

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Configuración del sistema y carga de documentación técnica:**
   * El instructor ingresa a la plataforma **Google AI Studio**, crea un nuevo "Chat Prompt" y utiliza la sección de configuración de contexto y subida de archivos para cargar los manuales mediante el siguiente prompt:
     ```text
     Actúa como un Administrador de Modelos y Arquitecto de Datos Técnicos.
     Configura este asistente integrando los manuales de equipos, especificaciones técnicas y procedimientos operativos subidos como base de conocimiento estricta para resolver dudas de ingeniería.
     ```

2. **Definición de directrices y restricciones en System Instructions:**
   * El instructor establece el comportamiento del asistente utilizando el panel de instrucciones del sistema con el siguiente comando:
     ```text
     Actúa como un Ingeniero Consultor de Soporte Técnico Industrial.
     Responde exclusivamente basándote en los manuales y especificaciones técnicas proporcionadas en el contexto, evitando suposiciones y citando la fuente exacta en cada recomendación operativa.
     ```

3. **Prueba en vivo de resolución de incidencias y control de procesos:**
   * El instructor realiza una simulación de falla en el chat de prueba utilizando la siguiente instrucción para evaluar la respuesta del asistente:
     ```text
     Actúa como un Supervisor de Turno de Ingeniería.
     Diagnostica la causa raíz de una baja de presión en el sistema principal de bombeo y genera una recomendación estandarizada para el seguimiento y control correctivo.
     ```

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Creación del Chat Prompt en Google AI Studio:**
   * Abre la interfaz de **Google AI Studio** con tu cuenta institucional y selecciona la opción para crear un nuevo **Chat Prompt**.

2. **Configuración de las instrucciones del sistema (System Instructions):**
   * Configura el rol y las reglas del asistente utilizando la siguiente directriz en el panel de system instructions:
     ```text
     Actúa como un Asistente Experto en Confiabilidad y Procesos de Ingeniería.
     Utiliza la documentación técnica provista para guiar al equipo en la solución de problemas, estandarizar procedimientos de mantenimiento y asegurar el cumplimiento de las normativas vigentes.
     ```

3. **Carga de fuentes y manuales en la base de conocimiento:**
   * Añade tus archivos PDF, manuales de equipos o especificaciones mediante el botón de adjuntar archivos en la interfaz y envía la siguiente instrucción en el chat:
     ```text
     Procesa los archivos de manuales técnicos y procedimientos cargados en la sesión para indexarlos como referencia única en las futuras consultas del equipo de ingeniería.
     ```

4. **Consulta para la resolución de incidencias operativas:**
   * Envía un caso práctico de falla en el chat del asistente utilizando el siguiente prompt para obtener un diagnóstico estandarizado:
     ```text
     Actúa como un Ingeniero de Mantenimiento Correctivo.
     Analiza la incidencia de sobrecalentamiento reportada en el compresor de aire industrial según los manuales cargados, y detalla los pasos de inspección y las recomendaciones de control.
     ```

5. **Generación de recomendaciones estandarizadas para el control de procesos:**
   * Pide al asistente que consolide el formato operativo final mediante la siguiente instrucción en el chat:
     ```text
     Genera un reporte estandarizado con el formato de seguimiento y control de procesos para prevenir la recurrencia de la incidencia anterior, dejándolo listo para exportar a la documentación del área de ingeniería.
     ```

## Resultado esperado
Un asistente configurado y optimizado en **Google AI Studio**, capaz de utilizar manuales, especificaciones y procedimientos como base de conocimiento técnica para resolver incidencias de ingeniería y generar recomendaciones estandarizadas de control[cite: 5].
