# Notificaciones
Wavy Node ofrece la posibilidad de alertar acerca de actividades irregulares o normas infligidas por medio de webhooks.

## Quickstart
1. Configura la url de tu webhook en el [dashboard de Wavy Node](https://wavynode.com/dashboard).
2. Crea un servidor web que escuche, en esa url, las notificaciones de nuestro servicio de notificaciones.
3. Responder con un status code `200` para marcar esa notificación como entregada. 

## Diagrama de notificaciones

## Payload
```json 
{
    "txHash": "some-tx-hash",
    "chainId": 42161,
    "inflictedLaws": Law[],
}
```
```typescript title="Estructura de datos"
interface Law {
    name: string,
    description: string,
    source?: string,
    risk: 'warn' | 'illegal',
}
```
