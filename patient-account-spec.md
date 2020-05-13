# openAPI Specification Template

## General Information

- Title: Patient Account
- Description: Patient Account specification should outline all that allows user
  to maintain a patient account.

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

- Name: patient
- HTTP operation: get
- Summary: Retrieve all patient
- Security: BearerAuth

### Response body definitions

- Status code: 200
- Status messages: OK
- Content type: application/json
- Schema: array{id, firstName, lastName, dob, gender, phoneNumber and user(id,
  email)}

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

<!-- Start Retrieve patient by ID -->

## Path Retrieve one patient

- Name: patient/{id}
- HTTP operation: get
- Summary: Get a patient by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Response body definitions

- Status code: 201 // ReST specs say use 201
- Status messages: OK
- Content type: application/json
- Schema:id, firstName, lastName, dob, gender, phoneNumber and user(id, email)
<!-- End Retrieve patient by ID -->

<!-- Start Create new patient account -->

## Path Create a new

- Name: **patient**
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
<!-- End Retrieve all -->

---

<!-- Start Update Patient by ID -->

## Path Update one patient by ID

- Name: patient/{id}
- HTTP operation: put
- Summary: Update a patient by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Request body definition

<!-- Copied from 'create patient' -->

- Content type: application/json
- Required: all
- Schema: firstName, lastName, dob, gender, phoneNumber and user(id, email)

### Response body definition

- Status code: 202
- Status messages: ACCEPTED
- Content type: application/json
- Schema:id, firstName, lastName, dob, gender, phoneNumber and user(id, email)

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
<!-- End Update Patient by ID -->

## Path Update one patient by ID

- Name: patient/{id}
- HTTP operation: put
- Summary: Update a patient by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Request body definition

<!-- Copied from 'create patient' -->

- Content type: application/json
- Required: all
- Schema: firstName, lastName, dob, gender, phoneNumber and user(id, email)

### Response body definition

- Status code: 202
- Status messages: ACCEPTED
- Content type: application/json
- Schema:id, firstName, lastName, dob, gender, phoneNumber and user(id, email)

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
<!-- End Update Patient by ID -->

<!-- Delete Patient by ID -->

## Path Delete one patient by ID

- Name: patient/{id}
- HTTP operation: delete
- Summary: delete a patient by ID
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
<!-- End Delete Patient by ID -->
