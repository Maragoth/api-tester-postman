# 🛠️ API Tester – Postman Project

![Run API Tests (Postman + Newman)](https://github.com/Maragoth/api-tester-postman/actions/workflows/run-api-tests.yml/badge.svg)  
![Tests](https://img.shields.io/badge/tests-47-green)  
![Last Commit](https://img.shields.io/github/last-commit/Maragoth/api-tester-postman?style=flat)  
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Cross--Platform-lightgrey)![License](https://img.shields.io/badge/license-MIT-blue.svg)  


## 🔧 Project Overview

This project is created from scratch as part of a **QA Automation portfolio**. It focuses on **API testing** using Postman to simulate real-world API testing scenarios for a typical backend system. The goal is to ensure that the API behaves as expected under different conditions, including both positive and negative test cases.

✅ All tests are designed to be 100% effective — they not only pass when the API works correctly but also reliably detect bugs and unexpected behavior.

---

## 🔑 Features

- **Created from scratch** with real-world testing scenarios in mind.
- Testing of common HTTP methods: **GET, POST, PUT, DELETE**.
- Testing of **authentication** and **authorization** (Bearer tokens).
- **Negative testing** to check for edge cases (e.g. 404, 401, 422).
- **JSON Schema validation** to ensure the response format is correct.
- Testing of common API **error scenarios**.
- **Data validation** to ensure correct parsing and structure.
- Comprehensive **documentation** of the testing process.

---

## ⛔️ Known API Behavior

⛔️ BUG DETECTED: POST /products/add accepts empty request bodies and still returns HTTP 201 with a new ID.

This issue was discovered and reported during execution of the negative test case: "Add Product with Missing Fields".

The response did not return the expected validation error, which indicates a backend issue.

✅This confirms the effectiveness of the test suite in identifying real-world issues.

## 🛠 Tools Used

- [Postman](https://www.postman.com/) – for creating and running API requests and tests
- [VS Code](https://code.visualstudio.com/) – for editing documentation and managing files
- [GitHub](https://github.com/) – for version control and portfolio hosting
- [DummyJSON API](https://dummyjson.com) – as the target public REST API for testing
- [JSON Schema](https://json-schema.org/) – for validating API response structure

---

## 📂 Project Structure

```plaintext
api-tester-postman/
├── .github/
│   └── workflows/
│       └── run-api-tests.yml
├── .vscode/
│   └── settings.json
├── docs/
│   ├── results/
│   └── screenshots/
│       └── API_TESTER_POSTMAN_RESULTS.png
├── json-schemas/
│   ├── addProduct.schema.json
│   ├── deletedProduct.schema.json
│   ├── product.schema.json
│   ├── productList.schema.json
│   ├── productNotFound.schema.json
│   ├── updateproduct.schema.json
│   ├── user.schema.json
│   ├── userList.schema.json
│   └── userNotFound.schema.json
├── postman/
│   ├── API_Tester.environment.json
│   └── API_Tester.postman_collection.json
├── LICENSE
├── README.md
├── TestPlan.md
└── TestSummary.md
```

---

## 🔍 Test Cases Included

Here is the list of test cases that will be created as part of this project:

### 1. **Basic API Tests**
   - **GET** `/users` – Retrieve a list of users.
   - **GET** `/users/{id}` – Retrieve a single user by ID.
   - **POST** `/auth/login` – Perform login and receive a token.
   - **GET** `/products` – Retrieve a list of products.
   - **GET** `/products/{id}` – Retrieve a single product by ID.
   - **POST** `/products/add` – Create a new product.
   - **PUT** `/products/{id}` – Update an existing product.
   - **DELETE** `/products/{id}` – Delete a product.

### 2. **Authentication Tests**
   - **POST** `/auth/login` – Test valid login with credentials.
   - **POST** `/auth/login` (invalid password) – Ensure login fails with incorrect credentials.
   - **GET** `/users` (with token) – Verify token-based access (if token is implemented).
   - **GET** `/users` (without token) – Validate access control (if required).
   - **POST** `/auth/refresh` – Test access token renewal using a valid refresh token.

### 3. **Negative Tests**
   - **GET** `/users/99999` – Non-existent user (404 Not Found).
   - **GET** `/products/99999` – Non-existent product (404 Not Found).
   - **POST** `/products/add` (missing required fields) – Invalid creation (400 or 422).
   - **PUT** `/products/{id}` (invalid data) – Invalid update (400).

### 4. **Data Validation Tests**
   - **GET** `/users/{id}` – Validate user fields (`id`, `firstName`, `email`, etc.).
   - **GET** `/products/{id}` – Validate product structure and fields.
   - **POST** `/products/add` – Ensure created product matches submitted data.
   - **PUT** `/products/{id}` – Ensure updated product reflects request body.

### 5. **Response Status and Time Tests**
   - **GET** `/users` – Expect `200 OK`.
   - **POST** `/auth/login` – Expect `200 OK`.
   - **POST** `/products/add` – Expect `200 OK` or `201 Created`.
   - **PUT** `/products/{id}` – Expect `200 OK`.
   - **DELETE** `/products/{id}` – Expect `200 OK`.
   - All endpoints should respond within 1000ms.

### 6. **JSON Schema Validation**
   - **GET** `/users/{id}` – Validate response against user schema.
   - **GET** `/products/{id}` – Validate response against product schema.
   - **POST** `/products/add` – Validate creation response schema.
   - **PUT** `/products/{id}` – Validate update response schema.

### 7. **Error Handling Tests**
   - **GET** `/users/{id}` with invalid ID – Expect `404`.
   - **POST** `/auth/login` with wrong credentials – Expect `400` or `401`.
   - **POST** `/products/add` with invalid body – Expect appropriate error response.

### 8. **Token Refresh Tests**
   - **POST** `/auth/refresh` – Should return a new access token and refresh token.
   - Validate status code `200`, accessToken presence, and refreshToken presence.

All included tests are validated and proven to detect both successful and faulty API behaviors. Failures in test reports are not false positives — they are real issues present in the tested API.

---

## 📝 How to Run the Tests

Install Postman: If you don’t have Postman installed, download it from here.

Import Collection: Open Postman and go to File > Import, select the API_Tester.postman_collection.json file from the /postman/ directory.

Import Environment: Import the API_Tester.environment.json to configure environment variables like base_url.

Run the Tests: Once the collection and environment are set up, use the Collection Runner in Postman to execute all tests.

View Results: Check the Tests tab for detailed results.

📁 Additionally, a detailed HTML report is automatically generated via CI and can be downloaded from the GitHub Actions Artifacts tab after every push.

📜 Test run results (e.g. exported .json or .html) are also saved under:docs/results/ – this folder contains saved test results for reference and documentation purposes.

---

## 👤 About Me as QA:

My name is Adam Fedorowicz, a QA Automation Engineer passionate about building real-world testing frameworks using scalable architecture.
I specialize in Selenium, Pytest, API testing (Postman), and CI workflows.
This project is part of my growing QA portfolio, aiming to showcase reliable, clean, and professional test automation.

## 📫 Find Me Online

- 🌐 [LinkedIn – Adam Fedorowicz](https://www.linkedin.com/in/adam-fedorowicz-UK)
- 💻 [GitHub – Maragoth](https://github.com/Maragoth)
- 💼 [Upwork – QA Automation Engineer](https://www.upwork.com/freelancers/~018d6c0e188850f30d?mp_source=share)

## 🛡️ License

This project is open source and available under the [MIT License](LICENSE).
© Adam Fedorowicz
