# openAPI Specification Template

## General Information

- Title: Authentication
- Description: Authentication API specification outlines all that allows
  user to access an account.

## Servers

- URL: http://localhost:8080/v1
- Description: development/staging server

<!-- ## Security -->
<!-- No security in this layer? -->
<!-- - Type: http
- Name: BearerAuth
- Schema: bearer
- bearerFormat: JWT -->

<!-- Define Paths -->

<!-- Start Retrieve all -->

## Path login
<!-- Defines the path to login to the app -->
- Name: login
- HTTP operation: post
- Summary: User Authentication
- Security: none

### Request body definitions

- Content type: application/json
- Required: all
- Schema: email and password

### Response body definitions

- Status code: 201
- Status messages: Accepted
- Content type: application/json
- Schema: scope, expires_in, refresh_token, access_token, developer_email

<!-- note on schema: note that one of the parameters, 'progress' is
  parametrized. // this gives us link to individual progress account -->

---

- Status code: 400
- Status messages: Bad request
- Content type: application/json
- Schema: code_error, message

---

- Status code: 404
- Status messages: Not found
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
<!-- End login -->
