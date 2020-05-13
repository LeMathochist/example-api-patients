# openAPI Specification Template

## General Information

- Title: Progress Account
- Description: Progress Account API specification outlines all that allows
  patient progress to be followed in a Progress account.

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

- Name: progress-all
- HTTP operation: get
- Summary: Retrieve all progress accounts
- Security: BearerAuth

### Response body definitions

- Status code: 200
- Status messages: OK
- Content type: application/json
- Schema: array{id, dateProgress, headCircumference, height, weight and
  patient(id, firstName, lastName, dob, gender, phoneNumber)}

<!-- note on schema: note that one of the parameters, 'progress' is
  parametrized. // this gives us link to individual progress account -->

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
  <!-- Start Create new progress account -->

## Path Create a new

- Name: **progress**
- HTTP operation: post
- Summary: Create a new progress
- Security: BearerAuth

<!-- bc we created sth, should send that data back! -->

### Request body definitions

- Content type: application/json
- Required: all
- Schema: dateProgress, headCircumference, height, weight and patient(id,
  firstName, lastName, dob, gender, phoneNumber)

### Response body definitions

- Status code: 201
- Status messages: CREATED
- Content type: application/json
- Schema: id, dateProgress, headCircumference, height, weight and patient(id,
  firstName, lastName, dob, gender, phoneNumber)

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
<!-- End Create New Progress-->

---

<!-- Start Retrieve progress by ID -->

## Path Retrieve one progress

- Name: progress/{id}
- HTTP operation: get
- Summary: Get a progress by ID
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
- Schema: id, dateProgress, headCircumference, height, weight and patient(id,
  firstName, lastName, dob, gender, phoneNumber)

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
<!-- End Retrieve progress by ID -->

<!-- Start Create new progress account -->

## Path Create a new

- Name: **progress**
- HTTP operation: post
- Summary
- Security: BearerAuth

<!-- bc we created sth, should send that data back! -->

### Request body definitions

- Content type: application/json
- Required: all
- Schema: id, firstName, lastName, dob, gender, phoneNumber and progress(id,
  email)

### Response body definitions

- Status code: 200
- Status messages: OK
- Content type: application/json
- Schema:id, firstName, lastName, dob, gender, phoneNumber and progress(id,
  email)

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
<!-- End Create New Progress-->

---

<!-- Start Update Progress by ID -->

## Path Update one progress by ID

- Name: progress/{id}
- HTTP operation: put
- Summary: Update a progress by ID
- Security: BearerAuth

### Parameters definitions

- Name: id
- Where: path
- Required: true
- Schema: integer

### Request body definition

<!-- Copied from 'create progress' -->

- Content type: application/json
- Required: all
- Schema: firstName, lastName, dob, gender, phoneNumber and progress(id, email)

### Response body definition

- Status code: 202
- Status messages: ACCEPTED
- Content type: application/json
- Schema: firstName, lastName, dob, gender, phoneNumber and progress(id, email)

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
<!-- End Update Progress by ID -->

<!-- Delete Progress by ID -->

## Path Delete one progress by ID

- Name: progress/{id}
- HTTP operation: delete
- Summary: delete a progress by ID
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
<!-- End Delete Progress by ID -->
