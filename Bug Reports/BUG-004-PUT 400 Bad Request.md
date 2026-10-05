# BUG-004: [API][PUT] /properties/:id - System returns 200 OK instead of 400 Bad Request when request body is empty

**Severity:** Low  
**Priority:** Low  
**Status:** Open  
**Reported:** 10/2026

| Field | Detail |
|---|---|
| **Description** | PUT /properties System returns 200 OK instead of 400 Bad Request when request body is empty. |
| **Steps to Reproduce** | 1. Open Postman and select the PUT {base_url}/properties/:id request. </br> 2. Ensure the user is fully authenticated. </br> 3. In the Request Body (JSON), write down "{}" as an empty request body. </br> 4. Send the request. |
| **Expected Result** | - Response should return HTTP status 400 Bad Request. </br> - The API should return a clear validation error message (e.g., "Missing required fields"). |
| **Actual Result** | - Response returns HTTP status 200 OK. </br> - The system returns the property object |
