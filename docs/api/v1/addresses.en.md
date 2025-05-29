# Addresses  
Allows you to configure relevant on-chain addresses.

!!! info

    Relevant addresses are those for which compliance notifications and alerts about interactions with malicious addresses will be sent to the configured webhook.

## All addresses  
* **Description**: Retrieves all the user's addresses.  
* **Endpoint**: `/v1/addresses`  
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
                    "address": "0x...",
                    "description": "My first relevant address"
                }
            ]
        }
        ```

## Create new relevant address  
* **Description**: Creates a new relevant address to listen for events.  
* **Endpoint**: `/v1/addresses`  
* **Method**: POST  
* **Request:**  
    * **Query params:**  
        * `apiKey` (required): Your API key  
    * **Body:** (JSON)  
        ```json
        {
            "address": "0x<your-address>",
            "description": "Some description here"
        }
        ```
* **Response:**  
    ```json 
    {
        "success": true
    }
    ```

## Delete an address  
* **Description**: Removes a relevant address from the user's relevant address list.  
* **Endpoint**: `/v1/addresses/{addressId}`  
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
