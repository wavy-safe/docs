# API Usage

## API Key

To properly use the API, you need to create an API key from the [WavyNode dashboard](https://wavynode.com/dashboard) and include it in every request using the `apiKey` parameter.

For example:

```bash
curl https://api.wavynode.com/v1/chains?apiKey={you-api-key}
```
## Make a request
* Endpoint base: `https://api.wavynode.com`
* Authentication: `apiKey` parameter

### Formato de respuesta
| Campo | Tipo | Opcional | 
|-------|------|----------|
| `success` | boolean | no |
| `data` | any | yes |
| `message` | string | yes |