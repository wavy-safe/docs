---
title: API keys
---


# API keys
Gestión de API keys por medio de la API.

!!! warning

    Esta documentación describe la `keys` API, si buscas información acerca de cómo crear una API key desde el dashboard lee [Uso de la API](/api/).

## Todas las direciones
* **Descripción**: Obtiene todas las API keys del usuario.
* **Endpoint**: `/v1/keys`
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
                    "created_at": "2025-01-29T05:12:15+00:00",
                    "label": "Some label",
                    "key": "wavy_...",
                }
            ]
        }
        ```

## Crear API key
* **Descripción**: Crea una API key
* **Endpoint**: `/v1/keys`
* **Método**: POST
* **Request:**
    * **Query params:**
        * `apiKey` (requerido): Tu API key
    * **Body:** (JSON)
        ```json
        {
            "label": "Some label"
        }
        ```
* **Response:**
    ```json 
    {
        "success": true,
        "data": 1 // key id
    }
    ```

## Eliminar una API key
* **Descripción**: Elimina una API key
* **Endpoint**: `/v1/keys/{keyId}`
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
