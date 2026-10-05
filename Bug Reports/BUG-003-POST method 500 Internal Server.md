# BUG-003: [API][POST] /properties - System returns 500 Internal Server Error when "price" field is a non-convertible string

**Severity:** Major  
**Priority:** Medium  
**Status:** Fixed  
**Reported:** 10/2026

| Field | Detail |
|---|---|
| **Description** | POST /properties System returns 500 Internal Server Error when "price" field is a non-convertible string (e.g., "1500abc"). |
| **Steps to Reproduce** | 1. Open Postman and select the POST {base_url}/properties request. </br> 2. Ensure the user is fully authenticated. </br> 3. In the Request Body (JSON), modify the "price" field from a number to a non-convertible string (e.g., "price": "1500abc"). </br> 4. Send the request. |
| **Expected Result** | - Response should return HTTP status 400 Bad Request. </br> - The API should return a clear validation error message (e.g., "price must be a valid number"). |
| **Actual Result** | - Response returns HTTP status 500 Internal Server Error. </br> - The server fails to handle the data type mismatch, causing a potential application crash (or unhandled exception). |
