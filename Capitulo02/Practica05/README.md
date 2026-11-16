# Práctica 5. Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes construirán un flujo de automatización optimizado utilizando la plataforma Low-Code **n8n**[cite: 4], integrando un nodo de Inteligencia Artificial para procesar de manera totalmente autónoma un reporte técnico simulado. El flujo recibirá la información, clasificará la incidencia, generará un resumen ejecutivo y estructurará una notificación automática en el tiempo estimado.

---

## Componentes y Arquitectura del Flujo en n8n
* **Nodo Trigger (Manual/Webhook):** Inicia la ejecución simulando la recepción del reporte de ingeniería.
* **Nodo de Inteligencia Artificial (Advanced AI / LLM):** Procesa el texto mediante instrucciones generativas internas.
* **Nodo de Procesamiento:** Extrae los campos clave de la respuesta del modelo.
* **Nodo de Notificación:** Simula el envío de la alerta al departamento correspondiente.

---

## Sección 1: Demostración del Instructor - Tres Pasos

1. **Configuración del nodo inicial y generación del reporte técnico en n8n:**
   * Abre tu entorno de n8n, crea un nuevo flujo y añade un nodo disparador manual que conecte con un nodo de Inteligencia Artificial utilizando la siguiente instrucción generativa:
     ```text
     Actúa como un Ingeniero de Confiabilidad.
     Genera de manera autónoma un reporte técnico breve sobre la falla de un equipo rotativo en planta,
     clasifica la incidencia en una categoría operativa y redacta un resumen ejecutivo de dos líneas.
     ```

2. **Estructuración y transformación de datos en n8n:**
   * Conecta el nodo anterior a una sección de procesamiento lógico configurada con el siguiente comando conversacional para la IA:
     ```text
     Actúa como un Arquitecto de Automatización.
     Toma los datos procesados y estructúralos en formato limpio con los campos:
     categoria, resumen_ejecutivo y severidad, asegurando que el contenido sea autogenerado.
     ```

3. **Configuración de la notificación automática en n8n:**
   * Finaliza la demostración conectando un nodo de salida simulado con la siguiente instrucción:
     ```text
     Actúa como un Coordinador de Operaciones.
     Redacta el mensaje de alerta final integrando la categoría y el resumen ejecutivo para notificar al equipo responsable.
     ```

---

## Sección 2: Práctica Guiada del Participante - Cinco Pasos

1. **Creación del workflow y autogeneración del reporte en n8n:**
   * Crea un nuevo proyecto en n8n, añade un nodo disparador e integra un nodo de IA con la siguiente instrucción para autogenerar el caso base:
     ```text
     Actúa como un Ingeniero de Mantenimiento.
     Genera de manera completamente autónoma un reporte de incidente sobre una sobrecarga térmica en un tablero eléctrico de control.
     ```

2. **Integración del nodo de IA para clasificación automática en n8n:**
   * Añade y configura un nodo de modelo de lenguaje dentro del flujo utilizando el siguiente prompt interno:
     ```text
     Actúa como un Especialista en Diagnóstico de Fallas.
     Analiza el reporte eléctrico autogenerado y clasifica el tipo de incidencia (Térmica, Eléctrica o Mecánica)
     junto con una breve justificación técnica.
     ```

3. **Construcción del nodo de resumen ejecutivo mediante instrucciones generativas:**
   * Conecta un nodo sucesivo para condensar la información con el siguiente comando:
     ```text
     Actúa como un Ingeniero Documentador.
     Extrae la información principal del análisis anterior y genera un resumen ejecutivo de dos líneas
     enfocado en la acción correctiva inmediata.
     ```

4. **Configuración de reglas de enrutamiento y severidad en n8n:**
   * Añade un nodo de decisión lógica (If/Switch) en n8n y configúralo mediante la siguiente instrucción conversacional:
     ```text
     Actúa como un Gestor de Operaciones.
     Establece la regla para que las incidencias críticas sean derivadas al canal prioritario de guardia
     y las moderadas al buzón de mantenimiento rutinario.
     ```

5. **Prueba integral, ejecución y validación final en n8n:**
   * Ejecuta una prueba manual del flujo completo (Test Workflow) en n8n y verifica el resultado con el siguiente comando:
     ```text
     Actúa como un Administrador de Sistemas.
     Simula la ejecución final del flujo en n8n y redacta una breve constancia que confirme
     la recepción, clasificación, resumen y notificación automática de la incidencia.
     ```

## Resultado esperado
Un flujo funcional optimizado para 30 minutos en **n8n**, basado en datos 100% autogenerados por inteligencia artificial, capaz de clasificar incidencias, resumir reportes y estructurar notificaciones operativas sin requerir archivos externos.
