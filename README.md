# Restful Booker API Automation Framework

![Postman](https://img.shields.io/badge/Postman-API%20Testing-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-CLI%20Runner-00A86B?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-24.x-339933?style=for-the-badge&logo=node.js&logoColor=white)
![npm](https://img.shields.io/badge/npm-Package%20Manager-CB3837?style=for-the-badge&logo=npm&logoColor=white)
![HTML Extra Reporter](https://img.shields.io/badge/HTML%20Extra-Reports-4479A1?style=for-the-badge)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-Pipeline-D24939?style=for-the-badge&logo=jenkins&logoColor=white)

An end-to-end REST API automated testing framework for the [Restful Booker](https://restful-booker.herokuapp.com) application using **Postman**, **Newman CLI**, **GitHub Actions**, and **Jenkins CI/CD**, with HTML execution reports.

---

## 👨‍💻 Maintainer Profile

**Mahesh Holkar** — *Senior Automation Test Engineer (SDET)*

- **LinkedIn:** [maheshholkarqaengineer](https://www.linkedin.com/in/maheshholkarqaengineer/)
- **GitHub:** [MaheshH91](https://github.com/MaheshH91)

---

## 🛠️ Tools & Technologies

| Tool / Technology | Purpose |
| --- | --- |
| **Postman** | API collection design, request chaining, and positive/negative test assertions |
| **Newman CLI** | Headless command-line execution of Postman collections |
| **newman-reporter-htmlextra** | Interactive, styled HTML test report generation |
| **GitHub Actions** | Automated CI workflows, artifact archiving, and configured email notifications |
| **Jenkins CI/CD** | Pipeline execution and report publishing with the HTML Publisher plugin |
| **Node.js & npm** | JavaScript runtime and package/dependency management |

---

## 📌 Framework Features

### Full CRUD and Authentication Testing

- `GET /booking` — retrieve booking IDs
- `POST /booking` — create a booking and extract the dynamic `b_id`
- `GET /booking/:id` — verify created booking properties
- `POST /auth` — generate a security token and extract `b_token`
- `PUT /booking/:id` — update booking details using token authentication
- `DELETE /booking/:id` — delete a booking using token authorization

### Validation and Automation

- Validate status codes such as `200`, `201`, `400`, and `404`
- Validate response time against the configured threshold (under 2,000 ms)
- Check response headers and body payloads
- Chain runtime variables such as `b_id` and `b_token` between requests
- Run tests through GitHub Actions and Jenkins pipelines
- Send email summaries and HTML reports when notification steps are configured

---

## 📋 Prerequisites

- [Node.js](https://nodejs.org/) v24.x or later
- [npm](https://www.npmjs.com/)
- [Newman CLI](https://www.npmjs.com/package/newman)
- [Newman HTML Extra Reporter](https://www.npmjs.com/package/newman-reporter-htmlextra)

Install Newman and the HTML Extra reporter:

```bash
npm install -g newman newman-reporter-htmlextra
```

Verify installation:

```bash
node --version
npm --version
newman --version
```

---

## 🚀 Local Execution

### 1. Clone the repository

```bash
git clone https://github.com/MaheshH91/RestfulBookerPostmanAPI.git
cd RestfulBookerPostmanAPI
```

### 2. Run the collection

```bash
newman run Booking_API.json -e Environment.json
```

### 3. Generate an HTML Extra report

```bash
newman run Booking_API.json \
  -e Environment.json \
  --reporters=cli,htmlextra \
  --reporter-htmlextra-export newman/BookingAPIReport.html \
  --reporter-htmlextra-darkTheme \
  --reporter-htmlextra-title "Restful Booker API Test Report" \
  --disable-unicode
```

Ensure `Booking_API.json` and `Environment.json` match the actual filenames in your repository. Create the `newman` output directory before execution if it does not exist.

---

## 🔄 CI/CD Pipelines

### GitHub Actions

The workflow file is described as `.github/workflows/newman-api-tests.yml`. Configure it to run the Newman collection on pushes or pull requests, upload `BookingAPIReport.html` as an artifact, and send a run summary/report email if those steps are enabled in the workflow.

### Jenkins Pipeline

The `Jenkinsfile` can execute the Newman suite on Jenkins agents and publish the HTML report using the HTML Publisher plugin.

- **Report directory:** `newman`
- **Report file:** `BookingAPIReport.html`
- **Suggested report title:** `Newman Booking API Report`

Configure Node.js, Newman, environment variables, credentials, and required Jenkins plugins on the agent before running the pipeline.

---

## 🔐 Configuration and Security

- Use test-only credentials and environment values.
- Do not commit secrets, passwords, or authentication tokens.
- Store CI/CD secrets in GitHub Actions secrets or Jenkins Credentials.
- Avoid including sensitive values in request/response logs and HTML reports.
- Verify collection and environment filenames against the repository before running commands.

---

## 👨‍💻 Maintainer

**Mahesh Holkar** — *Senior Automation Test Engineer (SDET)*

- GitHub: [MaheshH91](https://github.com/MaheshH91)
- LinkedIn: [Mahesh Holkar](https://www.linkedin.com/in/maheshholkarqaengineer/)
