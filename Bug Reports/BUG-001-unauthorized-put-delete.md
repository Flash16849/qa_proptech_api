# BUG-001: Unauthenticated Users Can Add/Modify/Delete Properties

**Severity:** Major  
**Priority:** High  
**Status:** Open  
**Reported:** 10/2026

| Field | Detail |
|---|---|
| **Description** | POST, PUT and DELETE endpoints do not require authentication. Any user without a valid JWT token can modify or delete properties. |
| **Steps to Reproduce** | 1. Send POST /properties with valid body — no Authorization header <br> 2. Send PUT /properties/:id with valid body — no Authorization header <br> 3. Send DELETE /properties/:id — no Authorization header |
| **Expected Result** | 401 Unauthorized |
| **Actual Result** | 200 OK — operation executes successfully |
| **Impact** | Data integrity risk — any anonymous user can alter or destroy property records. |
