# Wallets
The `wallets` API allows developers and clients to get information about certain wallets, wether they are flagged as malicious or blacklisted somewhere. 

## Status
Checks the status of the given wallet
```bash 
curl https://api.wavynode.com/v1/wallets/{wallet}/status?apiKey={you-api-key}
```
Response:

```json
{
    "success": true,
    "data": {
        "status": "dirty",
        "tags": [
            "tornado"
        ],
        "lastTxs": [],
        "lastDapps": []
    }
}
```
