## Test Setup

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
