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

## 🛠 Tools Used

- [Postman](https://www.postman.com/)
- [VS Code](https://code.visualstudio.com/)
- [GitHub](https://github.com/)
- [ReqRes API](https://reqres.in/)
- [JSON Schema](https://json-schema.org/)

---

## 📂 Project Structure

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


---

## 🧪 Test Cases Included

Here is the list of test cases that will be created as part of this project:

### 1. **Basic API Tests**
   - **GET** `/users` – Retrieve a list of users.
   - **GET** `/users/{id}` – Retrieve a single user by ID.
   - **POST** `/users` – Create a new user.
   - **PUT** `/users/{id}` – Update a user by ID.
   - **DELETE** `/users/{id}` – Delete a user by ID.

### 2. **Authentication Tests**
   - **POST** `/login` – Test valid login with credentials.
   - **POST** `/register` – Test valid registration with user details.
   - **GET** `/users` (with valid Bearer token) – Verify that authorized users can retrieve user data.
   - **GET** `/users` (without token) – Ensure that users cannot access the data without a valid token (401 Unauthorized).

### 3. **Negative Tests**
   - **GET** `/users/99999` – Test non-existent user retrieval (404 Not Found).
   - **POST** `/users` (with missing required fields) – Test invalid data submission (422 Unprocessable Entity).
   - **PUT** `/users/{id}` (with invalid data) – Test updating user with invalid data (400 Bad Request).
   - **DELETE** `/users/99999` – Test deleting a non-existent user (404 Not Found).

### 4. **Data Validation Tests**
   - **GET** `/users/{id}` – Verify that the user data returned has correct fields and values (e.g., `id`, `name`, `email`).
   - **POST** `/users` – Ensure the newly created user data matches the request body (e.g., check if the `name` and `job` are correctly returned).
   - **PUT** `/users/{id}` – Ensure the updated data matches the request body after updating a user.

### 5. **Response Status and Time Tests**
   - **GET** `/users` – Verify that the API returns a `200 OK` status.
   - **POST** `/users` – Verify that the API returns a `201 Created` status for successful creation.
   - **PUT** `/users/{id}` – Verify that the API returns a `200 OK` status for successful update.
   - **DELETE** `/users/{id}` – Verify that the API returns a `204 No Content` status for successful deletion.
   - Ensure that the API response time for each endpoint is under 1000ms.

### 6. **JSON Schema Validation**
   - **GET** `/users` – Validate the JSON schema of the response.
   - **GET** `/users/{id}` – Validate the JSON schema of the single user data.
   - **POST** `/users` – Validate the JSON schema of the newly created user data.
   - **PUT** `/users/{id}` – Validate the JSON schema of the updated user data.

### 7. **Error Handling Tests**
   - **GET** `/users/{id}` with incorrect ID – Ensure that the API handles incorrect IDs gracefully and returns a `404` status.
   - **POST** `/users` with missing required fields – Ensure that the API returns a `422` error when required fields are missing.
   - **PUT** `/users/{id}` with invalid data – Ensure that the API returns a `400` error for invalid data submission.

---

## 📝 How to Run the Tests

1. **Install Postman**: If you don’t have Postman installed, download it from [here](https://www.postman.com/downloads/).
2. **Import Collection**: Open Postman and go to `File > Import`, select the `API_Tester.postman_collection.json` file from the `/postman/` directory.
3. **Import Environment**: Import the `API_Tester.environment.json` to configure environment variables like `baseUrl` and `authToken`.
4. **Run the Tests**: Once the collection and environment are set up, you can use the **Collection Runner** in Postman to run all the tests at once.
5. **View Results**: Check the `Tests` tab for individual test results and the overall summary.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
© Adam Fedorowicz