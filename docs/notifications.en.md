# Notifications

Wavy Node lets you receive alerts about irregular activity or regulatory violations through webhooks.

## Quickstart

1. Set your webhook URL in the [Wavy Node dashboard](https://wavynode.com/dashboard).
2. Add your relevant addresses using the dashboard or [the API](/api/v1/addresses).
3. Create a web server that listens for notifications at that URL.
4. Respond with a `200` status code to confirm the notification was successfully received.

## Security

To ensure the authenticity and integrity of notifications sent by Wavy Node, we utilize HMAC (Hash-based Message Authentication Code). This method allows you to verify that each notification genuinely originates from our service and has not been tampered with during transmission. It works by combining a secret key (known only by Wavy Node and you, and created when you set up a webhook in our dashboard) with the notification message. This combination is then processed through a cryptographic hash function to generate a unique signature.

When you receive a notification from Wavy Node, it will include the HMAC signature in a header. Your server can then use the same secret key and hash function to calculate its own signature from the received message. If both signatures match, you can be confident that the notification is from Wavy Node and that its contents are unaltered. This safeguards against impersonation and data manipulation.

We use the `txHash` as the message to be signed; this can be found in the notification payload (body). The signature itself will be in the `x-wavynode-hmac` header.

Here's an example of the hashing function for Node.js:
```typescript 
import { createHmac } from 'node:crypto'

const createHmacSignature = (message: string, secret: string): string => {
	const hmac = createHmac('sha256', secret)
	hmac.update(message)

	return hmac.digest('base64')
}
```

## Sequence Diagram

![[Notifications Diagram]](/img/notificationsDiagramEn.png)

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

## Data Structures
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
