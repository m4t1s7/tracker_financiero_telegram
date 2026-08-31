# tracker_financiero_telegram

Descripción: Sistema de automatización para captura de egresos e ingresos en tiempo real mediante un bot interactivo de Telegram, procesado con lógica en JavaScript dentro de n8n y persistido en Microsoft Excel.

Arquitectura / Flujo:

Trigger de Telegram (Mensajes y botones con callback_query).

Nodo Code (JS) para parseo y limpieza de cadenas clave-valor.

API de Microsoft Excel para inserción automática.

Cómo usarlo / Despliegue: En una instancia de n8n importar el JSON expuesto en main, configurar las credenciales de cada nodo con datos personales (requerirá, en la versión alojada en un servidor propio o adquirido, de configurar una app en azure de microsoft), crear un bot de Telegram de la forma preferida para ajustar sus credenciales y habrá finalizado el despliegue.
