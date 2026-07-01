# BUG-002: No Validation for minPrice Greater Than maxPrice

**Severity:** Low  
**Status:** Fixed  
**Reported:** 05/2026

## Description
GET /properties accepted minPrice > maxPrice without error,
returning empty results silently instead of rejecting the request.

## Steps to Reproduce
1. GET /properties?minPrice=9000&maxPrice=100

## Expected Result
400 Bad Request — "minPrice must be less than maxPrice"

## Actual Result
200 OK — empty data array returned with no error message

## Fix Applied
Added validation check before filter logic in GET handler.