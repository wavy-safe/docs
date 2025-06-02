# Notificaciones
Wavy Node ofrece la posibilidad de alertar acerca de actividades irregulares o normas infligidas por medio de webhooks.

## Quickstart

1. Configura la url de tu webhook en el [dashboard de Wavy Node](https://wavynode.com/dashboard).
2. Define tus direcciones relevantes por medio del dashboard o [usando la api](/api/v1/addresses)
3. Crea un servidor web que escuche, en esa url, las notificaciones de nuestro servicio de notificaciones.
4. Responder con un status code `200` para marcar esa notificación como entregada. 

## Seguridad

Para asegurar la autenticidad e integridad de las notificaciones enviadas por Wavy Node, empleamos HMAC (Hash-based Message Authentication Code). Este método le permite verificar que cada notificación proviene genuinamente de nuestro servicio y que no ha sido alterada durante la transmisión. Funciona mediante la combinación de una clave secreta (conocida solo por Wavy Node y usted y creada al momento de crear un webhook en nuestro dashboard) con el mensaje de notificación. Esta combinación se procesa a través de una función hash criptográfica para generar una firma única.

Cuando recibe una notificación de Wavy Node, esta incluirá la firma HMAC en un encabezado. Su servidor puede entonces usar la misma clave secreta y función hash para calcular su propia firma a partir del mensaje recibido. Si ambas firmas coinciden, puede estar seguro de que la notificación proviene de Wavy Node y que no ha sido alterada durante la transmisión. Esto protege contra la suplantación de identidad y la manipulación de datos.

Usamos el `txHash` como mensaje a firmar, éste puede ser encontrado en el payload de la notificación (body), mientras que la firma puede ser encontrada en el header `x-wavynode-hmac`.

Este es un ejemplo de la función de hash para Node.js
```typescript 
import { createHmac } from 'node:crypto'

const createHmacSignature = (message: string, secret: string): string => {
	const hmac = createHmac('sha256', secret)
	hmac.update(message)

	return hmac.digest('base64')
}
```

## Diagrama de secuencia 
![[Diagrama de notificaciones]](/img/notificationsDiagram.png)

## Payload
```json 
{
    "id": 1,
    "txHash": "some-tx-hash",
    "chainId": 42161,
    "address": {
        "id": 543,
        "address": "0xyour-address-involved",
        "description": "Your address' description"
    },
    "inflictedLaws": [
        {
            "country": "mexico",
            "name": "The name of the law inflicted",
            "description": "Description of the law",
            "risk": "warn",
            "source": "Source of the law",
        },
        {
            ...
        }
    ]
}
```

## Estructuras de datos
```typescript 
// typescript
interface ILaw {
    country: string,
    name: string,
    description: string,
    risk: 'warn' | 'illegal',
    source?: string,
}
```
