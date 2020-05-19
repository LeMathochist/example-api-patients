# patient-growth-spec

## General Information

- Title: Report Progress-Patient
- Description: Report Progress API specification outlines all that allows
  patient progress data to be accessed and retrieved.

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

## Path

- Name: patient/{id}/prgress
- HTTP operation: get
- Summary: Get all progress by patient ID
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

- Status code: 404
- Status messages: Not Found
- Content type: application/json
- Schema: code_error, message

---

- Status code: 500
- Status messages: Server error
- Content type: application/json
- Schema: code_error, message
  <!-- End Retrieve All progress by patient ID -->
  