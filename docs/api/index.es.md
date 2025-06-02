# Uso de la API
## API key
Para hacer uso correcto de la API se necesita crear una API key desde el [dashboard de WavyNode](https://wavynode.com/dashboard) y agregarlo a cada request que se haga por medio del parámetro `apiKey`.
Por ejemplo:
```bash
curl https://api.wavynode.com/v1/chains?apiKey={you-api-key}
```

## Hacer una petición
* Endpoint base: `https://api.wavynode.com`
* Autenticación: Parámetro `apiKey`

### Formato de respuesta
| Campo | Tipo | Opcional | 
|-------|------|----------|
| `success` | booleano | no |
| `data` | any | si |
| `message` | string | si |
