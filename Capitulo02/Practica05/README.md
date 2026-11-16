# Práctica 5. Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes construirán un flujo automatizado completo dentro de **n8n** utilizando **exclusivamente prompts en lenguaje natural**, sin programar ni conectar herramientas externas. Mediante el **Asistente de IA integrado de n8n (`Assistant`)**, los asistentes generarán automáticamente la arquitectura de nodos y configurarán instrucciones generativas para que el flujo cree un reporte técnico simulado, clasifique la incidencia, redacte un resumen ejecutivo y genere la notificación final de manera 100% autónoma.

---

## ¿Cómo funciona la creación por prompts en n8n?
En lugar de arrastrar piezas manualmente, utilizaremos la inteligencia artificial nativa de n8n en dos niveles:

1. **Asistente Constructor (`Assistant` en el menú izquierdo):** Lee una instrucción en lenguaje natural y arma automáticamente los nodos y las flechas en el lienzo de trabajo.
2. **Nodos Generativos de Ejecución:** Dentro de los nodos creados, solo escribimos instrucciones de texto (prompts) para que la IA invente los datos de prueba, los analice y redacte la alerta sin requerir bases de datos, archivos ni cuentas de correo reales.

---

## Sección 1: Demostración del Instructor - Tres Pasos

1. **Paso 1: Ordenar al Asistente de n8n que construya el flujo mediante un prompt**
   * Abre un flujo nuevo en n8n (`New Workflow`).
   * En el menú lateral izquierdo, haz clic en **`Assistant`** para abrir el chat constructor de flujos.
   * Pega la siguiente instrucción para que n8n arme toda la estructura por ti:
     ```text
     Construye un flujo de trabajo sencillo con un disparador manual (Manual Trigger) conectado a tres nodos secuenciales de IA (usando Anthropic o Basic LLM Chain).
     El primer nodo debe generar un reporte técnico simulado sobre la falla de una bomba industrial.
     El segundo nodo debe leer ese reporte, clasificar la falla (Mecánica, Eléctrica o Control) y crear un resumen ejecutivo de dos líneas.
     El tercer nodo debe redactar un mensaje formal de alerta listo para notificar al jefe de mantenimiento.
     No conectes aplicaciones externas, todo debe ejecutarse con texto generado por IA.
     ```
   * Acepta o aplica los cambios sugeridos por el asistente para que los nodos aparezcan conectados en tu pantalla.

2. **Paso 2: Verificar y ajustar las instrucciones generativas dentro de los nodos**
   * Haz clic en cada uno de los nodos de IA creados en el lienzo y verifica que sus campos **Prompt** contengan instrucciones claras para operar con datos autogenerados (si falta alguno, pega este comando en el nodo de clasificación):
     ```text
     Actúa como un Especialista en Diagnóstico Industrial.
     Analiza el reporte técnico recibido del nodo anterior, clasifica la incidencia en una categoría operativa
     y redacta un resumen ejecutivo de dos líneas enfocado en la criticidad.
     ```

3. **Paso 3: Ejecutar el flujo autogenerado y validar la salida**
   * Haz clic en el botón negro **`Execute`** en la parte inferior de la pantalla.
   * Observa cómo el flujo se ejecuta paso a paso y abre el último nodo para verificar en el panel **Output** el reporte generado, su clasificación y la notificación redactada.

---

## Sección 2: Práctica Guiada del Participante - Cinco Pasos

1. **Paso 1: Generar la estructura completa del flujo mediante el Asistente de n8n**
   * Crea un nuevo flujo en blanco (`New Workflow`) y abre el panel **`Assistant`** en el menú izquierdo.
   * Envía el siguiente prompt para que n8n diseñe y conecte todos los nodos automáticamente:
     ```text
     Crea un flujo automatizado que inicie con un disparador manual y conecte cuatro nodos de IA en secuencia.
     Nodo 1: Genera un reporte técnico autogenerado sobre una sobrecarga térmica en un tablero eléctrico industrial.
     Nodo 2: Clasifica el tipo de falla eléctrica y justifica técnicamente el diagnóstico.
     Nodo 3: Redacta un resumen ejecutivo de dos líneas con la acción correctiva inmediata.
     Nodo 4: Redacta la notificación final de alerta indicando si debe ir al canal prioritario de guardia o a mantenimiento rutinario.
     Todo debe funcionar exclusivamente con prompts de IA sin servicios externos.
     ```

2. **Paso 2: Refinar el prompt de autogeneración del incidente (Nodo 1)**
   * Haz doble clic en el primer nodo de IA generado en el lienzo, ubica el campo **Prompt** y asegúrate de que tenga esta instrucción exacta para garantizar un caso técnico realista:
     ```text
     Actúa como un Ingeniero de Mantenimiento de Planta.
     Genera de manera completamente autónoma un reporte de incidente detallado sobre una sobrecarga térmica
     en un tablero eléctrico principal de distribución, incluyendo temperatura alcanzada y equipos afectados.
     ```

3. **Paso 3: Refinar el prompt de clasificación y análisis técnico (Nodo 2)**
   * Abre el segundo nodo de IA del flujo y actualiza su campo **Prompt** con el siguiente comando:
     ```text
     Actúa como un Analista de Fallas Eléctricas.
     Lee el reporte autogenerado en el paso anterior, clasifica el tipo exacto de incidencia
     y redacta una breve justificación técnica de por qué ocurrió.
     ```

4. **Paso 4: Refinar el prompt de resumen y enrutamiento de alerta (Nodos 3 y 4)**
   * Abre el último nodo de IA del flujo y asegúrate de que su campo **Prompt** consolide la decisión y la notificación final con esta instrucción:
     ```text
     Actúa como un Coordinador de Operaciones de Ingeniería.
     Toma el análisis anterior, redacta un resumen ejecutivo de dos líneas, determina si la alerta va al canal crítico de guardia
     o al buzón rutinario, y escribe el mensaje formal de notificación listo para enviar al responsable.
     ```

5. **Paso 5: Ejecutar el flujo completo y validar los resultados en n8n**
   * Haz clic en el botón negro **`Execute`** en la parte inferior del lienzo.
   * Verifica que cada nodo se marque en verde al completarse y revisa la pestaña **Output** del nodo final para comprobar que la IA creó el reporte, lo clasificó, lo resumió y redactó la notificación sin requerir datos externos.

## Resultado esperado
Un flujo de automatización funcional en **n8n** creado y operado **100% mediante prompts**, donde el asistente de IA construye la arquitectura visual y los nodos generativos ejecutan de punta a punta la creación del reporte técnico, la clasificación de la falla, el resumen ejecutivo y la notificación operativa.
