# Notificaciones
Wavy Node ofrece la posibilidad de alertar acerca de actividades irregulares o normas infligidas por medio de webhooks.

## Quickstart
1. Configura la url de tu webhook en el [dashboard de Wavy Node](https://wavynode.com/dashboard).
2. Define tus direcciones relevantes por medio del dashboard o [usando la api](/api/v1/addresses)
3. Crea un servidor web que escuche, en esa url, las notificaciones de nuestro servicio de notificaciones.
4. Responder con un status code `200` para marcar esa notificación como entregada. 

## Diagrama de secuencia 
![[Diagrama de notificaciones]](/img/notificationsDiagram.png)

## Payload
```json 
{
    "txHash": "some-tx-hash",
    "chainId": 42161,
    "address": {
        "address": "0xyour-address-involved",
        "description": "Your address' description"
    },
    "inflictedLaws": {
        "mexico": [
            {
                "name": "The name of the law inflicted",
                "risk": "warn",
                "description": "Description of the law",
                "source": "Source of the law"
            },
            {
                ...
            }
        ]
    }
}
```

## Estructuras de datos
```typescript 
// typescript
interface InflictedLaws {
    [country: string]: Law[] 
}

interface Law {
    name: string,
    description: string,
    source?: string,
    risk: 'warn' | 'illegal',
}
```
