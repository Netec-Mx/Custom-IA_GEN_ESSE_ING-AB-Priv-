<p align="center">
  <img src="assets/LogoNetec.png" alt="NETEC" width="300" />
</p>

# Setup Guide General

## Inteligencia Artificial Generativa Essentials aplicada a la Ingeniería

| Control documental | Información |
|---|---|
| Clave del curso | Custom IA_GEN_ESSE_ING AB (Priv) |
| Versión del documento | 1.0 |
| Estado | BORRADOR: revisión documental completa; pendiente de validación con cuentas de participante |
| Instructor responsable | Por asignar por Netec |
| Fecha de elaboración | 2026-11-09 |
| Fecha de última validación | 2026-11-09 (revisión del repositorio) |
| Repositorio de laboratorios | [github.com/Netec-Mx/Custom-IA_GEN_ESSE_ING-AB-Priv-](https://github.com/Netec-Mx/Custom-IA_GEN_ESSE_ING-AB-Priv-) |
| Rama y revisión analizada | `changes_course`, versión 1.0 |
| Alcance revisado | 3 capítulos, 6 módulos, 12 prácticas, 19 archivos de recursos, README principal y Setup Guide |
| Modalidad del entorno | Web (servicios SaaS gratuitos) con aplicaciones de ofimática locales o en la web |

[Inicio](README.md)

# Objetivo

Preparar, para cada participante, un equipo con navegador actualizado, Microsoft Word, Excel y PowerPoint (escritorio o web), cuentas gratuitas activas en ChatGPT, Microsoft Copilot, Google (Gemini, NotebookLM y Google AI Studio) y Claude, y acceso a n8n con una credencial de un modelo de IA gratuito. También se descargan los archivos ficticios de las 12 prácticas en una carpeta local. El entorno se considera listo cuando las validaciones obligatorias de la sección [Validación del Entorno](#validacion-entorno) se aprueban con la cuenta de un participante. No se requiere programación ni línea de comandos.

# Requisitos de Hardware

| Recurso | Mínimo requerido | Recomendado | Observaciones |
|---|---|---|---|
| Procesador y arquitectura | 64 bits, 2 núcleos | 4 núcleos o más | Las herramientas de IA y n8n Cloud se ejecutan en la nube |
| Memoria RAM | 8 GB | 16 GB | Varias pestañas del navegador y Office abiertos a la vez |
| Espacio libre | 2 GB | 5 GB | Los archivos de las prácticas ocupan menos de 1 MB |
| Pantalla | 1366 × 768 | 1920 × 1080 o dos monitores | Facilita comparar plataformas (Práctica 7) y trabajar en el lienzo de n8n (prácticas 5 y 6) |
| Conectividad | 10 Mbps por participante | 25 Mbps por participante | Necesaria durante todo el curso |

# Sistemas Operativos Compatibles

| Sistema operativo | Edición y versión | Arquitectura | Condición de soporte o validación |
|---|---|---|---|
| Windows 11 | Home, Pro o Enterprise | x64 | Plataforma base del curso; compatible según fabricante; pendiente de validar |
| macOS | 14 o posterior | Apple silicon o Intel | Compatible según fabricante; no validado. Los atajos de teclado cambian (Cmd en lugar de Ctrl) |

Las instrucciones usan Windows 11 y los nombres de menú de Microsoft Word y Excel en español.

# Software Requerido

| Componente | Edición y versión requerida | Arquitectura | Obligatorio u opcional | Fuente oficial |
|---|---|---|---|---|
| Navegador Microsoft Edge o Google Chrome | Versión estable vigente | x64 | Obligatorio | [google.com/chrome](https://www.google.com/chrome/) o [microsoft.com/edge](https://www.microsoft.com/edge) |
| Microsoft Word, Excel y PowerPoint | Escritorio o web (Office en la web gratuito con cuenta Microsoft); no se requiere licencia de Microsoft 365 Copilot | x64 | Obligatorio (para abrir y editar los archivos) | [microsoft365.com](https://www.microsoft365.com/) |
| ChatGPT | Servicio administrado, plan gratuito | N/A | Obligatorio (prácticas 7 y 11; opcional en 1 a 4) | [chatgpt.com](https://chatgpt.com/) |
| Microsoft Copilot Chat | Servicio administrado, versión gratuita | N/A | Obligatorio (prácticas 7 y 8; opcional en 1 a 4) | [copilot.microsoft.com](https://copilot.microsoft.com/) o [m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat) |
| Claude | Servicio administrado, plan gratuito | N/A | Obligatorio (prácticas 7 y 12; opcional en 1 a 4) | [claude.ai](https://claude.ai/) |
| Google Gemini | Servicio administrado, plan gratuito | N/A | Obligatorio (Práctica 7; opcional en 1 a 4) | [gemini.google.com](https://gemini.google.com/) |
| Google NotebookLM | Servicio administrado, plan gratuito | N/A | Obligatorio (Práctica 9) | [notebooklm.google.com](https://notebooklm.google.com/) |
| Google AI Studio | Servicio administrado, nivel gratuito | N/A | Obligatorio (Práctica 10 y clave de API para las prácticas 5 y 6) | [aistudio.google.com](https://aistudio.google.com/) |
| n8n | n8n Cloud (periodo de prueba gratuito) o n8n Community autoalojado por el instructor o TI | N/A | Obligatorio (prácticas 5 y 6) | [n8n.io/pricing](https://n8n.io/pricing/) y [docs.n8n.io/hosting](https://docs.n8n.io/hosting/) |

Los servicios de IA son administrados y cambian sus modelos, funciones y límites sin previo aviso. Las prácticas no fijan una versión de modelo: registrar la versión observada y las limitaciones en el [Registro de validación](#registro-validacion).

**Criterios de uso de herramientas acordados con el cliente**

| Criterio | Aplicación en este curso |
|---|---|
| Versiones gratuitas | Todas las prácticas se realizan con versiones gratuitas o periodos de prueba sin costo; no es obligatorio adquirir licencias Premium |
| Herramientas obligatorias | Solo en los módulos 5 y 6: n8n en las prácticas 5 y 6, y ChatGPT, Copilot, Claude, Gemini, NotebookLM y Google AI Studio en las prácticas 7 a 12 |
| Flexibilidad del instructor | En los módulos 1 a 4 (prácticas 1 a 4), el instructor elige la herramienta de IA según sus capacidades, disponibilidad y límites de consumo |
| Copilot con Word, Excel y PowerPoint | Práctica 8: Copilot Chat gratuito con carga de archivos; Copilot genera el contenido o los entregables descargables. No se usa Copilot integrado en las aplicaciones de Office |
| Limitaciones de las versiones gratuitas | En todas las prácticas, el instructor puede simplificar escenarios, usar datos más pequeños o ajustar la profundidad y la extensión, conservando los objetivos y resultados esperados |

# Herramientas y Dependencias

## Paquetes, frameworks y componentes adicionales

| Dependencia | Versión o restricción | Componente que la necesita | Método de instalación o habilitación |
|---|---|---|---|
| Carga de archivos en las herramientas de IA | Incluida en los planes gratuitos, con límites diarios | Prácticas 1 a 4 y 7 a 12 | Botón **+** o clip del cuadro de mensaje |
| Análisis de datos de ChatGPT (Advanced Data Analysis) | Disponible en el plan gratuito con límites | Práctica 11 | Se activa al adjuntar un CSV ([documentación](https://help.openai.com/en/articles/8437071-data-analysis-with-chatgpt)) |
| Canvas de ChatGPT | Disponible en el plan gratuito | Práctica 11 | Herramientas del cuadro de mensaje |
| Proyectos de Claude | Según el plan y la versión disponible | Práctica 12 | Panel izquierdo de Claude ([documentación](https://support.claude.com/en/articles/9517075-what-are-projects)); si no está disponible, se adjuntan los archivos en el chat |
| Instrucciones de sistema de Google AI Studio | Nivel gratuito | Práctica 10 | Panel **System instructions** del chat |
| Nodos de n8n | Form Trigger, Basic LLM Chain, Google Gemini Chat Model, Structured Output Parser, Switch, Edit Fields, Extract from File, Aggregate, Convert to File, n8n Form | Prácticas 5 y 6 | Incluidos en n8n Cloud y Community ([documentación](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm/)) |
| Credencial **Google Gemini(PaLM) Api** en n8n | Clave gratuita de Google AI Studio | Prácticas 5 y 6 | **Credentials > Create credential** ([documentación](https://docs.n8n.io/integrations/builtin/credentials/googleai/)) |
| Nodo Gmail de n8n | Opcional | Práctica 5, opción B | **Sign in with Google** desde el nodo ([documentación](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.gmail/)) |
| Archivos de las prácticas | Versión 1.0 del repositorio | Prácticas 1 a 12 | Carpetas `CapituloNN/PracticaNN/recursos/` (la Práctica 10 usa los archivos de la Práctica 9) |

## Licencias, cuentas y permisos

| Recurso o servicio | Licencia o suscripción | Cuenta o rol requerido | Permiso mínimo | Responsable de habilitación |
|---|---|---|---|---|
| ChatGPT | Gratuita | Cuenta de OpenAI | Usuario | Cada participante |
| Microsoft Copilot | Gratuita | Cuenta Microsoft (personal, de trabajo o escuela) | Usuario | Cada participante o TI del cliente |
| Gemini, NotebookLM y Google AI Studio | Gratuita | Cuenta de Google | Usuario | Cada participante |
| Claude | Gratuita | Cuenta de Anthropic | Usuario | Cada participante |
| n8n Cloud | Periodo de prueba gratuito | Cuenta de n8n (una por participante) | Propietario de su espacio | Cada participante, cerca de la fecha del Módulo 5 |
| n8n Community (alternativa) | Licencia Sustainable Use (sin costo) | Usuario creado por el administrador | Miembro | Instructor o TI del cliente |
| Microsoft 365 | Licencia del cliente o cuenta gratuita de Office en la web | Cuenta Microsoft | Usuario | TI del cliente |
| Acceso al repositorio | Repositorio privado de GitHub | Cuenta de GitHub con acceso de lectura, o paquete ZIP entregado por el instructor | Lectura | Netec |

Las cuentas y la clave de Google AI Studio son personales. No registrar contraseñas, claves ni códigos de verificación en este repositorio ni en los entregables. El periodo de prueba de n8n Cloud es por tiempo limitado: crear la cuenta cerca de la fecha del Módulo 5.

# Instalación y Configuración

## 1. Obtener los materiales

- Repositorio autorizado: [github.com/Netec-Mx/Custom-IA_GEN_ESSE_ING-AB-Priv-](https://github.com/Netec-Mx/Custom-IA_GEN_ESSE_ING-AB-Priv-) (botón **Code > Download ZIP**) o paquete ZIP entregado por el instructor.
- Revisión: rama `main`, una vez integrados los cambios de `changes_course`.
- Directorio de trabajo: `Documentos\Practicas_IA_Ingenieria\` con una subcarpeta por práctica (`Practica01` a `Practica12`).
- Archivos de entrada: carpetas `recursos` de cada práctica.

## 2. Instalar o habilitar los componentes

### Navegador y ofimática

1. Verificar que Edge o Chrome esté actualizado (**Configuración > Acerca de**).
2. Verificar el acceso a Word, Excel y PowerPoint (escritorio o [microsoft365.com](https://www.microsoft365.com/)).

**Resultado esperado:** El navegador indica que está actualizado y Excel abre un libro en blanco.

### Cuentas de IA

1. Crear o iniciar sesión en ChatGPT, Copilot, Gemini, NotebookLM, Google AI Studio y Claude.
2. Aceptar los términos de uso de cada servicio.
3. Enviar un mensaje de prueba en cada uno (por ejemplo, *"Responde solo OK"*).

**Resultado esperado:** Cada servicio responde con la sesión iniciada.

### n8n y modelo de IA gratuito

1. Crear una cuenta de prueba en [n8n.io](https://n8n.io/pricing/) o recibir del instructor la dirección y el usuario de la instancia Community.
2. Obtener una clave en [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) (**Create API key**).
3. En n8n, crear la credencial **Google Gemini(PaLM) Api** con la clave.

**Resultado esperado:** n8n abre el lienzo de flujos y la credencial queda guardada.

### Carpetas de trabajo

1. Descomprimir el ZIP del repositorio.
2. Crear `Documentos\Practicas_IA_Ingenieria\` y, dentro, las carpetas `Practica01` a `Practica12`.
3. Copiar a cada carpeta el contenido de `CapituloNN\PracticaNN\recursos` correspondiente. Para la Práctica 10, copiar los 4 PDF de la Práctica 9.

**Resultado esperado:** 19 archivos de recursos distribuidos en las carpetas de las prácticas.

## 3. Preparar archivos de configuración

No se requieren archivos de configuración. Los archivos de entrada están en las carpetas `recursos` y no deben modificarse antes de la práctica.

# Variables de Entorno

No se requieren variables de entorno: el curso no usa programación ni línea de comandos.

# Configuración Base para los Laboratorios

## Parámetros comunes

| Parámetro | Valor o convención | Observaciones |
|---|---|---|
| Raíz de trabajo | `Documentos\Practicas_IA_Ingenieria\` | Una carpeta por práctica |
| Nombre de entregables | `Nombre_[INICIALES].ext` | Ejemplo: `Lista_Verificacion_Respuesta_IA_LMR.xlsx` |
| Datos | Ficticios o anonimizados | No cargar información real de la organización |
| Nombres de flujos en n8n | `P05 ...` y `P06 ...` con las iniciales del participante | Evita confusiones en instancias compartidas |
| Escenarios técnicos | Torre de enfriamiento CT-4500X (prácticas 1 a 4), prensa hidráulica PH-400 (prácticas 8 a 11) y compresor de aire CA-250 (Práctica 12) | Equipos ficticios |

## Estructura de carpetas

```text
Documentos\Practicas_IA_Ingenieria\
├── Practica01\ ... Practica12\   Archivos de cada práctica y entregables
```

## Recursos compartidos

No hay recursos compartidos entre participantes, salvo la instancia de n8n Community si el instructor la usa. En ese caso, cada participante crea sus propios flujos y su propia credencial.

## Correcciones de coherencia

| Inconsistencia o dependencia omitida | Configuración unificada | Ajuste necesario en las copias de trabajo |
|---|---|---|
| El repositorio tenía 4 carpetas numeradas por módulo (`Capitulo03` a `Capitulo06`); el temario define 3 capítulos con 6 módulos | `Capitulo01` a `Capitulo03`, con una carpeta y un README por práctica | Ninguno |
| Varias prácticas estaban juntas en un mismo README | Un README por práctica (12 en total) | Ninguno |
| Las prácticas de n8n usaban nodos Code con JavaScript, Docker y comandos de terminal (`docker cp`), contrario al perfil "sin experiencia en programación" | Flujos sin código: formulario, Extract from File, Aggregate, Basic LLM Chain con salida estructurada, Switch y Convert to File | Ninguno |
| Una práctica de n8n dependía de un modelo obsoleto de Groq (Llama 3 8B, `llama-3-8b-8192`) | Modelo Gemini con clave gratuita de Google AI Studio | Ninguno |
| El participante debía capturar a mano un Excel de 20 filas, crear 4 documentos en Google Docs y "replicar el patrón" hasta 80 registros, lo que no cabe en prácticas de 14 minutos | 19 archivos listos para descargar en `recursos` | Ninguno |
| Se citaba ISO 10816-3 con el grupo 2 como "15-75 kW sobre soporte rígido, límite 7.1 mm/s" | ISO 20816-3 (sustituye a ISO 10816-3): grupo 2 de 15 kW a 300 kW; zona C/D de 4.5 mm/s (rígido) y 7.1 mm/s (flexible) | Ninguno |
| La fuente de referencia citaba CTI STD-201 como estándar de prueba y un título antiguo de ASHRAE Guideline 12 | CTI ATC-105 (prueba), CTI STD-201 (certificación) y ASHRAE Guideline 12-2023 (versión vigente) | Ninguno |
| La Práctica 12 llamaba "Compresor PH-400" a un equipo, mientras las prácticas 9 a 11 usan PH-400 para una prensa hidráulica | Compresor de aire CA-250 en la Práctica 12 | Ninguno |
| El procedimiento indicaba que 0.1% de agua en el aceite equivale a 500 ppm | 0.1% = 1,000 ppm | Ninguno |
| El dato erróneo deliberado del Excel de Copilot era "1absorption" | Error de captura realista: `12O0` (letra O) | Ninguno |
| Se citaban versiones de 2024 (GPT-4o, Claude 3.5 Sonnet, Gemini 1.5 Flash, n8n 1.44/1.45, Chrome 124) | Se indica "versión gratuita vigente" | Registrar la versión observada en cada curso |
| Los enlaces apuntaban a otro repositorio (`261109-Custom-IA-GEN-ESSE-ING-AB-Priv`) | Enlaces relativos dentro del repositorio | Ninguno |
| El archivo se llamaba `SETUP_GUIDE.md` | `Setup_Guide.md`, según la plantilla | Ninguno |

# Servicios Externos Requeridos

| Servicio | URL, endpoint o región | Uso | Acceso requerido |
|---|---|---|---|
| ChatGPT | [chatgpt.com](https://chatgpt.com/) | Prácticas 1 a 4 (opcional), 7 y 11 | Cuenta gratuita |
| Microsoft Copilot | [copilot.microsoft.com](https://copilot.microsoft.com/) | Prácticas 1 a 4 (opcional), 7 y 8 | Cuenta Microsoft |
| Google Gemini | [gemini.google.com](https://gemini.google.com/) | Prácticas 1 a 4 (opcional) y 7 | Cuenta de Google |
| Google NotebookLM | [notebooklm.google.com](https://notebooklm.google.com/) | Práctica 9 | Cuenta de Google |
| Google AI Studio | [aistudio.google.com](https://aistudio.google.com/) | Práctica 10 y clave de API | Cuenta de Google |
| Claude | [claude.ai](https://claude.ai/) | Prácticas 1 a 4 (opcional), 7 y 12 | Cuenta gratuita |
| n8n Cloud | Dominio asignado al crear la cuenta (`*.app.n8n.cloud`) | Prácticas 5 y 6 | Cuenta de prueba |
| API de Gemini | `generativelanguage.googleapis.com` | Prácticas 5 y 6 (llamada desde n8n) | Clave gratuita de Google AI Studio |
| GitHub | [github.com](https://github.com/) | Descarga de materiales | Lectura del repositorio |

## Configuración de red

| Origen | Destino | Protocolo y puerto | Sentido | Condición |
|---|---|---|---|---|
| Equipo del participante | chatgpt.com, copilot.microsoft.com, m365.cloud.microsoft, gemini.google.com, notebooklm.google.com, aistudio.google.com, claude.ai, n8n.io, app.n8n.cloud, github.com | HTTPS 443 | Saliente | Los dominios no deben estar bloqueados por el proxy o el firewall del cliente |
| Instancia de n8n (Cloud o Community) | generativelanguage.googleapis.com | HTTPS 443 | Saliente | Necesario para que el nodo de IA responda |

# Creación de Entornos / Máquinas Virtuales / Emuladores

No aplica para los participantes. Si el instructor o TI decide usar n8n Community en lugar de n8n Cloud, debe instalarlo con anticipación siguiendo la [documentación oficial de hosting](https://docs.n8n.io/hosting/) y entregar a cada participante su usuario y la dirección de acceso.

<a id="validacion-entorno"></a>

# Validación del Entorno

| ID | Componente o capacidad | Procedimiento | Resultado esperado | Evidencia mínima |
|---|---|---|---|---|
| V-01 | Navegador y materiales | Abrir el repositorio y descargar el ZIP | El ZIP contiene `Capitulo01` a `Capitulo03` | Captura |
| V-02 | Ofimática | Abrir `Lista_Verificacion_Respuesta_IA.xlsx` y elegir una categoría de la lista desplegable | La lista muestra 5 categorías | Captura |
| V-03 | ChatGPT | Adjuntar `Calidad_Produccion_PH400.csv` y pedir el número de filas | 120 filas | Captura |
| V-04 | Copilot | Adjuntar `Indicadores_Operacion_PH400.xlsx` (o el CSV) y pedir el número de registros | 20 registros | Captura |
| V-05 | NotebookLM | Crear un cuaderno y subir `MOP-2026-001_Manual_Operacion_PH-400.pdf` | La fuente aparece en el panel | Captura |
| V-06 | Google AI Studio | Crear un chat con instrucciones de sistema *"Responde solo OK"* y enviar un mensaje | Responde OK | Captura |
| V-07 | Claude | Adjuntar `DOC2_Reporte_Inspeccion_CA-250.pdf` y preguntar la vibración medida | 5.1 mm/s RMS | Captura |
| V-08 | Gemini | Enviar *"Responde solo OK"* | Responde OK | Captura |
| V-09 | n8n y modelo de IA | Crear un flujo con **On new n8n Form event** + **Basic LLM Chain** con Gemini y el prompt *"Responde solo OK"*; ejecutar | El nodo de IA responde OK | Captura de la ejecución |

**Criterio de entorno listo:** V-01 a V-09 aprobadas con la cuenta de un participante. Si V-09 falla por un bloqueo de red, el instructor debe resolverlo antes del Módulo 5 o usar una instancia de n8n con salida a Internet.

# Comandos de Verificación

No aplica. El curso se valida en interfaces web con los procedimientos V-01 a V-09, sin instalar herramientas de línea de comandos.

# Troubleshooting

| Síntoma | Causa probable | Comprobación | Corrección | Validación posterior |
|---|---|---|---|---|
| Un servicio de IA no carga | Bloqueo de red del cliente | Abrir el sitio desde otra red | Solicitar a TI la autorización del dominio | V-03 a V-09 |
| Límite de mensajes o de archivos alcanzado | Restricciones de la versión gratuita | Mensaje del servicio | Esperar, usar otra herramienta (prácticas 1 a 4) o reducir el alcance | Repetir el paso |
| Un archivo no se adjunta | Formato o tamaño no admitido | Mensaje de error | Usar la versión CSV o pegar el contenido como texto | Repetir el paso |
| El nodo de IA de n8n o Google AI Studio responde con error 429 o *quota* | Límite del nivel gratuito de la API de Gemini | Mensaje del servicio | Esperar un minuto o elegir otro modelo Flash de la lista | V-06 y V-09 |
| La credencial de Gemini no se guarda | Clave mal copiada o API no disponible en la región de la cuenta | Probar la clave en Google AI Studio | Crear una clave nueva; usar otra cuenta de Google si la región no está habilitada | V-09 |
| El periodo de prueba de n8n Cloud venció | Cuenta creada con demasiada anticipación | Mensaje al iniciar sesión | Crear la cuenta con otro correo o usar la instancia Community del instructor | V-09 |
| NotebookLM o Google AI Studio no están disponibles | Restricción de edad, región o administración de la cuenta | Mensaje de acceso | Usar una cuenta de Google que cumpla los requisitos | V-05 y V-06 |

# Checklist Final

- [ ] Navegador actualizado y Word, Excel y PowerPoint disponibles.
- [ ] Cuentas gratuitas activas en ChatGPT, Copilot, Google (Gemini, NotebookLM y AI Studio) y Claude.
- [ ] Acceso a n8n (prueba de n8n Cloud vigente o instancia Community) y credencial de Gemini guardada.
- [ ] Dominios de las herramientas permitidos en la red del cliente.
- [ ] 19 archivos de las prácticas descargados en `Documentos\Practicas_IA_Ingenieria\`.
- [ ] Validaciones V-01 a V-09 aprobadas y registradas.

# Resumen

Para iniciar el curso, cada participante necesita un navegador actualizado, Word, Excel y PowerPoint, cuentas gratuitas en las cuatro plataformas de IA, NotebookLM y Google AI Studio, acceso a n8n con una clave gratuita de Gemini y los archivos ficticios de las prácticas descargados. No se requiere programación ni instalación de lenguajes o herramientas de línea de comandos.

<a id="registro-validacion"></a>

## Registro de validación

| Fecha | Responsable | Plataforma o entorno probado | Resultado | Limitaciones o acciones pendientes |
|---|---|---|---|---|
| 2026-11-09 | Desarrollo de contenido Netec | Revisión del repositorio: estructura, enlaces, recursos, tiempos, nombres y alineación con el temario. Se recalcularon los valores de referencia de las prácticas 4, 6, 8 y 11 a partir de los archivos | APTO para publicación del repositorio | No se ejecutaron las prácticas con cuentas de participante ni los flujos de n8n. Pendiente: V-01 a V-09 |

## Referencias oficiales

| Documento o recurso | URL | Fecha de consulta |
|---|---|---|
| Análisis de datos con ChatGPT | https://help.openai.com/en/articles/8437071-data-analysis-with-chatgpt | 2026-11-09 |
| Proyectos de Claude | https://support.claude.com/en/articles/9517075-what-are-projects | 2026-11-09 |
| Planes de n8n | https://n8n.io/pricing/ | 2026-11-09 |
| n8n: hosting de la edición Community | https://docs.n8n.io/hosting/ | 2026-11-09 |
| n8n: nodo n8n Form Trigger | https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger/ | 2026-11-09 |
| n8n: nodo Basic LLM Chain | https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm/ | 2026-11-09 |
| n8n: credencial de Google Gemini | https://docs.n8n.io/integrations/builtin/credentials/googleai/ | 2026-11-09 |
| Precios y nivel gratuito de la API de Gemini | https://ai.google.dev/gemini-api/docs/pricing | 2026-11-09 |
| ISO 20816-3:2022 (vibración mecánica, máquinas industriales) | https://www.iso.org/standard/78311.html | 2026-11-09 |
| ASHRAE Guideline 12-2023 | https://www.techstreet.com/ashrae/products/2568228 | 2026-11-09 |
| Cooling Technology Institute | https://www.cti.org/ | 2026-11-09 |
| Política de privacidad de OpenAI | https://openai.com/es-ES/policies/privacy-policy/ | 2026-11-09 |
| Declaración de privacidad de Microsoft | https://www.microsoft.com/es-es/privacy/privacystatement | 2026-11-09 |
| Política de privacidad de Google | https://policies.google.com/privacy | 2026-11-09 |
| Política de privacidad de Anthropic | https://www.anthropic.com/legal/privacy | 2026-11-09 |

[Inicio](README.md)
