# AI Lead Automation — Proyecto Final Coderhouse

## Descripción del proyecto

Sistema de automatización de gestión de leads que utiliza inteligencia artificial para analizar consultas comerciales, registrar la información y proponer respuestas, incorporando una instancia de aprobación humana antes de enviar una respuesta al cliente.

## Objetivo

Automatizar el procesamiento inicial de consultas comerciales, reducir tareas manuales y mantener supervisión humana sobre las respuestas enviadas.

## Tecnologías utilizadas

- **n8n:** orquestación y automatización de los workflows.
- **Airtable:** almacenamiento de leads, análisis de IA y decisiones de aprobación.
- **Google Gemini:** análisis de consultas y generación de respuestas propuestas.
- **Gmail:** notificaciones de aprobación y envío de respuestas.
- **Postman:** pruebas del Webhook y validación de datos.

## Arquitectura y funcionamiento

### Workflow 1: Recepción y análisis de leads

1. Recibe los datos mediante un Webhook HTTP.
2. Valida que estén presentes los datos obligatorios.
3. Registra el lead en Airtable.
4. Utiliza Gemini para generar prioridad, intención, resumen y respuesta propuesta.
5. Actualiza el registro en Airtable.
6. Envía un correo al responsable para solicitar aprobación humana.

### Workflow 2: Gestión de aprobaciones

1. Consulta periódicamente los registros de aprobación pendientes de procesar.
2. Si la decisión es **Aprobado**, envía la respuesta propuesta al lead mediante Gmail.
3. Si la decisión es **Rechazado**, no envía la respuesta al cliente.
4. Actualiza los estados correspondientes en Airtable y marca la aprobación como procesada.

## Validaciones y pruebas

Se realizaron pruebas para verificar:

- Recepción y procesamiento de un lead válido.
- Rechazo de solicitudes con datos obligatorios incompletos.
- Generación del análisis mediante IA.
- Envío del correo de solicitud de aprobación.
- Aprobación y envío automático de la respuesta.
- Rechazo de una propuesta sin enviar una respuesta al cliente.

## Documentación y evidencias

- **Diagrama de arquitectura:** `diagrama-arquitectura.pdf`
- **Workflow principal:** `workflows/ai-lead-assistant.json`
- **Workflow de aprobaciones:** `workflows/gestion-aprobaciones.json`
- **Capturas de evidencia:** carpeta `evidencias/`
- **Enlaces de acceso:** `enlaces.md`

## Consideraciones de seguridad

Las credenciales y claves API no deben incluirse en los archivos publicados. El acceso a la base de Airtable se compartirá en modo lectura, evitando exponer datos personales innecesarios.

---

Proyecto realizado como entrega final de la formación en AI Automation de Coderhouse.
