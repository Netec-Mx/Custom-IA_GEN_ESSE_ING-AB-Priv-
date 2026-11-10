# Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente

## Metadatos

| Campo | Valor |
|---|---|
| **Duración** | 36 minutos |
| **Complejidad** | Alta |
| **Nivel Bloom** | Crear |

## Descripción General

En este laboratorio construirás un flujo de automatización completo en n8n Community Edition 1.44.1 que recibe un reporte técnico de incidencia, lo envía a un modelo de IA para clasificar el tipo de incidencia y generar un resumen ejecutivo en formato JSON, enruta la respuesta mediante un nodo de decisión que asigna al responsable según la categoría, y envía una notificación automática. Probarás el flujo con tres reportes técnicos ficticios de diferentes categorías para validar su funcionamiento de extremo a extremo. Este laboratorio integra las competencias de diseño de prompts estructurados desarrolladas en los labs 04-00-01 y 04-00-02, y las prácticas de anonimización del lab 03-00-02.

## Objetivos de Aprendizaje

- [ ] Construir un flujo automatizado en n8n que reciba un reporte técnico, utilice un modelo de IA para clasificar el tipo de incidencia, generar un resumen ejecutivo y notificar automáticamente al responsable correspondiente.
- [ ] Configurar en n8n un trigger que reciba un reporte técnico mediante formulario web o entrada manual según el canal disponible.
- [ ] Agregar un nodo de IA con un prompt estructurado (rol, contexto, tarea, formato de salida, restricciones) que clasifique el tipo de incidencia y genere un resumen ejecutivo en formato JSON.
- [ ] Implementar un nodo de decisión que asigne al responsable según la clasificación y envíe la notificación automática por el canal disponible.
- [ ] Validar el funcionamiento del flujo completo probándolo con al menos tres reportes técnicos ficticios de diferentes categorías, incluyendo un caso adverso.

## Prerrequisitos

**Conocimientos previos:**

- Haber completado los labs 03-00-01, 03-00-02, 04-00-01 y 04-00-02.
- Haber revisado los contenidos teóricos del Módulo 5.0 (lecciones 5.1 a 5.4) sobre automatización con IA, n8n, triggers, nodos, acciones e integración de modelos de IA en flujos automatizados.
- Comprender la estructura de prompt de cinco componentes (rol, contexto, tarea, formato de salida, restricciones) del lab 04-00-01.

**Acceso y herramientas:**

- n8n Community Edition 1.44.1 instalado vía Docker Desktop 4.30.0 y accesible en `http://localhost:5678`, **o** acceso a n8n Cloud con periodo de prueba activo en `https://app.n8n.cloud`.
- Docker Desktop 4.30.0 instalado y en ejecución (solo para n8n autoalojado).
- Clave de API de OpenAI con créditos de prueba disponibles ([https://platform.openai.com/api-keys](https://platform.openai.com/api-keys)), **o** clave de API de Google Gemini gratuita obtenida desde Google AI Studio ([https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)), según indicación del instructor. **[VERIFICAR disponibilidad del tier gratuito al momento de impartición]**.
- Tres reportes técnicos ficticios proporcionados en este laboratorio (Paso 4).
- Documento de plantillas de prompts estructurados generado en el lab 04-00-01 como referencia.

## Entorno de Laboratorio

**Infraestructura n8n (autoalojado con Docker):**

| Componente | Valor |
|---|---|
| Contenedor Docker | `n8n` |
| Puerto de acceso | `5678` |
| URL de interfaz | `http://localhost:5678` |
| Volumen de datos | `n8n_data` |
| Directorio de trabajo | `/home/node/.n8n` |
| Nombre del workflow | `Clasificador-Incidencias-v1` |

**Software requerido:**

| Software | Versión | Fuente oficial |
|---|---|---|
| n8n Community Edition | 1.44.1 | [https://docs.n8n.io/hosting/installation/docker/](https://docs.n8n.io/hosting/installation/docker/) |
| Docker Desktop | 4.30.0 | [https://docs.docker.com/desktop/release-notes/](https://docs.docker.com/desktop/release-notes/) |
| Navegador web | Chrome 124.0+ / Firefox 125.0+ / Edge 124.0+ | — |

**Verificación del entorno (solo n8n autoalojado):**

Si n8n aún no está en ejecución, iniciar el contenedor:

```bash
docker start n8n
```

Verificar que el contenedor está activo:

```bash
docker ps --filter "name=n8n" --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
```

Salida esperada:

```
NAMES   STATUS         PORTS
n8n     Up X minutes   0.0.0.0:5678->5678/tcp
```

Si el contenedor no existe, crearlo con el siguiente comando:

```bash
docker run -d --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n:1.44.1
```

Abrir `http://localhost:5678` en el navegador y confirmar que la interfaz de n8n se carga correctamente.

## Instrucciones Paso a Paso

### Paso 1: Crear el workflow y configurar el trigger de entrada

**Objetivo:** Crear el workflow `Clasificador-Incidencias-v1` y agregar un nodo Manual Trigger como punto de entrada del flujo para recibir el texto del reporte técnico.

**Instrucciones:**

1. Abrir n8n en el navegador (`http://localhost:5678` o la URL de n8n Cloud).
2. Hacer clic en **+ Create Workflow** (o **+ Nuevo Workflow**) en la esquina superior derecha.
3. Hacer clic en el nombre del workflow (por defecto "My workflow") en la parte superior y renombrarlo a:

```
Clasificador-Incidencias-v1
```

4. Hacer clic en el botón **+** en el centro del canvas para agregar el primer nodo.
5. En el buscador de nodos, escribir `Manual Trigger` y seleccionar el nodo **Manual Trigger**.
6. El nodo se agregará al canvas. No requiere configuración adicional.

> **Nota para el instructor:** Si se prefiere usar **n8n Form Trigger** en lugar de Manual Trigger, agregar el nodo "n8n Form Trigger" y configurar un campo de texto llamado `reporte_texto` de tipo "Text" con la opción "Multiline" activada. El resto del laboratorio funciona igual sustituyendo la referencia de datos de entrada. Este laboratorio usa Manual Trigger para garantizar compatibilidad con todos los entornos.

**Resultado esperado:** Un workflow vacío llamado `Clasificador-Incidencias-v1` con un nodo Manual Trigger como primer nodo en el canvas.

**Verificación:** El nombre `Clasificador-Incidencias-v1` aparece en la barra superior del editor. El nodo Manual Trigger está visible en el canvas sin errores.

---

### Paso 2: Agregar el nodo Code para inyectar los reportes de prueba

**Objetivo:** Agregar un nodo Code que proporcione el texto del reporte técnico como dato de entrada al flujo, simulando la recepción de un reporte por formulario o correo.

**Instrucciones:**

1. Hacer clic en el **+** que aparece a la derecha del nodo Manual Trigger para agregar un nodo conectado.
2. Buscar `Code` y seleccionar el nodo **Code**.
3. En el panel de configuración del nodo Code, seleccionar **Language: JavaScript** y **Mode: Run Once for All Items**.
4. Borrar el código de ejemplo y pegar el siguiente código que contiene el primer reporte de prueba:

```javascript
return [
  {
    json: {
      reporte_id: "RPT-2024-0471",
      fecha: "2024-11-15",
      area: "Línea de Producción 3",
      reportado_por: "Técnico de turno",
      texto_reporte: "Durante la inspección rutinaria del turno nocturno se detectó una vibración anormal en el motor principal de la banda transportadora BT-307. La vibración medida con acelerómetro portátil registró 8.2 mm/s RMS en dirección radial, superando el umbral de alerta de 7.1 mm/s según ISO 10816-3. Se observó también un incremento de temperatura en el rodamiento lado acople, alcanzando 78°C frente a los 55°C habituales. La banda continuó operando pero se redujo la velocidad al 70% como medida preventiva. Se requiere intervención de mantenimiento mecánico para diagnóstico de rodamientos y alineación del conjunto motor-reductor."
    }
  }
];
```

5. Renombrar el nodo haciendo clic en su nombre y escribiendo:

```
Reporte de Entrada
```

6. Hacer clic en **Back to canvas** para regresar al canvas principal.

**Resultado esperado:** El nodo "Reporte de Entrada" está conectado al Manual Trigger y contiene el código con el primer reporte técnico ficticio de categoría mecánica.

**Verificación:** Hacer clic en el nodo "Reporte de Entrada", luego clic en **Test step**. En el panel de salida debe aparecer un objeto JSON con los campos `reporte_id`, `fecha`, `area`, `reportado_por` y `texto_reporte`.

---

### Paso 3: Configurar las credenciales del modelo de IA

**Objetivo:** Registrar la clave de API del modelo de IA (OpenAI o Google Gemini) en n8n para que el nodo de clasificación pueda consumir el servicio.

**Instrucciones:**

1. En la barra lateral izquierda de n8n, hacer clic en el ícono de **Settings** (engranaje) y luego en **Credentials** (o ir al menú **Credentials** directamente).
2. Hacer clic en **+ Add Credential**.

**Opción A — OpenAI (GPT-4o-mini):**

3a. Buscar `OpenAI` y seleccionar **OpenAI API**.
4a. En el campo **API Key**, pegar la clave de API obtenida de [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys).
5a. Hacer clic en **Test Connection** para verificar que la clave es válida.
6a. Nombrar la credencial:

```
OpenAI-Lab05
```

7a. Hacer clic en **Save**.

**Opción B — Google Gemini (vía nodo HTTP Request):**

3b. Esta opción no requiere una credencial nativa de n8n. La clave de API se incluirá directamente en la URL del nodo HTTP Request en el Paso 4. Obtener la clave gratuita desde [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) y tenerla disponible.

> **Nota:** El instructor debe indicar antes del laboratorio cuál opción utilizar. Este laboratorio documenta ambas rutas. Los pasos siguientes muestran la Opción A como ruta principal y la Opción B como alternativa en cada paso donde difieren.

**Resultado esperado:** La credencial `OpenAI-Lab05` aparece en la lista de credenciales con estado de conexión exitosa (Opción A), o se tiene la clave de API de Gemini lista para usar (Opción B).

**Verificación:** En **Settings → Credentials**, la credencial `OpenAI-Lab05` muestra un indicador verde de conexión válida (Opción A). Para Opción B, verificar que la clave de API tiene al menos 39 caracteres y comienza con `AIza`.

---

### Paso 4: Agregar el nodo de clasificación y resumen con IA

**Objetivo:** Configurar un nodo que envíe el texto del reporte al modelo de IA con un prompt estructurado de cinco componentes para clasificar la incidencia y generar un resumen ejecutivo en formato JSON.

**Instrucciones:**

1. En el canvas, hacer clic en el **+** a la derecha del nodo "Reporte de Entrada".

**Opción A — OpenAI:**

2a. Buscar `OpenAI` y seleccionar el nodo **OpenAI**.
3a. Configurar el nodo con los siguientes parámetros:
   - **Resource:** Message a Model
   - **Operation:** Send a Message (o "Create a Completion" según la versión del nodo)
   - **Credential:** Seleccionar `OpenAI-Lab05`
   - **Model:** `gpt-4o-mini`
   - **Messages** → **System Message** (o campo "System Prompt"): Pegar el siguiente prompt del sistema:

```text
Eres un ingeniero senior de confiabilidad y mantenimiento industrial con 15 años de experiencia en plantas de manufactura. Tu función es clasificar reportes técnicos de incidencias y generar resúmenes ejecutivos precisos.
```

4a. En el campo **User Message** (o "Prompt"), pegar el siguiente prompt estructurado:

```text
CONTEXTO: Recibes reportes técnicos de incidencias de una planta de manufactura. Cada reporte debe ser clasificado y resumido para enrutamiento automático al responsable correspondiente.

TAREA: Analiza el siguiente reporte técnico y realiza estas acciones:
1. Clasifica la incidencia en exactamente UNA de estas categorías: mecanica, electrica, calidad, seguridad.
2. Genera un resumen ejecutivo de máximo 150 palabras.
3. Sugiere el responsable según la categoría:
   - mecanica → Jefe de Mantenimiento Mecánico
   - electrica → Jefe de Mantenimiento Eléctrico
   - calidad → Supervisor de Calidad
   - seguridad → Coordinador de Seguridad Industrial

REPORTE TÉCNICO:
ID: {{ $json.reporte_id }}
Fecha: {{ $json.fecha }}
Área: {{ $json.area }}
Texto: {{ $json.texto_reporte }}

FORMATO DE SALIDA: Responde ÚNICAMENTE con un objeto JSON válido, sin texto adicional, sin bloques de código markdown, con esta estructura exacta:
{
  "categoria": "<mecanica|electrica|calidad|seguridad>",
  "resumen": "<resumen ejecutivo de máximo 150 palabras>",
  "responsable_sugerido": "<nombre del responsable según la categoría>",
  "reporte_id": "{{ $json.reporte_id }}"
}

RESTRICCIONES:
- No inventes información que no esté en el reporte.
- Si el reporte no contiene información suficiente para clasificar, usa la categoría "mecanica" como valor por defecto e indica la limitación en el resumen.
- No incluyas explicaciones fuera del JSON.
```

5a. En la sección **Options** (si está disponible), configurar:
   - **Temperature:** `0.2` (para respuestas más determinísticas)

6a. Renombrar el nodo:

```
Clasificador IA
```

**Opción B — Google Gemini (vía HTTP Request):**

2b. Buscar `HTTP Request` y seleccionar el nodo **HTTP Request**.
3b. Configurar:
   - **Method:** POST
   - **URL:** (reemplazar `TU_API_KEY` con la clave real)

```
https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=TU_API_KEY
```

4b. En **Body** → **Body Content Type:** JSON. En el campo **JSON**, pegar:

```json
{
  "contents": [
    {
      "role": "user",
      "parts": [
        {
          "text": "Eres un ingeniero senior de confiabilidad y mantenimiento industrial con 15 años de experiencia en plantas de manufactura.\n\nCONTEXTO: Recibes reportes técnicos de incidencias de una planta de manufactura.\n\nTAREA: Analiza el siguiente reporte técnico y realiza estas acciones:\n1. Clasifica la incidencia en exactamente UNA de estas categorías: mecanica, electrica, calidad, seguridad.\n2. Genera un resumen ejecutivo de máximo 150 palabras.\n3. Sugiere el responsable según la categoría:\n   - mecanica → Jefe de Mantenimiento Mecánico\n   - electrica → Jefe de Mantenimiento Eléctrico\n   - calidad → Supervisor de Calidad\n   - seguridad → Coordinador de Seguridad Industrial\n\nREPORTE TÉCNICO:\nID: {{ $json.reporte_id }}\nFecha: {{ $json.fecha }}\nÁrea: {{ $json.area }}\nTexto: {{ $json.texto_reporte }}\n\nFORMATO DE SALIDA: Responde ÚNICAMENTE con un objeto JSON válido, sin texto adicional, sin bloques de código markdown, con esta estructura exacta:\n{\"categoria\": \"<mecanica|electrica|calidad|seguridad>\", \"resumen\": \"<resumen ejecutivo de máximo 150 palabras>\", \"responsable_sugerido\": \"<nombre del responsable según la categoría>\", \"reporte_id\": \"{{ $json.reporte_id }}\"}\n\nRESTRICCIONES:\n- No inventes información que no esté en el reporte.\n- Si el reporte no contiene información suficiente para clasificar, usa la categoría 'mecanica' como valor por defecto e indica la limitación en el resumen.\n- No incluyas explicaciones fuera del JSON."
        }
      ]
    }
  ],
  "generationConfig": {
    "temperature": 0.2
  }
}
```

5b. En **Headers**, agregar:
   - **Name:** `Content-Type` **Value:** `application/json`

6b. Renombrar el nodo:

```
Clasificador IA
```

**Resultado esperado:** El nodo "Clasificador IA" está conectado al nodo "Reporte de Entrada" y configurado con el prompt estructurado de cinco componentes y el modelo de IA seleccionado.

**Verificación:** Hacer clic en el nodo "Clasificador IA" y ejecutar **Test step**. La salida debe contener una respuesta del modelo de IA con un JSON que incluya los campos `categoria`, `resumen`, `responsable_sugerido` y `reporte_id`. Para Opción A, el JSON estará en el campo de respuesta del nodo OpenAI. Para Opción B, el JSON estará dentro de `candidates[0].content.parts[0].text` de la respuesta HTTP.

---

### Paso 5: Agregar el nodo de extracción y parseo del JSON

**Objetivo:** Extraer y parsear la respuesta del modelo de IA para obtener los campos `categoria`, `resumen`, `responsable_sugerido` y `reporte_id` como datos estructurados utilizables por los nodos siguientes.

**Instrucciones:**

1. Hacer clic en el **+** a la derecha del nodo "Clasificador IA" y agregar un nodo **Code**.
2. Seleccionar **Language: JavaScript** y **Mode: Run Once for All Items**.
3. Pegar el siguiente código:

**Opción A — OpenAI:**

```javascript
const items = $input.all();
const results = [];

for (const item of items) {
  // El nodo OpenAI devuelve la respuesta en el campo 'text' o 'content'
  let respuestaTexto = item.json.message?.content || item.json.text || JSON.stringify(item.json);
  
  // Limpiar posibles bloques de código markdown
  respuestaTexto = respuestaTexto.replace(/```json\n?/g, '').replace(/```\n?/g, '').trim();
  
  try {
    const datos = JSON.parse(respuestaTexto);
    results.push({ json: datos });
  } catch (e) {
    results.push({
      json: {
        categoria: "mecanica",
        resumen: "Error al parsear la respuesta del modelo. Respuesta original: " + respuestaTexto.substring(0, 200),
        responsable_sugerido: "Jefe de Mantenimiento Mecánico",
        reporte_id: "PARSE_ERROR",
        error_parseo: true
      }
    });
  }
}

return results;
```

**Opción B — Google Gemini:**

```javascript
const items = $input.all();
const results = [];

for (const item of items) {
  let respuestaTexto = item.json.candidates?.[0]?.content?.parts?.[0]?.text || '';
  
  // Limpiar posibles bloques de código markdown
  respuestaTexto = respuestaTexto.replace(/```json\n?/g, '').replace(/```\n?/g, '').trim();
  
  try {
    const datos = JSON.parse(respuestaTexto);
    results.push({ json: datos });
  } catch (e) {
    results.push({
      json: {
        categoria: "mecanica",
        resumen: "Error al parsear la respuesta del modelo. Respuesta original: " + respuestaTexto.substring(0, 200),
        responsable_sugerido: "Jefe de Mantenimiento Mecánico",
        reporte_id: "PARSE_ERROR",
        error_parseo: true
      }
    });
  }
}

return results;
```

4. Renombrar el nodo:

```
Parsear Respuesta IA
```

**Resultado esperado:** El nodo extrae el JSON de la respuesta del modelo y lo convierte en campos estructurados accesibles por los nodos siguientes.

**Verificación:** Ejecutar **Test step** en el nodo. La salida debe mostrar un objeto JSON con exactamente los campos: `categoria` (valor: `mecanica`), `resumen` (texto coherente), `responsable_sugerido` (valor: `Jefe de Mantenimiento Mecánico`) y `reporte_id` (valor: `RPT-2024-0471`). Si aparece el campo `error_parseo: true`, revisar la respuesta cruda del modelo en el paso anterior.

---

### Paso 6: Agregar el nodo Switch para enrutar por categoría

**Objetivo:** Implementar un nodo de decisión que evalúe el campo `categoria` del JSON y dirija el flujo hacia la rama correspondiente a cada tipo de incidencia.

**Instrucciones:**

1. Hacer clic en el **+** a la derecha del nodo "Parsear Respuesta IA" y agregar un nodo **Switch**.
2. Configurar el nodo Switch con los siguientes parámetros:
   - **Mode:** Rules
   - **Data Type:** String
   - **Value 1** (campo a evaluar): Hacer clic en el campo y seleccionar la expresión:

```
{{ $json.categoria }}
```

3. Agregar cuatro reglas (rules) haciendo clic en **Add Rule** para cada una:

   - **Rule 0 (Output 0):** Operation: `Equal`, Value: `mecanica`
   - **Rule 1 (Output 1):** Operation: `Equal`, Value: `electrica`
   - **Rule 2 (Output 2):** Operation: `Equal`, Value: `calidad`
   - **Rule 3 (Output 3):** Operation: `Equal`, Value: `seguridad`

4. Activar la opción **Fallback Output** (o "Send data to all matching outputs" → desactivado, y "Always Output Data" si está disponible) para que los reportes que no coincidan con ninguna regla se envíen a una salida por defecto.

5. Renombrar el nodo:

```
Enrutar por Categoría
```

**Resultado esperado:** El nodo Switch tiene cuatro salidas etiquetadas (mecanica, electrica, calidad, seguridad) más una salida fallback, y evalúa el campo `categoria` del JSON de entrada.

**Verificación:** Ejecutar **Test step**. Con el reporte de prueba mecánico del Paso 2, los datos deben salir por **Output 0** (mecanica). Verificar que las demás salidas muestran 0 items.

---

### Paso 7: Agregar los nodos de notificación para cada rama

**Objetivo:** Configurar un nodo de notificación en cada salida del Switch que envíe el resumen ejecutivo, la categoría y el responsable asignado por el canal disponible.

> **Nota del instructor:** Este paso utiliza nodos **Write Binary File** (escritura en archivo) como canal de notificación universal. Si los participantes tienen acceso a Gmail, Slack o Telegram, el instructor puede sustituir estos nodos por el canal correspondiente, manteniendo el mismo contenido del mensaje.

**Instrucciones:**

1. Hacer clic en la **salida 0** (mecanica) del nodo "Enrutar por Categoría" y agregar un nodo **Code**.
2. Configurar el nodo Code con **Language: JavaScript**, **Mode: Run Once for All Items** y el siguiente código:

```javascript
const item = $input.first().json;
const mensaje = `
========================================
NOTIFICACIÓN AUTOMÁTICA DE INCIDENCIA
========================================
Reporte ID: ${item.reporte_id}
Categoría: ${item.categoria.toUpperCase()}
Responsable: ${item.responsable_sugerido}
----------------------------------------
RESUMEN EJECUTIVO:
${item.resumen}
========================================
Generado automáticamente por Clasificador-Incidencias-v1
Fecha de procesamiento: ${new Date().toISOString()}
`;

return [{ json: { mensaje, ...item } }];
```

3. Renombrar este nodo:

```
Notificación Mecánica
```

4. Repetir los sub-pasos 1–3 para las salidas 1, 2 y 3 del Switch, creando nodos idénticos con los siguientes nombres:
   - Salida 1 → `Notificación Eléctrica`
   - Salida 2 → `Notificación Calidad`
   - Salida 3 → `Notificación Seguridad`

> **Simplificación:** El código es idéntico para las cuatro ramas porque el campo `responsable_sugerido` ya viene asignado por el modelo de IA. Si se desea sobreescribir el responsable de forma determinística (sin depender del modelo), agregar una línea como `item.responsable_sugerido = "Jefe de Mantenimiento Mecánico";` antes de construir el mensaje en cada rama.

5. Para la **salida Fallback** del Switch, agregar un nodo Code con el mismo código pero renombrarlo:

```
Notificación No Clasificada
```

**Resultado esperado:** Cinco nodos de notificación (uno por cada categoría más el fallback) conectados a las salidas del nodo Switch, cada uno generando un mensaje de notificación formateado.

**Verificación:** Ejecutar el flujo completo haciendo clic en **Test Workflow** (botón en la parte inferior del canvas). El reporte mecánico del Paso 2 debe fluir desde Manual Trigger → Reporte de Entrada → Clasificador IA → Parsear Respuesta IA → Enrutar por Categoría (Output 0) → Notificación Mecánica. Verificar que el campo `mensaje` del nodo final contiene el resumen, la categoría "MECANICA" y el responsable "Jefe de Mantenimiento Mecánico".

---

### Paso 8: Primera prueba completa — Reporte mecánico

**Objetivo:** Ejecutar el flujo de extremo a extremo con el primer reporte de prueba (mecánico) y documentar el resultado.

**Instrucciones:**

1. Asegurarse de que el nodo "Reporte de Entrada" contiene el código del reporte mecánico del Paso 2 (RPT-2024-0471).
2. Hacer clic en **Test Workflow** en la barra inferior del canvas.
3. Esperar a que todos los nodos muestren un indicador verde (✓) de ejecución exitosa.
4. Hacer clic en el último nodo ejecutado ("Notificación Mecánica") y revisar la salida.
5. Registrar los resultados en la siguiente tabla (copiar en un archivo de texto o en la hoja de cálculo):

```
| Reporte ID     | Categoría Esperada | Categoría Obtenida | Responsable Asignado               | ¿Correcto? |
|----------------|--------------------|--------------------|-------------------------------------|------------|
| RPT-2024-0471  | mecanica           |                    |                                     |            |
```

6. Completar los campos vacíos con los valores obtenidos de la ejecución.

**Resultado esperado:** El flujo se ejecuta sin errores. La categoría obtenida es `mecanica`. El responsable asignado es `Jefe de Mantenimiento Mecánico`. La columna "¿Correcto?" se marca como "Sí".

**Verificación:** Todos los nodos muestran indicador verde. El campo `categoria` en la salida del nodo "Parsear Respuesta IA" es exactamente `mecanica` (en minúsculas, sin acentos).

---

### Paso 9: Segunda prueba — Reporte eléctrico

**Objetivo:** Probar el flujo con un segundo reporte ficticio de categoría eléctrica para validar que el Switch enruta correctamente.

**Instrucciones:**

1. Hacer doble clic en el nodo "Reporte de Entrada" para editarlo.
2. Reemplazar el contenido del código por el siguiente reporte eléctrico:

```javascript
return [
  {
    json: {
      reporte_id: "RPT-2024-0472",
      fecha: "2024-11-16",
      area: "Subestación Eléctrica SE-02",
      reportado_por: "Electricista de guardia",
      texto_reporte: "Se registró una caída de tensión intermitente en el bus de 480V de la subestación SE-02 que alimenta los variadores de frecuencia de las bombas de proceso P-201 a P-204. El registrador de eventos del relé de protección SEL-751 muestra tres eventos de subtensión (< 456V) en las últimas 6 horas, con duración promedio de 2.3 segundos cada uno. La termografía infrarroja del interruptor principal reveló un punto caliente de 89°C en la conexión del cable de fase B, cuando la temperatura de las fases A y C es de 52°C. Se sospecha de una conexión floja o deteriorada. Se requiere intervención urgente del equipo eléctrico para retorque de conexiones y posible reemplazo del terminal de fase B."
    }
  }
];
```

3. Hacer clic en **Back to canvas** y ejecutar **Test Workflow**.
4. Verificar que el flujo se enruta por **Output 1** (electrica) del Switch.
5. Registrar en la tabla de resultados:

```
| RPT-2024-0472  | electrica          |                    |                                     |            |
```

**Resultado esperado:** Categoría obtenida: `electrica`. Responsable: `Jefe de Mantenimiento Eléctrico`. El flujo llega al nodo "Notificación Eléctrica".

**Verificación:** El nodo "Notificación Eléctrica" muestra indicador verde y su salida contiene `categoria: electrica` en el mensaje.

---

### Paso 10: Tercera prueba — Reporte de seguridad

**Objetivo:** Probar el flujo con un tercer reporte ficticio de categoría de seguridad para completar la validación mínima de tres categorías.

**Instrucciones:**

1. Editar el nodo "Reporte de Entrada" y reemplazar el código por:

```javascript
return [
  {
    json: {
      reporte_id: "RPT-2024-0473",
      fecha: "2024-11-17",
      area: "Almacén de Químicos AQ-01",
      reportado_por: "Supervisor de turno",
      texto_reporte: "Durante la ronda de seguridad de las 06:00 se detectó una fuga menor en el contenedor de ácido sulfúrico diluido al 15% (tanque IBC-0892) ubicado en el rack 3 del almacén de químicos AQ-01. La fuga se origina en la válvula de drenaje inferior del IBC, que presenta desgaste visible en el sello. Se estima un derrame de aproximadamente 2 litros sobre la charola de contención secundaria. El área fue acordonada, se colocó material absorbente y se notificó verbalmente al coordinador de seguridad. No se reportan personas expuestas ni lesiones. Se requiere la presencia del equipo de seguridad industrial para evaluación del riesgo, gestión del residuo y verificación del estado de los contenedores adyacentes según el procedimiento PSST-012 de manejo de derrames."
    }
  }
];
```

2. Ejecutar **Test Workflow**.
3. Verificar que el flujo se enruta por **Output 3** (seguridad).
4. Registrar en la tabla de resultados:

```
| RPT-2024-0473  | seguridad          |                    |                                     |            |
```

**Resultado esperado:** Categoría obtenida: `seguridad`. Responsable: `Coordinador de Seguridad Industrial`. El flujo llega al nodo "Notificación Seguridad".

**Verificación:** El nodo "Notificación Seguridad" muestra indicador verde. El resumen ejecutivo menciona la fuga de ácido sulfúrico sin inventar información adicional.

---

### Paso 11: Prueba adversa — Reporte ambiguo con información insuficiente

**Objetivo:** Validar el comportamiento del flujo ante un reporte que contiene información insuficiente o ambigua para clasificar, verificando que el modelo aplica las restricciones del prompt y que el flujo no se interrumpe.

**Instrucciones:**

1. Editar el nodo "Reporte de Entrada" y reemplazar el código por:

```javascript
return [
  {
    json: {
      reporte_id: "RPT-2024-0474",
      fecha: "2024-11-18",
      area: "Zona general de planta",
      reportado_por: "Operador",
      texto_reporte: "Hay un problema en la planta. Algo no funciona bien desde ayer. Necesitamos que alguien venga a revisar."
    }
  }
];
```

2. Ejecutar **Test Workflow**.
3. Observar por cuál salida del Switch se enruta el flujo.
4. Revisar el campo `resumen` en la salida del nodo "Parsear Respuesta IA" y verificar si el modelo indicó la limitación de información.
5. Registrar en la tabla de resultados:

```
| RPT-2024-0474  | (ambiguo)          |                    |                                     |            |
```

> **Importante:** Este es un caso adverso deliberado. El modelo de IA puede clasificarlo como `mecanica` (valor por defecto según las restricciones del prompt) o asignar otra categoría con baja confianza. Lo relevante es que: (a) el flujo no se interrumpe, (b) el JSON se parsea correctamente, y (c) el resumen reconoce la falta de información. Si el modelo clasifica con confianza una categoría específica a partir de un reporte vago, esto ilustra una limitación de la IA: **tendencia a generar respuestas aparentemente seguras incluso con información insuficiente**. Anotar esta observación.

**Resultado esperado:** El flujo se ejecuta sin errores. El modelo genera un JSON válido. El resumen idealmente indica que la información es insuficiente para una clasificación precisa.

**Verificación:** Ningún nodo muestra error (indicador rojo). El campo `categoria` contiene uno de los cuatro valores válidos. Documentar si el modelo reconoció la ambigüedad o si clasificó con aparente certeza — ambos resultados son pedagógicamente valiosos.

---

### Paso 12: Guardar el workflow y documentar resultados

**Objetivo:** Guardar el workflow completo y consolidar la tabla de resultados de las cuatro pruebas realizadas.

**Instrucciones:**

1. Presionar **Ctrl+S** (o **Cmd+S** en Mac) para guardar el workflow.
2. Verificar que el nombre `Clasificador-Incidencias-v1` aparece en la barra superior.
3. Consolidar la tabla de resultados completa:

```
| Reporte ID     | Categoría Esperada | Categoría Obtenida | Responsable Asignado                    | ¿Correcto? |
|----------------|--------------------|--------------------|------------------------------------------|------------|
| RPT-2024-0471  | mecanica           | [completar]        | [completar]                              | [Sí/No]    |
| RPT-2024-0472  | electrica          | [completar]        | [completar]                              | [Sí/No]    |
| RPT-2024-0473  | seguridad          | [completar]        | [completar]                              | [Sí/No]    |
| RPT-2024-0474  | (ambiguo)          | [completar]        | [completar]                              | [N/A]      |
```

4. Si alguna de las tres primeras pruebas fue clasificada incorrectamente, regresar al nodo "Clasificador IA" y ajustar el prompt. Posibles ajustes:
   - Agregar ejemplos de cada categoría en el prompt (few-shot).
   - Reforzar la instrucción de clasificación con palabras clave por categoría.
   - Reducir la temperatura a `0.1`.

5. Después de cualquier ajuste, re-ejecutar la prueba fallida para confirmar la corrección.

**Resultado esperado:** El workflow está guardado. La tabla muestra al menos 3 de 3 clasificaciones correctas en los reportes con categoría definida. El caso adverso está documentado con observaciones.

**Verificación:** El workflow aparece en la lista de workflows de n8n con el nombre `Clasificador-Incidencias-v1`. La tabla de resultados tiene las cuatro filas completadas.

---

### Paso 13: Revisión de la arquitectura del flujo completo

**Objetivo:** Verificar visualmente que el flujo completo tiene la estructura correcta y reflexionar sobre los componentes de automatización implementados.

**Instrucciones:**

1. En el canvas de n8n, hacer zoom para ver todos los nodos del flujo. La estructura debe ser:

```
Manual Trigger → Reporte de Entrada → Clasificador IA → Parsear Respuesta IA → Enrutar por Categoría
                                                                                    ├─→ Notificación Mecánica
                                                                                    ├─→ Notificación Eléctrica
                                                                                    ├─→ Notificación Calidad
                                                                                    ├─→ Notificación Seguridad
                                                                                    └─→ Notificación No Clasificada
```

2. Verificar que el flujo tiene exactamente **9 nodos** conectados (1 trigger + 1 entrada + 1 IA + 1 parseo + 1 switch + 5 notificaciones).
3. Identificar en el flujo los componentes aprendidos en la lección 5.1:
   - **Trigger (disparador):** Manual Trigger — inicia el flujo.
   - **Nodo de procesamiento con IA:** Clasificador IA — el modelo actúa como nodo dentro del pipeline.
   - **Nodo de decisión:** Switch — enruta según la categoría.
   - **Nodo de acción:** Notificaciones — ejecutan la acción final.

4. Reflexionar: este flujo es un ejemplo de **automatización mediante IA** (no asistencia), porque una vez diseñado, cada ejecución procesa el reporte sin intervención humana. Si se sustituyera el Manual Trigger por un Email Trigger o un Webhook, el flujo operaría de forma completamente autónoma.

**Resultado esperado:** El participante identifica visualmente los 9 nodos del flujo y relaciona cada componente con los conceptos teóricos de trigger, nodo de IA, nodo de decisión y nodo de acción.

**Verificación:** El canvas muestra todos los nodos conectados sin errores (sin indicadores rojos). El participante puede nombrar los cuatro tipos de componentes del flujo y su función.

## Validación y Pruebas

Para considerar el laboratorio completado exitosamente, verificar los siguientes criterios medibles:

| # | Criterio | Evidencia requerida | ¿Cumple? |
|---|---|---|---|
| 1 | El workflow `Clasificador-Incidencias-v1` existe y está guardado en n8n | El workflow aparece en la lista de workflows | [ ] |
| 2 | El flujo tiene 9 nodos conectados en la estructura correcta | Captura del canvas o inspección visual | [ ] |
| 3 | El prompt del nodo de IA contiene los cinco componentes (rol, contexto, tarea, formato de salida, restricciones) | Inspeccionar el contenido del nodo "Clasificador IA" | [ ] |
| 4 | El reporte mecánico (RPT-2024-0471) fue clasificado como `mecanica` | Tabla de resultados, fila 1 | [ ] |
| 5 | El reporte eléctrico (RPT-2024-0472) fue clasificado como `electrica` | Tabla de resultados, fila 2 | [ ] |
| 6 | El reporte de seguridad (RPT-2024-0473) fue clasificado como `seguridad` | Tabla de resultados, fila 3 | [ ] |
| 7 | El caso adverso (RPT-2024-0474) no interrumpió el flujo y se documentó el comportamiento | Tabla de resultados, fila 4 con observaciones | [ ] |
| 8 | Cada nodo de notificación genera un mensaje con categoría, resumen y responsable | Salida del nodo de notificación ejecutado | [ ] |
| 9 | El nodo Switch enruta correctamente a diferentes salidas según la categoría | Al menos 2 salidas diferentes activadas en las pruebas | [ ] |

**Criterio de aprobación:** Mínimo 8 de 9 criterios cumplidos. El criterio 7 (caso adverso) se evalúa por la documentación del comportamiento observado, no por la corrección de la clasificación.

> **Limitación de IA reconocida:** El modelo puede clasificar incorrectamente un reporte en ejecuciones futuras, especialmente con reportes ambiguos o que mezclan categorías. Un flujo de producción requeriría: (a) validación humana periódica de las clasificaciones, (b) un umbral de confianza para escalar casos dudosos, y (c) un conjunto de prueba más amplio. Los resultados de este laboratorio con cuatro reportes son insuficientes para declarar el flujo como apto para producción.

## Solución de Problemas

### Problema 1: El nodo "Parsear Respuesta IA" muestra `error_parseo: true`

**Síntoma:** Al ejecutar el flujo, el nodo "Parsear Respuesta IA" devuelve un JSON con el campo `error_parseo: true` y un mensaje que incluye texto no-JSON del modelo.

**Causa:** El modelo de IA devolvió la respuesta envuelta en bloques de código markdown (`` ```json ... ``` ``) o incluyó texto explicativo antes o después del JSON, a pesar de la instrucción en el prompt. Esto es un comportamiento conocido, especialmente con modelos Gemini y en algunos casos con GPT-4o-mini cuando la temperatura es alta.

**Solución:**

1. Verificar la salida cruda del nodo "Clasificador IA" haciendo clic en él y revisando el contenido de la respuesta.
2. Si la respuesta contiene bloques markdown, el código de parseo ya los limpia. Si contiene otro formato inesperado, agregar una línea de limpieza adicional en el nodo "Parsear Respuesta IA":

```javascript
// Agregar después de la línea de limpieza de markdown existente:
respuestaTexto = respuestaTexto.replace(/^[^{]*/, '').replace(/[^}]*$/, '');
```

3. Si el problema persiste, agregar al final del prompt del nodo de IA la siguiente línea reforzada:

```text
IMPORTANTE: Tu respuesta debe comenzar con { y terminar con }. No incluyas ningún otro texto.
```

4. Re-ejecutar **Test Workflow** y verificar que el parseo es exitoso.

---

### Problema 2: El nodo "Clasificador IA" muestra error 429 (Rate Limit) o 401 (Unauthorized)

**Síntoma:** Al ejecutar el flujo, el nodo "Clasificador IA" muestra un error HTTP 429 ("Too Many Requests") o 401 ("Unauthorized / Invalid API Key").

**Causa:** Para el error 429: se agotaron los créditos gratuitos de la API o se excedió el límite de solicitudes por minuto del tier gratuito. Para el error 401: la clave de API es inválida, expiró o no fue copiada correctamente.

**Solución:**

Para error **401**:
1. Ir a **Settings → Credentials** en n8n.
2. Editar la credencial `OpenAI-Lab05` (o verificar la clave en la URL de Gemini).
3. Verificar que la clave de API está completa (sin espacios al inicio o final).
4. Hacer clic en **Test Connection**. Si falla, generar una nueva clave desde la plataforma correspondiente.

Para error **429**:
1. Esperar 60 segundos y re-ejecutar el flujo (los límites por minuto se reinician).
2. Si el error persiste, verificar el consumo en el dashboard de la plataforma de IA:
   - OpenAI: [https://platform.openai.com/usage](https://platform.openai.com/usage)
   - Google AI Studio: [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
3. Si los créditos gratuitos se agotaron, el instructor puede: (a) proporcionar una clave alternativa, (b) cambiar al modelo alternativo (Gemini si se usaba OpenAI, o viceversa), o (c) compartir pantalla para demostrar las pruebas restantes.

## Limpieza

Después de completar el laboratorio, realizar las siguientes acciones:

1. **Conservar el workflow:** No eliminar `Clasificador-Incidencias-v1` — podrá ser referenciado en actividades posteriores del curso.

2. **Proteger la clave de API:** Si se usó la Opción B (Gemini vía HTTP Request), la clave de API está visible en la URL del nodo. Para protegerla:
   - Ir al nodo "Clasificador IA", copiar la clave y reemplazarla en la URL por el texto `TU_API_KEY`.
   - Almacenar la clave en un gestor de contraseñas o archivo seguro fuera de n8n.

3. **Restaurar el reporte de prueba original:** Editar el nodo "Reporte de Entrada" y restaurar el código del reporte mecánico (RPT-2024-0471) del Paso 2, para que el workflow quede en un estado funcional de referencia.

4. **No detener Docker ni n8n** si se van a realizar actividades adicionales del curso. Si es la última actividad de la sesión:

```bash
docker stop n8n
```

Para reiniciar en la siguiente sesión:

```bash
docker start n8n
```

## Resumen

En este laboratorio construiste un flujo de automatización completo en n8n que implementa los cuatro componentes fundamentales de un pipeline automatizado con IA:

- **Trigger:** Punto de entrada que inicia el flujo (Manual Trigger, sustituible por Email Trigger o Webhook para operación autónoma).
- **Nodo de IA:** Modelo de lenguaje (GPT-4o-mini o Gemini 1.5 Flash) que clasifica incidencias y genera resúmenes ejecutivos mediante un prompt estructurado de cinco componentes.
- **Nodo de decisión:** Switch que enruta el flujo según la categoría de incidencia, asignando al responsable correspondiente.
- **Nodo de acción:** Notificaciones que entregan el resumen y la asignación al destinatario correcto.

La prueba adversa con un reporte ambiguo demostró una limitación importante de la IA en flujos automatizados: los modelos pueden generar clasificaciones aparentemente seguras incluso con información insuficiente. En un entorno de producción, esto requiere supervisión humana periódica, umbrales de confianza y conjuntos de prueba significativamente más amplios.

**Conexión con las lecciones del módulo:**

- **Lección 5.1:** Distinguiste en la práctica la diferencia entre asistencia (labs 03 y 04, donde tú conducías la interacción) y automatización (este lab, donde el flujo opera sin intervención por ejecución).
- **Lección 5.2:** Identificaste que la clasificación de incidencias es un proceso repetitivo, estructurado y de alto volumen — candidato ideal para automatización.
- **Lección 5.3–5.4:** Aplicaste los componentes de n8n (triggers, nodos, acciones) e integraste un modelo de IA como nodo dentro del pipeline.

**Recursos adicionales:**

- Documentación oficial de n8n: [https://docs.n8n.io/](https://docs.n8n.io/)
- Nodo OpenAI en n8n: [https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.openai/](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.openai/)
- Nodo Switch en n8n: [https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.switch/](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.switch/)
- API de Google Gemini: [https://ai.google.dev/gemini-api/docs](https://ai.google.dev/gemini-api/docs)
- Guía de prompt engineering de OpenAI: [https://platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)

---

# Práctica: Diseñar un flujo automatizado que procese un archivo con indicadores de operación, identifique desviaciones mediante IA y genere automáticamente un reporte técnico para apoyar el monitoreo y control del proceso.

## Metadatos

| Campo | Valor |
|---|---|
| **Duración** | 36 minutos |
| **Complejidad** | Alta |
| **Nivel de Bloom** | Crear |

## Descripción General

En este laboratorio el participante diseñará de principio a fin un flujo automatizado en n8n Community Edition 1.45.1 que lee un archivo CSV con indicadores de operación ficticios, compara cada valor contra su meta para detectar desviaciones, envía las desviaciones a un modelo de IA generativa mediante API para obtener un análisis de causas y recomendaciones, y almacena el reporte técnico resultante como archivo de texto. El ejercicio integra los conceptos de automatización versus asistencia, identificación de procesos automatizables, componentes de un flujo (Trigger → Nodos de procesamiento → Nodo de IA → Salida) y prompt engineering aplicado a operaciones industriales, todo dentro de un entorno sin costo.

## Objetivos de Aprendizaje

- [ ] Crear un archivo CSV con indicadores de operación ficticios que incluya deliberadamente desviaciones respecto a metas definidas.
- [ ] Diseñar un flujo completo en n8n con Trigger manual, lectura de archivo, lógica de comparación, nodo de IA y nodo de salida.
- [ ] Configurar un nodo de IA dentro de n8n conectado a un modelo con acceso gratuito (Groq Llama 3 u OpenAI) para interpretar desviaciones y generar recomendaciones técnicas.
- [ ] Generar un reporte técnico estructurado como resultado del flujo automatizado y almacenarlo como archivo en disco local.
- [ ] Validar el flujo completo ejecutándolo y verificando que el reporte contenga las desviaciones detectadas con causas y recomendaciones.

## Prerrequisitos

**Conocimientos previos:**

- Haber completado el Lab 05-00-01 (Clasificador-Incidencias-v1) y comprender la navegación básica en n8n (canvas, nodos, credenciales).
- Conceptos de la lección 5.1: diferencia entre asistencia y automatización mediante IA, componentes de un flujo (Trigger, nodos, acciones).
- Uso básico de un editor de texto o hoja de cálculo para crear archivos CSV.

**Acceso y entorno:**

- n8n Community Edition ejecutándose en Docker Desktop 4.30.0 y accesible en `http://localhost:5678` (contenedor `n8n` con volumen `n8n_data`, configurado en el Lab 05-00-01).
- Cuenta gratuita activa con API key en **al menos uno** de los siguientes proveedores:
  - **Opción A — Groq** (recomendada por su generosidad en el tier gratuito): [https://console.groq.com](https://console.groq.com) — modelo `llama-3-8b-8192`.
  - **Opción B — OpenAI**: [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys) — modelo `gpt-4o-mini` (requiere créditos de prueba activos).
- Credencial `OpenAI-Lab05` ya configurada en n8n (Lab 05-00-01, Opción A) **o** API key de Groq disponible para registrar en este laboratorio.

> **Nota para el instructor:** Este laboratorio documenta la **Opción A (Groq)** como ruta principal por su disponibilidad gratuita sin créditos limitados. La **Opción B (OpenAI)** se indica como alternativa en los pasos donde difieren. Si el instructor ya comunicó un proveedor específico, seguir esa indicación.

## Entorno de Laboratorio

| Componente | Detalle |
|---|---|
| **Contenedor Docker** | `n8n` (ya existente del Lab 05-00-01) |
| **Puerto de acceso** | `5678` → `http://localhost:5678` |
| **Volumen de datos** | `n8n_data` → `/home/node/.n8n` |
| **n8n Community Edition** | 1.45.1 ([https://docs.n8n.io/](https://docs.n8n.io/)) |
| **Docker Desktop** | 4.30.0 ([https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)) |
| **Modelo IA (Opción A)** | Groq — Llama 3 8B (`llama-3-8b-8192`) ([https://console.groq.com/docs/models](https://console.groq.com/docs/models)) |
| **Modelo IA (Opción B)** | OpenAI — GPT-4o-mini ([https://platform.openai.com/docs/models](https://platform.openai.com/docs/models)) |
| **Nombre del workflow** | `Monitor-Indicadores-v1` |
| **Directorio de trabajo CSV** | `/home/node/.n8n/` (dentro del contenedor) |

**Verificación rápida del entorno:**

```bash
docker ps --filter "name=n8n" --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
```

Salida esperada:

```
NAMES   STATUS         PORTS
n8n     Up X minutes   0.0.0.0:5678->5678/tcp
```

Si el contenedor no está activo:

```bash
docker start n8n
```

## Instrucciones Paso a Paso

---

### Paso 1: Crear el archivo CSV con indicadores de operación ficticios

**Objetivo:** Preparar el archivo de datos de entrada con indicadores industriales que incluyan desviaciones deliberadas respecto a las metas, para que el flujo tenga datos significativos que procesar.

**Instrucciones:**

1. Abrir un editor de texto plano (Bloc de notas, VS Code, nano) o una hoja de cálculo.
2. Crear un archivo con el siguiente contenido exacto (copiar y pegar):

```csv
indicador,valor_actual,meta,unidad,turno,tipo_comparacion
Disponibilidad,78.5,90.0,%,Turno 1,mayor_o_igual
Rendimiento,92.3,85.0,%,Turno 1,mayor_o_igual
Scrap,6.8,3.0,%,Turno 1,menor_o_igual
Tiempo_Paro,47,30,min,Turno 2,menor_o_igual
Disponibilidad,91.2,90.0,%,Turno 2,mayor_o_igual
Rendimiento,80.1,85.0,%,Turno 2,mayor_o_igual
Scrap,2.1,3.0,%,Turno 2,menor_o_igual
Tiempo_Paro,28,30,min,Turno 3,menor_o_igual
Disponibilidad,65.0,90.0,%,Turno 3,mayor_o_igual
OEE,58.4,75.0,%,Turno 3,mayor_o_igual
```

3. Guardar el archivo con el nombre `indicadores_operacion.csv` en una ubicación accesible (por ejemplo, el Escritorio).
4. Copiar el archivo al contenedor de n8n para que los nodos de lectura puedan acceder a él:

```bash
docker cp indicadores_operacion.csv n8n:/home/node/.n8n/indicadores_operacion.csv
```

5. Verificar que el archivo se copió correctamente:

```bash
docker exec n8n cat /home/node/.n8n/indicadores_operacion.csv
```

**Resultado esperado:** El contenido del CSV se muestra en la terminal con las 10 filas de indicadores (más la fila de encabezado), incluyendo deliberadamente 5 indicadores con desviación (Disponibilidad T1: 78.5 vs 90, Scrap T1: 6.8 vs 3.0, Tiempo_Paro T2: 47 vs 30, Rendimiento T2: 80.1 vs 85, Disponibilidad T3: 65.0 vs 90, OEE T3: 58.4 vs 75) y 4 indicadores dentro de meta.

**Verificación:** Contar las líneas del archivo — deben ser 11 (1 encabezado + 10 registros):

```bash
docker exec n8n wc -l /home/node/.n8n/indicadores_operacion.csv
```

Salida esperada: `11 /home/node/.n8n/indicadores_operacion.csv`

---

### Paso 2: Crear el workflow y configurar el Trigger manual

**Objetivo:** Iniciar un nuevo flujo de automatización en n8n con un disparador manual que permita ejecutar el pipeline bajo demanda durante el desarrollo y las pruebas.

**Instrucciones:**

1. Abrir el navegador y acceder a `http://localhost:5678`.
2. En la pantalla principal de n8n, hacer clic en **+ Create Workflow** (esquina superior derecha o botón central).
3. Hacer clic en el nombre del workflow (por defecto `My workflow`) y renombrarlo a:

```
Monitor-Indicadores-v1
```

4. El canvas ya incluye un nodo **Manual Trigger** por defecto. Si no aparece, hacer clic en **+** en el canvas, buscar `Manual Trigger` y agregarlo.
5. Guardar el workflow con **Ctrl + S**.

**Resultado esperado:** El workflow `Monitor-Indicadores-v1` aparece en la lista de workflows de n8n con un nodo Manual Trigger en el canvas.

**Verificación:** El nombre `Monitor-Indicadores-v1` se muestra en la barra superior del editor de workflows.

---

### Paso 3: Agregar el nodo de lectura del archivo CSV

**Objetivo:** Configurar un nodo que lea el archivo CSV desde el sistema de archivos del contenedor y lo convierta en datos estructurados que los nodos posteriores puedan procesar.

**Instrucciones:**

1. En el canvas, hacer clic en el **+** a la derecha del nodo **Manual Trigger**.
2. En el buscador de nodos, escribir `Read/Write Files from Disk` y seleccionarlo.

> **Nota:** En n8n 1.45.1 este nodo se llama **Read/Write Files from Disk**. Si aparece como **Read Binary File**, seleccionar esa opción equivalente.

3. Configurar el nodo con los siguientes parámetros:
   - **Operation:** `Read File(s) From Disk`
   - **File(s) Selector:** `/home/node/.n8n/indicadores_operacion.csv`
4. Renombrar el nodo haciendo clic en su nombre y escribiendo:

```
Leer CSV Indicadores
```

5. Hacer clic en **Back to canvas**.
6. A continuación, agregar un nodo para extraer los datos del CSV. Hacer clic en **+** a la derecha del nodo `Leer CSV Indicadores`.
7. Buscar `Extract from File` y seleccionarlo.
8. Configurar:
   - **Operation:** `Extract From CSV`
   - **Input Binary Field:** `data` (valor por defecto)
9. Renombrar el nodo a:

```
Parsear CSV
```

10. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.

**Resultado esperado:** Dos nodos nuevos conectados en secuencia: `Leer CSV Indicadores` → `Parsear CSV`, ambos conectados al `Manual Trigger`.

**Verificación:** Hacer clic en el nodo `Leer CSV Indicadores`, luego **Test step**. Debe aparecer un item binario con el archivo. Luego hacer clic en `Parsear CSV` y **Test step**: debe mostrar 10 items JSON, cada uno con los campos `indicador`, `valor_actual`, `meta`, `unidad`, `turno` y `tipo_comparacion`.

---

### Paso 4: Agregar el nodo de lógica para detectar desviaciones

**Objetivo:** Implementar la lógica de comparación que evalúe cada indicador contra su meta y filtre únicamente aquellos que presenten desviación, generando además un texto consolidado para enviar al modelo de IA.

**Instrucciones:**

1. Hacer clic en **+** a la derecha del nodo `Parsear CSV`.
2. Buscar `Code` y seleccionar el nodo **Code**.
3. Renombrar el nodo a:

```
Detectar Desviaciones
```

4. En el campo **Language**, asegurarse de que esté seleccionado **JavaScript**.
5. Reemplazar todo el contenido del editor de código con el siguiente script:

```javascript
const items = $input.all();
const desviaciones = [];

for (const item of items) {
  const indicador = item.json.indicador;
  const valorActual = parseFloat(item.json.valor_actual);
  const meta = parseFloat(item.json.meta);
  const unidad = item.json.unidad;
  const turno = item.json.turno;
  const tipo = item.json.tipo_comparacion;

  let hayDesviacion = false;
  let diferencia = 0;

  if (tipo === 'mayor_o_igual') {
    // El valor debe ser >= meta; desviación si es menor
    hayDesviacion = valorActual < meta;
    diferencia = valorActual - meta;
  } else if (tipo === 'menor_o_igual') {
    // El valor debe ser <= meta; desviación si es mayor
    hayDesviacion = valorActual > meta;
    diferencia = valorActual - meta;
  }

  if (hayDesviacion) {
    desviaciones.push({
      indicador,
      valor_actual: valorActual,
      meta,
      diferencia: Math.round(diferencia * 100) / 100,
      unidad,
      turno
    });
  }
}

// Generar texto consolidado para el prompt de IA
let textoDesviaciones = "INDICADORES CON DESVIACIÓN DETECTADA:\n\n";
for (const d of desviaciones) {
  textoDesviaciones += `- ${d.indicador} (${d.turno}): Valor actual = ${d.valor_actual}${d.unidad}, Meta = ${d.meta}${d.unidad}, Diferencia = ${d.diferencia}${d.unidad}\n`;
}

return [{
  json: {
    total_indicadores: items.length,
    total_desviaciones: desviaciones.length,
    desviaciones: desviaciones,
    texto_para_ia: textoDesviaciones
  }
}];
```

6. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.

**Resultado esperado:** El nodo `Detectar Desviaciones` está conectado después de `Parsear CSV` y contiene la lógica de comparación.

**Verificación:** Hacer clic en el nodo `Detectar Desviaciones` y luego **Test step**. La salida debe ser un único item JSON con:
- `total_indicadores`: `10`
- `total_desviaciones`: `6`
- `desviaciones`: un arreglo con 6 objetos (Disponibilidad T1, Scrap T1, Tiempo_Paro T2, Rendimiento T2, Disponibilidad T3, OEE T3)
- `texto_para_ia`: un texto legible listando las 6 desviaciones

---

### Paso 5: Configurar las credenciales del modelo de IA

**Objetivo:** Registrar la clave de API del proveedor de IA seleccionado en n8n para que el nodo HTTP Request pueda consumir el servicio.

> **Nota:** Si ya se tiene la credencial `OpenAI-Lab05` del Lab 05-00-01 y se usará OpenAI, saltar al Paso 6 Opción B. Este paso documenta la configuración de Groq como ruta principal.

**Instrucciones:**

**Opción A — Groq (ruta principal):**

1. Acceder a [https://console.groq.com/keys](https://console.groq.com/keys) y crear una API key si no se tiene una.
2. Copiar la API key (comienza con `gsk_`).
3. En n8n, ir a **Settings** (ícono de engranaje en la barra lateral) → **Credentials**.
4. Hacer clic en **+ Add Credential**.
5. Buscar `Header Auth` y seleccionar **Header Auth**.
6. Configurar:
   - **Name:** `Authorization`
   - **Value:** `Bearer gsk_TU_API_KEY_AQUI` (reemplazar con la key real, incluir la palabra `Bearer` seguida de un espacio)
7. Nombrar la credencial:

```
Groq-Lab05
```

8. Hacer clic en **Save**.

**Opción B — OpenAI (alternativa):**

Si se reutiliza la credencial `OpenAI-Lab05` del Lab 05-00-01, no es necesario crear una nueva. Verificar en **Settings → Credentials** que `OpenAI-Lab05` sigue activa con indicador verde.

**Resultado esperado:** La credencial `Groq-Lab05` (Opción A) aparece en la lista de credenciales, o la credencial `OpenAI-Lab05` (Opción B) está verificada como activa.

**Verificación:** En **Settings → Credentials**, la credencial correspondiente aparece en la lista. La validación de conexión se realizará en el Paso 7 al ejecutar el nodo.

---

### Paso 6: Agregar el nodo HTTP Request para invocar al modelo de IA

**Objetivo:** Configurar un nodo que envíe las desviaciones detectadas al modelo de IA mediante API REST con un prompt estructurado que instruya al modelo a generar un reporte técnico de operaciones.

**Instrucciones:**

1. En el canvas, hacer clic en **+** a la derecha del nodo `Detectar Desviaciones`.
2. Buscar `HTTP Request` y seleccionar el nodo **HTTP Request**.
3. Renombrar el nodo a:

```
Analisis IA
```

4. Configurar los parámetros del nodo:

**Opción A — Groq:**

   - **Method:** `POST`
   - **URL:**

```
https://api.groq.com/openai/v1/chat/completions
```

   - **Authentication:** `Generic Credential Type`
   - **Generic Auth Type:** `Header Auth`
   - **Credential for Header Auth:** Seleccionar `Groq-Lab05`
   - **Send Headers:** Activar (ON)
   - Agregar header:
     - **Name:** `Content-Type`
     - **Value:** `application/json`
   - **Send Body:** Activar (ON)
   - **Body Content Type:** `JSON`
   - **Specify Body:** `Using JSON`
   - En el campo JSON, pegar:

```json
{
  "model": "llama-3-8b-8192",
  "temperature": 0.3,
  "messages": [
    {
      "role": "system",
      "content": "Eres un analista de operaciones industriales con experiencia en manufactura. Tu tarea es analizar indicadores de operación que presentan desviaciones respecto a sus metas y generar un reporte técnico estructurado. El reporte debe incluir: 1) RESUMEN EJECUTIVO (3-4 oraciones), 2) TABLA DE DESVIACIONES (formato texto con columnas: Indicador, Turno, Valor, Meta, Diferencia), 3) ANÁLISIS DE CAUSAS POSIBLES (una causa probable por cada indicador con desviación), 4) RECOMENDACIONES DE ACCIÓN (una acción concreta por cada desviación). Usa lenguaje técnico profesional en español. No inventes datos adicionales; trabaja solo con la información proporcionada."
    },
    {
      "role": "user",
      "content": "Analiza las siguientes desviaciones de indicadores de operación de una planta de manufactura y genera el reporte técnico:\n\n{{ $json.texto_para_ia }}\n\nTotal de indicadores monitoreados: {{ $json.total_indicadores }}\nTotal de desviaciones detectadas: {{ $json.total_desviaciones }}"
    }
  ]
}
```

**Opción B — OpenAI:**

   - **Method:** `POST`
   - **URL:**

```
https://api.openai.com/v1/chat/completions
```

   - **Authentication:** `Generic Credential Type`
   - **Generic Auth Type:** `Header Auth`
   - **Credential for Header Auth:** Seleccionar `OpenAI-Lab05` (si se configuró como Header Auth) o configurar manualmente agregando un header `Authorization` con valor `Bearer sk-TU_API_KEY`.
   - **Send Headers:** Activar (ON)
   - Agregar header:
     - **Name:** `Content-Type`
     - **Value:** `application/json`
   - **Send Body:** Activar (ON)
   - **Body Content Type:** `JSON`
   - **Specify Body:** `Using JSON`
   - En el campo JSON, pegar el mismo JSON de la Opción A pero cambiando la primera línea:

```json
{
  "model": "gpt-4o-mini",
  "temperature": 0.3,
  "messages": [
    {
      "role": "system",
      "content": "Eres un analista de operaciones industriales con experiencia en manufactura. Tu tarea es analizar indicadores de operación que presentan desviaciones respecto a sus metas y generar un reporte técnico estructurado. El reporte debe incluir: 1) RESUMEN EJECUTIVO (3-4 oraciones), 2) TABLA DE DESVIACIONES (formato texto con columnas: Indicador, Turno, Valor, Meta, Diferencia), 3) ANÁLISIS DE CAUSAS POSIBLES (una causa probable por cada indicador con desviación), 4) RECOMENDACIONES DE ACCIÓN (una acción concreta por cada desviación). Usa lenguaje técnico profesional en español. No inventes datos adicionales; trabaja solo con la información proporcionada."
    },
    {
      "role": "user",
      "content": "Analiza las siguientes desviaciones de indicadores de operación de una planta de manufactura y genera el reporte técnico:\n\n{{ $json.texto_para_ia }}\n\nTotal de indicadores monitoreados: {{ $json.total_indicadores }}\nTotal de desviaciones detectadas: {{ $json.total_desviaciones }}"
    }
  ]
}
```

5. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.

**Resultado esperado:** El nodo `Analisis IA` está conectado después de `Detectar Desviaciones` y configurado con la URL de la API, credenciales y el cuerpo JSON que incluye el prompt de sistema con las cinco componentes (rol, contexto, tarea, formato de salida, restricciones) y el prompt de usuario con las expresiones de n8n que inyectan los datos dinámicos.

**Verificación:** Revisar visualmente que el nodo muestra el método `POST` y la URL correcta. Las expresiones `{{ $json.texto_para_ia }}`, `{{ $json.total_indicadores }}` y `{{ $json.total_desviaciones }}` deben aparecer en el cuerpo del JSON (n8n las resaltará en color naranja).

---

### Paso 7: Probar el nodo de IA de forma aislada

**Objetivo:** Ejecutar el flujo hasta el nodo de IA para verificar que la API responde correctamente y el reporte generado tiene la estructura esperada antes de agregar el nodo de salida.

**Instrucciones:**

1. Hacer clic en el nodo `Analisis IA` en el canvas.
2. Hacer clic en **Test step** (esto ejecutará automáticamente todos los nodos anteriores).
3. Esperar la respuesta de la API (puede tardar 5-15 segundos dependiendo del proveedor).
4. En el panel de salida, localizar el campo `choices[0].message.content` — este contiene el reporte generado por la IA.
5. Verificar que el reporte contiene las cuatro secciones solicitadas: RESUMEN EJECUTIVO, TABLA DE DESVIACIONES, ANÁLISIS DE CAUSAS POSIBLES y RECOMENDACIONES DE ACCIÓN.

**Resultado esperado:** La API retorna un objeto JSON con status 200. El campo `choices[0].message.content` contiene un texto en español con las cuatro secciones del reporte técnico, mencionando las 6 desviaciones identificadas.

**Verificación:** El campo `choices` del JSON de respuesta no está vacío. El texto del reporte menciona al menos estos indicadores con desviación: Disponibilidad (Turno 1), Scrap (Turno 1), Tiempo_Paro (Turno 2), Rendimiento (Turno 2), Disponibilidad (Turno 3) y OEE (Turno 3). Si la API retorna un error, consultar la sección **Solución de Problemas**.

---

### Paso 8: Agregar el nodo Code para formatear el reporte final

**Objetivo:** Extraer el contenido del reporte de la respuesta de la API y formatearlo como un documento de texto completo con encabezado, fecha y metadatos del análisis.

**Instrucciones:**

1. Hacer clic en **+** a la derecha del nodo `Analisis IA`.
2. Buscar `Code` y seleccionar el nodo **Code**.
3. Renombrar el nodo a:

```
Formatear Reporte
```

4. En **Language**, seleccionar **JavaScript**.
5. Reemplazar el contenido del editor con:

```javascript
const respuestaIA = $input.first().json;

// Extraer el texto del reporte de la respuesta de la API
const contenidoReporte = respuestaIA.choices[0].message.content;
const modelo = respuestaIA.model || "modelo-no-identificado";
const tokensUsados = respuestaIA.usage
  ? respuestaIA.usage.total_tokens
  : "N/A";

// Construir el reporte final con metadatos
const fechaActual = new Date().toISOString().split('T')[0];
const horaActual = new Date().toTimeString().split(' ')[0];

const reporteFinal = `========================================
REPORTE TÉCNICO DE MONITOREO DE INDICADORES
========================================
Fecha de generación: ${fechaActual}
Hora de generación: ${horaActual}
Generado por: Flujo Monitor-Indicadores-v1 (n8n)
Modelo de IA utilizado: ${modelo}
Tokens consumidos: ${tokensUsados}
========================================

${contenidoReporte}

========================================
FIN DEL REPORTE
Nota: Este reporte fue generado automáticamente.
Las recomendaciones deben ser validadas por el equipo
de ingeniería antes de su implementación.
========================================`;

return [{
  json: {
    reporte_texto: reporteFinal,
    nombre_archivo: `reporte_indicadores_${fechaActual}.txt`,
    fecha: fechaActual
  }
}];
```

6. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.

**Resultado esperado:** El nodo `Formatear Reporte` está conectado después de `Analisis IA` y produce un JSON con el campo `reporte_texto` que contiene el reporte completo con encabezado y metadatos.

**Verificación:** Hacer clic en `Formatear Reporte` y **Test step**. El campo `reporte_texto` debe comenzar con la línea de `=` y contener el encabezado con fecha, hora y modelo. El campo `nombre_archivo` debe tener el formato `reporte_indicadores_YYYY-MM-DD.txt`.

---

### Paso 9: Agregar el nodo para convertir el reporte a archivo binario

**Objetivo:** Convertir el texto del reporte a un formato binario que n8n pueda escribir como archivo en disco.

**Instrucciones:**

1. Hacer clic en **+** a la derecha del nodo `Formatear Reporte`.
2. Buscar `Convert to File` y seleccionar el nodo **Convert to File**.
3. Configurar:
   - **Operation:** `Convert to Text File`
   - **Text Input Field:** `reporte_texto`
   - **File Name:** seleccionar **Expression** y escribir:

```
{{ $json.nombre_archivo }}
```

4. Renombrar el nodo a:

```
Convertir a Archivo
```

5. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.

**Resultado esperado:** El nodo `Convertir a Archivo` transforma el texto del reporte en un item binario listo para escritura en disco.

**Verificación:** Hacer clic en el nodo y **Test step**. La salida debe mostrar un item binario con el nombre de archivo `reporte_indicadores_YYYY-MM-DD.txt` y tipo MIME `text/plain`.

---

### Paso 10: Agregar el nodo de escritura del reporte en disco

**Objetivo:** Almacenar el reporte técnico generado como archivo de texto en el sistema de archivos del contenedor, completando el nodo de salida del flujo de automatización.

**Instrucciones:**

1. Hacer clic en **+** a la derecha del nodo `Convertir a Archivo`.
2. Buscar `Read/Write Files from Disk` y seleccionarlo.
3. Configurar:
   - **Operation:** `Write File to Disk`
   - **File Path and Name:** seleccionar **Expression** y escribir:

```
/home/node/.n8n/{{ $json.fileName }}
```

> **Nota:** `$json.fileName` es el nombre del archivo binario generado por el nodo anterior. Si n8n muestra el campo como `$binary.data.fileName`, usar esa referencia.

4. Renombrar el nodo a:

```
Guardar Reporte
```

5. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.

**Resultado esperado:** El flujo completo tiene 7 nodos conectados en secuencia: `Manual Trigger` → `Leer CSV Indicadores` → `Parsear CSV` → `Detectar Desviaciones` → `Analisis IA` → `Formatear Reporte` → `Convertir a Archivo` → `Guardar Reporte`.

**Verificación:** En el canvas, verificar visualmente que todos los nodos están conectados sin interrupciones. El flujo debe tener exactamente 8 nodos (incluyendo el Trigger).

---

### Paso 11: Ejecutar el flujo completo y validar el reporte

**Objetivo:** Ejecutar el flujo de principio a fin, verificar que cada nodo procesa correctamente y que el reporte final se almacena en disco con el contenido esperado.

**Instrucciones:**

1. En el canvas, hacer clic en **Test Workflow** (botón en la esquina inferior izquierda o inferior central del canvas).
2. Esperar a que todos los nodos se ejecuten. Cada nodo mostrará una marca verde (✓) si fue exitoso o roja (✗) si falló.
3. Verificar que todos los 8 nodos muestran marca verde.
4. Hacer clic en el nodo `Guardar Reporte` para confirmar que escribió el archivo exitosamente.
5. Verificar el archivo generado desde la terminal:

```bash
docker exec n8n ls -la /home/node/.n8n/reporte_indicadores_*.txt
```

6. Leer el contenido del reporte generado:

```bash
docker exec n8n cat /home/node/.n8n/reporte_indicadores_*.txt
```

7. Revisar que el reporte contiene:
   - Encabezado con fecha, hora y modelo utilizado.
   - Resumen ejecutivo.
   - Tabla de desviaciones con las 6 desviaciones del CSV.
   - Análisis de causas posibles.
   - Recomendaciones de acción.
   - Nota de cierre indicando que es un reporte automático.

**Resultado esperado:** El archivo `reporte_indicadores_YYYY-MM-DD.txt` existe en `/home/node/.n8n/` y contiene un reporte técnico completo y coherente en español con las cuatro secciones solicitadas al modelo de IA.

**Verificación:** El comando `cat` muestra el reporte completo. El reporte menciona explícitamente los 6 indicadores con desviación. La sección de recomendaciones contiene al menos una acción concreta por cada desviación.

---

### Paso 12: Copiar el reporte al equipo local

**Objetivo:** Extraer el reporte generado del contenedor Docker al equipo local para revisión, archivo o distribución.

**Instrucciones:**

1. Copiar el reporte al directorio actual del equipo local:

```bash
docker cp n8n:/home/node/.n8n/reporte_indicadores_*.txt ./reporte_final.txt
```

> **Nota:** Si el comando anterior falla por el wildcard, primero obtener el nombre exacto del archivo:

```bash
docker exec n8n ls /home/node/.n8n/reporte_indicadores_*.txt
```

Y luego copiar con el nombre completo:

```bash
docker cp n8n:/home/node/.n8n/reporte_indicadores_2025-01-15.txt ./reporte_final.txt
```

2. Abrir el archivo `reporte_final.txt` en un editor de texto para revisión.

**Resultado esperado:** El archivo `reporte_final.txt` está disponible en el equipo local y puede abrirse con cualquier editor de texto.

**Verificación:** El archivo tiene un tamaño mayor a 500 bytes (indicando que contiene contenido sustancial):

```bash
wc -c reporte_final.txt
```

---

### Paso 13: Ajustar el prompt y re-ejecutar (iteración)

**Objetivo:** Experimentar con la modificación del prompt del modelo de IA para mejorar la calidad o el enfoque del reporte, reforzando la importancia de la iteración en prompt engineering dentro de flujos automatizados.

**Instrucciones:**

1. En el canvas, hacer doble clic en el nodo `Analisis IA` para editarlo.
2. En el campo JSON del body, localizar el `content` del mensaje con `role: "system"`.
3. Agregar la siguiente restricción al final del texto del mensaje de sistema (antes de las comillas de cierre):

```
Además, al final del reporte incluye una sección 5) NIVEL DE RIESGO OPERATIVO donde clasifiques el estado general de la operación como VERDE (0-1 desviaciones), AMARILLO (2-3 desviaciones) o ROJO (4 o más desviaciones), con una justificación de una oración.
```

4. Hacer clic en **Back to canvas** y guardar con **Ctrl + S**.
5. Ejecutar nuevamente el flujo completo con **Test Workflow**.
6. Verificar en el nodo `Formatear Reporte` que el nuevo reporte incluye la sección de NIVEL DE RIESGO OPERATIVO.
7. Verificar el archivo actualizado:

```bash
docker exec n8n cat /home/node/.n8n/reporte_indicadores_*.txt
```

**Resultado esperado:** El reporte ahora incluye una quinta sección con la clasificación de riesgo. Dado que hay 6 desviaciones, el modelo debe clasificar el nivel como **ROJO**.

**Verificación:** El texto del reporte contiene la cadena "ROJO" o "rojo" en la sección de nivel de riesgo, junto con una justificación que menciona el número de desviaciones.

## Validación y Pruebas

Completar las siguientes verificaciones para confirmar que el laboratorio cumple sus objetivos:

**Prueba 1 — Integridad del flujo:**

Verificar que el workflow tiene 8 nodos conectados en secuencia ejecutando el flujo completo:

1. En el canvas de `Monitor-Indicadores-v1`, hacer clic en **Test Workflow**.
2. Confirmar que los 8 nodos muestran marca verde (✓).

**Criterio de éxito:** 8/8 nodos ejecutados exitosamente sin errores.

**Prueba 2 — Precisión de la detección de desviaciones:**

1. Hacer clic en el nodo `Detectar Desviaciones` y revisar la salida.
2. Verificar que `total_desviaciones` es exactamente `6`.
3. Verificar que los indicadores dentro de meta (Rendimiento T1, Disponibilidad T2, Scrap T2, Tiempo_Paro T3) **no** aparecen en el arreglo de desviaciones.

**Criterio de éxito:** Exactamente 6 desviaciones detectadas, 0 falsos positivos.

**Prueba 3 — Calidad del reporte de IA:**

1. Leer el reporte generado (`reporte_final.txt`).
2. Verificar que contiene las 5 secciones (incluyendo nivel de riesgo tras el Paso 13).
3. Confirmar que las recomendaciones son específicas a cada indicador (no genéricas).
4. Verificar que el modelo **no inventó indicadores** que no estaban en los datos de entrada.

**Criterio de éxito:** 5 secciones presentes, recomendaciones diferenciadas por indicador, sin datos fabricados.

**Prueba 4 — Caso adversario (información inexistente):**

Esta prueba valida las limitaciones de la IA y la necesidad de supervisión humana.

1. Editar el nodo `Analisis IA` y modificar temporalmente el mensaje de usuario para agregar al final:

```
Incluye también el análisis del indicador "Temperatura de horno" que tuvo un valor de 850°C contra una meta de 800°C.
```

2. Ejecutar **Test step** en el nodo `Analisis IA`.
3. Revisar si el modelo incluye el indicador "Temperatura de horno" en su reporte a pesar de que **no existe en el CSV original**.

**Criterio de éxito:** Si el modelo incluye el indicador ficticio, documenta una limitación importante: la IA procesa instrucciones del prompt sin validar contra la fuente de datos real. Esto refuerza la necesidad de que el prompt contenga la restricción "No inventes datos adicionales" y de que un humano supervise los reportes automatizados. **Revertir el cambio** después de la prueba.

4. Después de la prueba, restaurar el mensaje de usuario original (sin la línea de "Temperatura de horno") y guardar con **Ctrl + S**.

## Solución de Problemas

**Problema 1: El nodo `Analisis IA` retorna error 401 (Unauthorized) o 403 (Forbidden)**

| Aspecto | Detalle |
|---|---|
| **Síntoma** | Al ejecutar **Test step** en el nodo `Analisis IA`, n8n muestra un error HTTP con código 401 o 403. El mensaje puede incluir "Invalid API Key" o "Insufficient permissions". |
| **Causa** | La API key configurada en la credencial `Groq-Lab05` (o `OpenAI-Lab05`) es incorrecta, ha expirado, o el formato del header de autorización no incluye el prefijo `Bearer `. |
| **Solución** | 1. Ir a **Settings → Credentials** y editar la credencial correspondiente. 2. Verificar que el campo **Value** tiene el formato exacto: `Bearer gsk_xxxxx` (Groq) o `Bearer sk-xxxxx` (OpenAI), con un espacio entre `Bearer` y la key. 3. Si la key es correcta, acceder al portal del proveedor ([console.groq.com/keys](https://console.groq.com/keys) o [platform.openai.com/api-keys](https://platform.openai.com/api-keys)) y verificar que la key no ha sido revocada. 4. Generar una nueva key si es necesario, actualizar la credencial en n8n y volver a ejecutar. |

**Problema 2: El nodo `Parsear CSV` muestra 0 items o campos vacíos**

| Aspecto | Detalle |
|---|---|
| **Síntoma** | Al ejecutar **Test step** en `Parsear CSV`, la salida muestra 0 items, o los items tienen campos con valores vacíos o nombres de columna incorrectos. |
| **Causa** | El archivo CSV tiene un formato incorrecto: puede contener caracteres BOM (Byte Order Mark) invisibles al inicio del archivo, usar punto y coma (`;`) como separador en lugar de coma (`,`), o tener saltos de línea inconsistentes (mezcla de `\r\n` y `\n`). Esto ocurre frecuentemente cuando el CSV se crea con Excel en configuración regional en español. |
| **Solución** | 1. Verificar el contenido raw del archivo: `docker exec n8n xxd /home/node/.n8n/indicadores_operacion.csv | head -3`. Si los primeros bytes son `ef bb bf`, el archivo tiene BOM. 2. Recrear el archivo usando un editor de texto plano (no Excel) copiando el contenido exacto del Paso 1. 3. Asegurar que el separador sea coma (`,`) y no punto y coma. 4. Volver a copiar al contenedor: `docker cp indicadores_operacion.csv n8n:/home/node/.n8n/indicadores_operacion.csv`. 5. Re-ejecutar desde el nodo `Leer CSV Indicadores`. |

## Limpieza

Ejecutar los siguientes comandos para limpiar los archivos generados durante el laboratorio, manteniendo el contenedor y el workflow para referencia futura:

```bash
docker exec n8n rm -f /home/node/.n8n/indicadores_operacion.csv
docker exec n8n rm -f /home/node/.n8n/reporte_indicadores_*.txt
```

Verificar la limpieza:

```bash
docker exec n8n ls /home/node/.n8n/*.csv /home/node/.n8n/reporte_*.txt 2>&1
```

Salida esperada: `ls: cannot access '/home/node/.n8n/*.csv': No such file or directory` (o similar).

> **Nota:** El workflow `Monitor-Indicadores-v1` y las credenciales permanecen en n8n para referencia. Si se desea eliminar el workflow, hacerlo desde la interfaz de n8n en **Workflows** → seleccionar → **Delete**. **No detener ni eliminar** el contenedor `n8n` ya que puede ser necesario para actividades posteriores del curso.

Eliminar el archivo local si se copió:

```bash
rm -f reporte_final.txt
```

## Resumen

En este laboratorio se diseñó un flujo de automatización completo en n8n que implementa el patrón **Trigger → Lectura → Procesamiento → IA → Salida**, aplicando directamente los conceptos de la lección 5.1 sobre la diferencia entre asistencia y automatización mediante IA. El flujo creado (`Monitor-Indicadores-v1`) transforma una actividad repetitiva de monitoreo — que normalmente requiere que un ingeniero revise manualmente indicadores, identifique desviaciones, analice causas y redacte un reporte — en un pipeline automatizado que se ejecuta con un solo clic (o podría programarse con un Schedule Trigger para ejecución periódica).

**Conceptos clave reforzados:**

- **Automatización vs. asistencia:** El flujo opera sin intervención humana entre nodos; el ingeniero diseña y supervisa, pero no participa en cada ejecución.
- **Componentes de un flujo:** Trigger (Manual Trigger), nodos de procesamiento (Read File, Code), nodo de IA (HTTP Request a API de LLM) y nodo de salida (Write File).
- **Prompt engineering en automatización:** El prompt de sistema se diseñó con rol, contexto, tarea, formato de salida y restricciones, y se iteró para agregar la sección de nivel de riesgo.
- **Limitaciones de la IA:** La prueba adversaria del Paso 4 de Validación demostró que los modelos pueden incorporar datos ficticios del prompt, reforzando la necesidad de supervisión humana.

**Recursos adicionales:**

- Documentación de n8n — Nodo Code: [https://docs.n8n.io/code/](https://docs.n8n.io/code/)
- Documentación de n8n — HTTP Request: [https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/)
- Documentación de la API de Groq: [https://console.groq.com/docs/api-reference](https://console.groq.com/docs/api-reference)
- Documentación de la API de OpenAI: [https://platform.openai.com/docs/api-reference/chat](https://platform.openai.com/docs/api-reference/chat)
