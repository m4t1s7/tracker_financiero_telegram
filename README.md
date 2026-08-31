# Tracker Financiero en Telegram (n8n + Microsoft Excel API)

Sistema de automatización para la captura e ingesta de egresos e ingresos en tiempo real mediante un bot interactivo de Telegram. El procesamiento de datos se realiza con lógica personalizada en JavaScript dentro de **n8n** y la persistencia se gestiona en **Microsoft Excel Online**.

---

## Arquitectura y Flujo

1. **Telegram Trigger:** Recepción de mensajes de texto e interacciones mediante botones en pantalla (`callback_query`).
2. **Switch & Response Nodes:** Generación dinámica de plantillas para captura de datos.
3. **Node Code (JavaScript):** Algoritmo de parseo para extraer, limpiar y convertir cadenas `clave: valor` en un objeto JSON estructurado.
4. **Microsoft Excel API:** Inserción automática de filas en la tabla del libro contable.

---

## Despliegue y Configuración

### 1. Requisitos Previos
* Una instancia de **n8n** activa (en servidor propio o local).
* Un Bot de Telegram creado vía `@BotFather` (guardar el API Token).
* Una cuenta de Microsoft OneDrive / Excel Online.
* *(Si usas n8n en servidor propio)* Una aplicación registrada en **Microsoft Azure Portal** para la autenticación OAuth2 del nodo de Excel.

### 2. Configuración en Excel
1. Crea un archivo `.xlsx` en tu OneDrive.
2. Define las siguientes columnas: `Fecha`, `Descripción`, `Categoría`, `Tipo` y `Monto (COP)`.
3. Selecciona el rango y conviértelo en una **Tabla formateada** (`Ctrl + T` en Windows / `Cmd + T` en Mac).

### 3. Importación del Flujo
1. En tu panel de n8n, crea un flujo nuevo e importa el archivo `tracker.json` cargado en este repositorio.
2. Configura las credenciales de los nodos de **Telegram** y **Microsoft Excel**.
3. Selecciona tu libro de Excel y la tabla correspondiente dentro del nodo *Append rows to table*.
4. Activa el flujo (`Active = True`).

---

## Modo de Uso

### Para solicitar la plantilla:
1. Escribe la palabra **`Formato`** (respetando la mayúscula) en el chat con tu bot.
2. Haz clic en el botón interactivo según la transacción: **[Ingreso]** o **[Egreso]**.

### Para registrar un movimiento:
1. Copia la plantilla que te devuelve el bot:
   ```text
   Fecha: 08-31-2026
   Descripción: Almuerzo
   Categoría: Alimentación
   Tipo: Egreso
   Monto: 25000
