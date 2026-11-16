# Práctica 5. Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes construirán su primer flujo de automatización paso a paso utilizando la plataforma Low-Code **n8n**[cite: 4]. Aprenderán desde cero cómo conectar piezas visuales (llamadas nodos) para que una inteligencia artificial reciba un reporte técnico, lo lea, entienda qué tipo de falla es, cree un resumen corto y envíe una notificación automática, todo sin necesidad de saber programar.

---

## ¿Cómo funciona n8n? (Componentes y Arquitectura Básica)
Para los que nunca han usado n8n, imagina que estás armando un rompecabezas donde cada pieza cumple una función específica. Estas piezas se llaman **nodos** y se conectan entre sí mediante flechas para formar un camino o **flujo**. Los componentes principales que usaremos son:

1. **El Disparador (Trigger):** Es la pieza que da inicio a todo el proceso. Funciona como un botón de encendido o una alarma (por ejemplo, cuando alguien presiona un botón o llega un mensaje nuevo).
2. **El Nodo de Inteligencia Artificial (AI Node / LLM):** Es el "cerebro" dentro del flujo. Aquí es donde la IA lee los textos, piensa, clasifica y escribe de forma completamente autónoma usando instrucciones sencillas en lenguaje natural.
3. **El Nodo de Procesamiento o Decisión (If / Switch):** Funciona como un vigilante o desvío de tránsito. Lee lo que dijo la IA y decide por qué camino debe continuar el flujo (por ejemplo: si la falla es grave, va por el camino rojo; si es leve, va por el verde).
4. **El Nodo de Acción o Notificación:** Es la pieza final que ejecuta una tarea en el mundo exterior, como enviar un correo electrónico, un mensaje de alerta o un reporte resumido al responsable correspondiente.

---

## Sección 1: Demostración del Instructor - Tres Pasos

1. **Paso 1: Crear el inicio del flujo y la generación del reporte (Trigger + IA)**
   * Abre tu cuenta o entorno de n8n, haz clic en **New Workflow** (Nuevo Flujo).
   * Añade un nodo de tipo **Manual Trigger** (un botón que puedes presionar para probar el flujo cuando quieras).
   * Conéctalo a un nodo de Inteligencia Artificial y escribe la siguiente instrucción generativa para que la IA cree el caso base:
     ```text
     Actúa como un Ingeniero de Confiabilidad.
     Genera de manera autónoma un reporte técnico breve sobre la falla de un equipo rotativo en planta,
     clasifica la incidencia en una categoría operativa y redacta un resumen ejecutivo de deux líneas.
     ```

2. **Paso 2: Organizar y estructurar la información con la IA**
   * Conecta el nodo anterior a otro bloque de procesamiento donde le pedirás a la inteligencia artificial que ordene los datos para que sean fáciles de leer por el sistema mediante este comando:
     ```text
     Actúa como un Arquitecto de Automatización.
     Toma los datos procesados y estructúralos en formato limpio con los campos:
     categoria, resumen_ejecutivo y severidad, asegurando que el contenido sea autogenerado.
     ```

3. **Paso 3: Enviar la notificación automática**
   * Conecta una última pieza que simule el envío de la alerta. Configura la instrucción final para la IA:
     ```text
     Actúa como un Coordinador de Operaciones.
     Redacta el mensaje de alerta final integrando la categoría y el resumen ejecutivo para notificar al equipo responsable.
     ```

---

## Sección 2: Práctica Guiada del Participante - Cinco Pasos

1. **Paso 1: Iniciar el flujo desde cero y autogenerar el reporte en n8n**
   * En tu pantalla de n8n, añade un nodo de inicio (Trigger). Luego, busca y añade un nodo de Inteligencia Artificial. Haz clic en él y escribe esta instrucción para que el sistema cree un problema eléctrico de forma automática:
     ```text
     Actúa como un Ingeniero de Mantenimiento.
     Genera de manera completamente autónoma un reporte de incidente sobre una sobrecarga térmica en un tablero eléctrico de control.
     ```

2. **Paso 2: Conectar el nodo de IA para clasificar la incidencia**
   * Arrastra una flecha desde tu nodo anterior para crear un nuevo nodo de lenguaje de IA. Escribe la siguiente instrucción para que el modelo analice y separe el tipo de problema:
     ```text
     Actúa como un Especialista en Diagnóstico de Fallas.
     Analiza el reporte eléctrico autogenerado y clasifica el tipo de incidencia (Térmica, Eléctrica o Mecánica)
     junto con una breve justificación técnica.
     ```

3. **Paso 3: Crear el resumen ejecutivo paso a paso**
   * Añade un nodo consecutivo en la pantalla y configúralo con el siguiente comando conversacional para resumir el texto técnico:
     ```text
     Actúa como un Ingeniero Documentador.
     Extrae la información principal del análisis anterior y genera un resumen ejecutivo de dos líneas
     enfocado en la acción correctiva inmediata.
     ```

4. **Paso 4: Configurar una regla lógica de desvío (¿Es urgente o rutinario?)**
   * Añade a tu flujo un nodo de decisión llamado **If** (Condicional). Este nodo sirve para evaluar qué tan grave es el asunto usando esta instrucción sencilla para guiar el filtro:
     ```text
     Actúa como un Gestor de Operaciones.
     Establece la regla para que las incidencias críticas sean derivadas al canal prioritario de guardia
     y las moderadas al buzón de mantenimiento rutinario.
     ```

5. **Paso 5: Probar el flujo completo y validar el resultado**
   * Haz clic en el botón superior **Test Workflow** (Probar Flujo) dentro de n8n para ver cómo las piezas trabajan juntas de forma automática. Verifica que todo corra correctamente escribiendo esta instrucción final de validación:
     ```text
     Actúa como un Administrador de Sistemas.
     Simula la ejecución final del flujo en n8n y redacta una breve constancia que confirme
     la recepción, clasificación, resumen y notificación automática de la incidencia.
     ```

## Resultado esperado
Un flujo de trabajo visual totalmente funcional en **n8n**, creado paso a paso en 30 minutos, donde la inteligencia artificial autogenera los datos, clasifica las fallas, crea un resumen gerencial y toma decisiones lógicas para notificar al personal adecuado sin requerir archivos externos ni conocimientos previos de programación.
