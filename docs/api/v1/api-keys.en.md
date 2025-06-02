---
title: API keys
---

# API keys  
API key management through the API.

!!! warning

    This documentation describes the `keys` API. If you're looking for information on how to create an API key from the dashboard, read [Using the API](/en/api).

## All keys  
* **Description**: Retrieves all the user's API keys.  
* **Endpoint**: `/v1/keys`  
* **Method**: GET  
* **Request:**  
    * **Query params:**  
        * `apiKey` (required): Your API key  
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
                    "key": "wavy_..."
                }
            ]
        }
        ```

## Create API key  
* **Description**: Creates an API key  
* **Endpoint**: `/v1/keys`  
* **Method**: POST  
* **Request:**  
    * **Query params:**  
        * `apiKey` (required): Your API key  
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
        "data": 1
    }
    ```

## Delete an API key  
* **Description**: Deletes an API key  
* **Endpoint**: `/v1/keys/{keyId}`  
* **Method**: DELETE  
* **Request:**  
    * **Query params:**  
        * `apiKey` (required): Your API key  
* **Response:**  
    ```json 
    {
        "success": true
    }
    ```
