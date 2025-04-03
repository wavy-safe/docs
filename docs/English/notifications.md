# Notifications

Wavy Node lets you receive alerts about irregular activity or regulatory violations through webhooks.

## Quickstart

1. Set your webhook URL in the [Wavy Node dashboard](https://wavynode.com/dashboard).
2. Add your relevant addresses using the dashboard or [the API](/api/v1/addresses).
3. Create a web server that listens for notifications at that URL.
4. Respond with a `200` status code to confirm the notification was successfully received.

## Sequence Diagram

![[Notifications Diagram]](/img/notificationsDiagram.png)

## Payload
```json 
{
    "id": 1
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