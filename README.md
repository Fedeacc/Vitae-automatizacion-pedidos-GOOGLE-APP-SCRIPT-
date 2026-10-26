# Automatización de pedidos – Google Apps Script

Backend del emprendimiento Vitae.Lp. Recibe los pedidos enviados desde la página web y los registra automáticamente, sin carga manual.

## Qué hace

1. Recibe una petición POST con los datos del pedido en JSON.
2. Guarda la foto del cliente (enviada en Base64) en una carpeta de Google Drive.
3. Agrega una fila en Google Sheets con fecha, nombre, WhatsApp, pedido, tipo de pago, monto, estado ("Pendiente") y link a la foto.
4. Responde con un JSON indicando éxito o error.

## Tecnologías

Google Apps Script (JavaScript) · Google Sheets · Google Drive

## Datos que espera recibir

```json
{
  "nombre": "string",
  "whatsapp": "string",
  "pedido": "string",
  "tipoPago": "string",
  "monto": 0,
  "archivoBase64": "string",
  "nombreArchivo": "foto.jpg"
}
```

## Cómo usarlo

1. Creá una planilla de Google Sheets y abrí **Extensiones → Apps Script**.
2. Pegá el código y reemplazá `FOLDER_ID` por el ID de tu carpeta de Drive.
3. **Implementar → Nueva implementación → Aplicación web.**
4. Usá la URL generada como destino del POST desde tu página.

## Mejoras futuras

- Validar los datos recibidos y limitar el tamaño y tipo de archivo.
- Agregar un token secreto para que solo la página pueda enviar pedidos.
- Detectar el tipo real de imagen en vez de asumir JPEG.
