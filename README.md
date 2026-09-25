# RestfulBookerPostmanAPI
Automated API testing framework for Restful Booker API using Postman, Newman, and Jenkins CI/CD integration with Newman HTML Extra reporting.
# Restful Booker API Automation Framework

An end-to-end REST API automated testing framework for the [Restful Booker](https://restful-booker.herokuapp.com) application using **Postman**, **Newman CLI**, and **Jenkins CI/CD**.

---

## Features

- **CRUD Operations Tested**:
  - `GET /booking` (Fetch booking IDs)
  - `POST /booking` (Create new booking & dynamically extract `b_id`)
  - `GET /booking/:id` (Verify created booking details)
  - `POST /auth` (Generate authentication token & extract `b_token`)
  - `PUT /booking/:id` (Update booking with token authorization)
  - `DELETE /booking/:id` (Delete booking record)
- **Positive & Negative Test Coverage**: Includes status code validations (`200`, `201`, `400`, `404`), schema structure, and response time checks.
- **Dynamic Variable Chaining**: Passes data dynamically between requests (`b_id`, `b_token`) across environment scopes.
- **Reporting**: Detailed HTML execution reports generated using `newman-reporter-htmlextra`.
- **CI/CD Integrated**: Configured to run automatically in Jenkins.

---

## Prerequisites

- [Node.js](https://nodejs.org/) (v16.x or later)
- [npm](https://www.npmjs.com/)
- [Newman CLI](https://www.npmjs.com/package/newman)
- [Newman HTML Extra Reporter](https://www.npmjs.com/package/newman-reporter-htmlextra)

---

## Installation

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/MaheshH91/RestfulBookerPostmanAPI.git](https://github.com/MaheshH91/RestfulBookerPostmanAPI.git)
   cd RestfulBookerPostmanAPI
