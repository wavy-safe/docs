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
    "id": 0,
    "userId": "user-id",
    "chainId": 42161,
    "txHash": "0xsome-tx-hash",
    "address": {
        "id": 0
        "address": "0xyour-address-involved",
        "description": "Your address' description"
    },
    "amount": {
        "token": 0.001,
        "usd": 1.6323
    },
    "token": {
        "address": null,
        "decimals": 18,
        "name": "ETH",
        "symbol": "ETH",
    },
    "timestamp": "2025-04-15T00:03:01.000Z",
    "inflictedLaws": [
        {
            "country": "mexico",
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
```
