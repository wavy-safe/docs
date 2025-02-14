# Addresses
Permite configurar las direcciones en cadena relevantes.

!!! info 

    Las direcciones relevantes son aquellas por las que se enviarán notificaciones de compliance con las legislaciones y alertas de interacciones con direcciones maliciosas al webhook configurado.

## Todas las direciones
* **Descripción**: Obtiene todas las direcciones del usuario.
* **Endpoint**: `/v1/addresses`
* **Método**: GET
* **Request:**
    * **Query params:**
        * `apiKey` (requerido): Tu API key
* **Response:**
    * **Body:** (JSON)
        ```json
        {
            "success": true,
            "data": [
                {
                    "id": 1,
                    "address": "0x...",
                    "description": "My first relevant address"
                },
            ]
        }
        ```

## Crear nueva dirección relevante
* **Descripción**: Crea una nueva dirección relevante para la cual escuchar eventos.
* **Endpoint**: `/v1/addresses`
* **Método**: POST
* **Request:**
    * **Query params:**
        * `apiKey` (requerido): Tu API key
    * **Body:** (JSON)
        ```json
        {
            "address": "0x<your-address>",
            "description": "Some description here",
        }
        ```
* **Response:**
    ```json 
    {
        "success": true
    }
    ```

## Eliminar una dirección
* **Descripción**: Remueve una dirección relevante de la lista de direcciones relevantes del usuario.
* **Endpoint**: `/v1/addresses/{addressId}`
* **Método**: DELETE
* **Request:**
    * **Query params:**
        * `apiKey` (requerido): Tu API key
* **Response:**
    ```json 
    {
        "success": true
    }
    ```
