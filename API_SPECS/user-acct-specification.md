# openAPI Specification Template

## General Information

- Title: User Account
- Description: User Account API specification outlines all that allows user to
  maintain a User account.

## Servers

- URL: http://localhost:8080/v1
- Description: development/staging server

## Security

- Type: http
- Name: BearerAuth
- Schema: bearer
- bearerFormat: JWT

<!-- Define Paths -->

<!-- Start Retrieve all -->

## Path Retrieve all

- Name: users
- HTTP operation: get
- Summary: Retrieve all users
- Security: BearerAuth

### Response body definitions

- Status code: 200
- Status messages: OK
- Content type: application/json
- Schema: array{id, email}

<!-- note on schema: note that one of the parameters, 'user' i
  parametrized. // this gives us link to individual user account -->

---

- Status code: 401
- Status messages: Unauthorized
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
  <!-- End Retrieve All -->
  <!-- Start Create new user account -->

## Path Create a new

- Name: **user**
- HTTP operation: post
- Summary: Create a new user
- Security: BearerAuth

<!-- bc we created sth, should send that data back! -->

### Request body definitions

- Content type: application/json
- Required: all
- Schema: email and password

### Response body definitions

- Status code: 201
- Status messages: CREATED
- Content type: application/json
- Schema:id, email

---

<!-- Because Requests can be malformed in someway -->

- Status code: 400
- Status messages: Bad request // send malformed, incorrect, or incomplete info
- Content type: application/json
- Schema: code_error, message

---

- Status code: 401
- Status messages: Unauthorized
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
<!-- End Create New User-->

---

<!-- Start Retrieve user by ID -->

## Path Retrieve one user

- Name: user/{id}
- HTTP operation: get
- Summary: Get a user by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Response body definitions

- Status code: 200
- Status messages: OK
- Content type: application/json
- Schema: id, email

---

- Status code: 401
- Status messages: Unauthorized
- Content type: application/json
- Schema: code_error, message

---

- Status code: 404
- Status messages: Not Found
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
<!-- End Retrieve user by ID -->

<!-- Start Create new user account -->

## Path Create a new

- Name: **user**
- HTTP operation: post
- Summary
- Security: BearerAuth

<!-- bc we created sth, should send that data back! -->

### Request body definitions

- Content type: application/json
- Required: all
- Schema: id, firstName, lastName, dob, gender, phoneNumber and user(id, email)

### Response body definitions

- Status code: 200
- Status messages: OK
- Content type: application/json
- Schema:id, firstName, lastName, dob, gender, phoneNumber and user(id, email)

---

<!-- Because Requests can be malformed in someway -->

- Status code: 400
- Status messages: Bad request // send malformed, incorrect, or incomplete info
- Content type: application/json
- Schema: code_error, message

---

- Status code: 401
- Status messages: Unauthorized
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
<!-- End Create New User-->

---

<!-- Start Update User by ID -->

## Path Update one user by ID

- Name: user/{id}
- HTTP operation: put
- Summary: Update a user by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Request body definition

<!-- Copied from 'create user' -->

- Content type: application/json
- Required: all
- Schema: email, password

### Response body definition

- Status code: 202
- Status messages: ACCEPTED
- Content type: application/json
- Schema:id, email

---

<!-- Because Requests can be malformed, incorrect, incomplete, etc -->

- Status code: 404
- Status messages: Not Found
- Content type: application/json
- Schema: code_error, message

---

- Status code: 400
- Status messages: Bad request
- Content type: application/json
- Schema: code_error, message

---

- Status code: 401
- Status messages: Unauthorized
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
<!-- End Update User by ID -->

<!-- Delete User by ID -->

## Path Delete one user by ID

- Name: user/{id}
- HTTP operation: delete
- Summary: delete a user by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Response body definition

- Status code: 204
- Status messages: NO CONTENT
- Content type: none
- Schema: none

---

<!-- Because Requests can be malformed, incorrect, incomplete, etc -->

- Status code: 404
- Status messages: Not Found
- Content type: application/json
- Schema: code_error, message

---

<!-- No request so no Bad requests -->
<!-- - Status code: 400
- Status messages: Bad request
- Content type: application/json
- Schema: code_error, message

--- -->

- Status code: 401
- Status messages: Unauthorized
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
<!-- End Delete User by ID -->
