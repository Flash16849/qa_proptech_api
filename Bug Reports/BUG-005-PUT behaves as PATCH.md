# BUG-005: [API][PUT] /properties/:id - PUT method is behaving as PATCH

**Severity:** Low  
**Priority:** Low  
**Status:** Open  
**Reported:** 10/2026

| Field | Detail |
|---|---|
| **Description** | PUT /properties System return a non-empty value at field "tags" instead of an empty value. |
| **Steps to Reproduce** | 1. Open Postman and select the PUT {base_url}/properties/:id request. </br> 2. Ensure the user is fully authenticated. </br> 3. In the Request Body (JSON), 3. In the Request Body (JSON), write down: </br>{  "name": "Micropachycephalosaurus",</br>   "description": "Et ex possimus aut sit.",</br>  "price": 18438039233,</br>  "location": {</br>    "num": 419,</br>    "street": "Prohaska Ports",</br>    "city": "Reichelton"</br>  },</br>  "type": "Condotel"} </br> without field "tags". </br> 4. Send the request. |
| **Expected Result** | - Response should return HTTP status 200 OK. </br> - The system returns modified property with field "tags" as empty-value. |
| **Actual Result** | - Response returns HTTP status 200 OK. </br> - The system returns the property object with field "tags" unchanged that has a non-empty value |
