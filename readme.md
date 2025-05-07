# 🧪 API Tester – Postman Project

## 🔧 Project Overview

This project is created from scratch as part of a **QA Automation portfolio**. It focuses on **API testing** using Postman to simulate real-world API testing scenarios for a typical backend system. The goal is to ensure that the API behaves as expected under different conditions, including both positive and negative test cases.

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

---

## ⚠️ Known API Behavior

- POST /products/add accepts empty request bodies and still returns HTTP 201 with a new ID. This seems to be a backend validation issue and was discovered during testing.

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
├── README.md
├── TestPlan.md
├── TestSummary.md
├── postman/
│ ├── API_Tester.postman_collection.json
│ └── API_Tester.environment.json
├── json-schemas/
│ └── *.json
├── docs/screenshots/
└── .vscode/
└── settings.json
```

---

## 🧪 Test Cases Included

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


---

## 📝 How to Run the Tests

1. **Install Postman**: If you don’t have Postman installed, download it from [here](https://www.postman.com/downloads/).
2. **Import Collection**: Open Postman and go to `File > Import`, select the `API_Tester.postman_collection.json` file from the `/postman/` directory.
3. **Import Environment**: Import the `API_Tester.environment.json` to configure environment variables like `base_url`.
4. **Run the Tests**: Once the collection and environment are set up, use the **Collection Runner** in Postman to execute all tests.
5. **View Results**: Check the `Tests` tab for detailed results.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
© Adam Fedorowicz