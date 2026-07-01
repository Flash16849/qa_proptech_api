# PropTech API Test Suite

API test suite for a Node.js + Express + MongoDB PropTech REST API, built with Postman. Covers CRUD operations, authentication flows, status code validation, and edge cases.

## Tech Stack

- **Tool:** Postman
- **API:** Node.js, Express, MongoDB
- **Auth:** JWT

## Test Coverage

### Properties

| # | Method | Endpoint | Scenario | Expected Status |
|---|--------|----------|----------|-----------------|
| 1 | GET | /properties | Get all properties | 200 |
| 2 | GET | /properties/:id | Valid ID | 200 |
| 3 | GET | /properties/:id | ID not found in DB | 404 |
| 4 | GET | /properties/:id | Malformed ID format | 400 |
| 5 | GET | /properties?tags= | Filter by tag | 200 |
| 6 | GET | /properties?minPrice=500&maxPrice=200 | minPrice > maxPrice | 400 |
| 7 | POST | /properties | Valid body | 201 |
| 8 | POST | /properties | Missing required fields | 400 |
| 9 | PUT | /properties/:id | Valid update | 200 |
| 10 | PUT | /properties/:id | ID not found in DB | 404 |
| 11 | PUT | /properties/:id | Malformed ID format | 400 |
| 12 | DELETE | /properties/:id | Valid ID | 200 |
| 13 | DELETE | /properties/:id | ID not found in DB | 404 |
| 14 | DELETE | /properties/:id | Malformed ID format | 400 |
| 15 | DELETE | /properties | Delete all | 200 |

### Auth

| # | Method | Endpoint | Scenario | Expected Status |
|---|--------|----------|----------|-----------------|
| 16 | POST | /auth/register | Valid registration | 201 |
| 17 | POST | /auth/register | Missing required fields | 400 |
| 18 | POST | /auth/register | Email already exists | 409 |
| 19 | POST | /auth/login | Valid credentials | 200 |
| 20 | POST | /auth/login | Missing email/password | 400 |
| 21 | POST | /auth/login | Wrong credentials | 401 |
| 22 | GET | /auth | Get all users | 200 |

## Setup

1. Import `PropTech.postman_collection.json` into Postman
2. Create a new environment with the following variables (leave empty — auto-set during collection run):

| Variable | Description |
|----------|-------------|
| `propID` | Set after POST create property |
| `tag` | Set after POST create property |
| `token` | Set after POST login |
| `testEmail` | Set after POST register |

3. Run the collection **in order from top to bottom**. Some test cases depend on the result of previous requests.

Recommended run order:
### Properties
1. POST - Create Property - 400 Bad Request
2. POST - Create Property - 201 Created
3. GET - Get All Properties - 200 OK
4. GET - Get Property By ID - 200 OK
5. PUT - Update Property - 200 OK
6. PUT - Update Property - 400 Bad Request
7. GET - Get Property By ID - 400 Bad Request
8. GET - Get Properties With Filter - 200 OK
9. GET - Get Properties With Filter - 400 Bad Request
10. DELETE - Delete Property By ID - 200 OK
11. GET - Get Property By ID - 404 Not Found
12. PUT - Update Property - 404 Not Found
13. DELETE - Delete Property By ID - 404 Not Found
14. DELETE - Delete Property By ID - 400 Bad Request
15. DELETE - Delete All Property - 200 OK

### Auth
1. POST - Register - 201 Created
2. POST - Register - 400 Bad Request
3. POST - Register - 409 Conflict Data
4. POST - Login - 200 OK
5. POST - Login - 400 Bad Request
6. POST - Login - 401 Invalid Credentials
7. GET - Get All Users - 200 OK

## Notes

- POST create property uses a pre-request script to randomize data (name, price, tags) on each run
- Register 409 automatically reuses the email from Register 201 to test duplicate detection
- PUT 200 verifies that data was actually updated correctly, not just the status code
