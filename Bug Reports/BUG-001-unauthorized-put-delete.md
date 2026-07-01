# BUG-001: Unauthenticated Users Can Modify/Delete Properties

**Severity:** High  
**Status:** Open  
**Reported:** 05/2026

| Description | PUT and DELETE endpoints do not require authentication. Any user without a valid JWT token can modify or delete properties. |
| Steps to Reproduce | 1. Send PUT /properties/:id with valid body — no Authorization header 2. Send DELETE /properties/:id — no Authorization header |
| Expected Result | 401 Unauthorized |
| Actual Result | 200 OK — operation executes successfully |
| Impact | Data integrity risk — any anonymous user can alter or destroy property records. |
