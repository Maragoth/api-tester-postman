# 📋 Test Plan – API Tester (Postman)

## 1. Project Name
API Tester – Postman Project

## 2. Author
Adam Fedorowicz

## 3. Date
07.05.2025

## 4. Objective
Verify the correct functioning of a REST API using automated tests in Postman. Focus areas include HTTP methods, authentication, negative cases, and response validation (including JSON Schema).

## 5. Scope
- API base: https://dummyjson.com
- Endpoints: /auth/login, /users, /products, /auth/refresh
- Methods: GET, POST, PUT, DELETE
- Coverage: positive, negative, data validation, schema validation

## 6. Out of Scope
- UI testing
- Performance load testing (beyond response time check)

## 7. Test Types
- Functional Testing
- Security (authentication) Testing (login + refresh token mechanism)
- Negative Testing
- Schema Validation (using JSON Schema)

## 8. Tools
- Postman
- Reqres API
- JSON Schema
- Git + GitHub

## 9. Environment Variables
- `base_url`
- `authToken` – access token received after login
- `refreshToken` – token used to renew accessToken
  
## 10. Success Criteria
- All test cases pass as expected
- API responses match expected structure, status codes, and timings
