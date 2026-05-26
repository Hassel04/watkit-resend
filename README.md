# watkit-resend

Módulo de notificaciones por correo electrónico para Watkit API, usando Resend y n8n.

## ¿Qué hace?

Al detectarse un nuevo push o commit en el repositorio de Watkit API, este módulo envía automáticamente un correo electrónico de notificación al destinatario configurado, complementando el canal de alertas por Telegram ya existente.

## Tecnologías usadas

- [Resend](https://resend.com) — API de envío de correos
- [n8n](https://n8n.io) — Automatización del flujo
- Python 3.13

## Configuración

1. Instala la dependencia:
pip install resend

2. Crea una cuenta en resend.com y genera una API Key

3. Configura la variable de entorno:
RESEND_API_KEY=re_tu_key_aqui

## Flujo en n8n

El workflow sigue este orden:

1. **Webhook** — recibe el evento de push del repositorio
2. **HTTP Request** — notifica al bot de Telegram
3. **HTTP Request (Resend)** — envía correo al destinatario vía Resend API

## Uso

```python
from watkidapi import send_pipeline_notification

send_pipeline_notification(
    status="success",
    image_tag="watkit-api:latest",
    health="ok"
)
```

## Workflow en n8n

![Workflow](preview.jpg)
