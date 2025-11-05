# Module 11 – Secure Calculation Model & Validation (FastAPI + SQLAlchemy + CI/CD)

**Author:** Muhammad Arham  
**Course:** IS601 – Module 11  
**Repository:** [assignment11](https://github.com/arhamidrees63/assignment11)  
**Docker Hub:** [arhamidrees63/module11_is601](https://hub.docker.com/r/arhamidrees63/module11_is601)

---

## 🚀 Project Overview
This module extends the FastAPI application from Module 10 by adding a **Calculation model** with full database integration, Pydantic validation, and optional Factory Pattern logic.  
It reinforces clean architecture principles while maintaining automated testing, continuous integration, and Docker-based deployment.

---

## 🧠 Key Features
- **SQLAlchemy Calculation Model**
  - Fields: `id`, `a`, `b`, `type`, `result`, and optional `user_id` (FK).
  - Supports operations: Add, Subtract, Multiply, Divide.
  - Optional on-demand result computation or persisted results.

- **Pydantic Schemas**
  - `CalculationCreate`: Validates input (`a`, `b`, `type`) and disallows invalid types or zero divisors.
  - `CalculationRead`: Serializes output cleanly for frontend or API responses.

- **Factory Pattern (Optional Enhancement)**
  - Centralized creation of calculation objects for each operation type.
  - Enables easy extension for future mathematical operations.

- **Testing**
  - ✅ **Unit Tests:** cover calculation logic, validation, and factory creation.  
  - ✅ **Integration Tests:** confirm correct database persistence using PostgreSQL in CI.  
  - ✅ **End-to-End Tests:** verify API and UI functionality.

- **CI/CD Pipeline**
  - GitHub Actions pipeline performs:
    - Automated testing (`pytest` + coverage)
    - Security scan (Trivy)
    - Docker image build and push to Docker Hub on success

---

## 🧩 Project Structure
├── app/
│ ├── models/
│ │ └── calculation.py
│ ├── schemas/
│ │ └── calculation_schema.py
│ ├── operations/
│ │ └── factory.py
│ ├── auth/
│ ├── database.py
│ └── main.py
├── tests/
│ ├── unit/
│ ├── integration/
│ └── e2e/
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── pytest.ini
└── .github/workflows/test.yml

yaml
Copy code

---

## 🧪 Run Locally

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/arhamidrees63/assignment11.git
cd assignment11
2️⃣ Create and Activate Virtual Environment
bash
Copy code
python3 -m venv venv
source venv/bin/activate
3️⃣ Install Dependencies
bash
Copy code
pip install -r requirements.txt
4️⃣ Run Docker Services
bash
Copy code
docker compose up -d --build
This will start:

FastAPI app → http://localhost:8000

PostgreSQL → port 5432

pgAdmin → http://localhost:5050

5️⃣ Run Tests
bash
Copy code
pytest -v
All unit, integration, and E2E tests should pass.

🐳 Docker Image
To pull and run the image directly from Docker Hub:

bash
Copy code
docker pull arhamidrees63/module11_is601:latest
docker run -d -p 8000:8000 arhamidrees63/module11_is601
🧭 CI/CD Workflow
Testing: Runs unit + integration tests in GitHub Actions.

Security Scan: Trivy scans for vulnerabilities in dependencies.

Deployment: On successful tests, Docker image is pushed to
👉 arhamidrees63/module11_is601.

🧾 Reflection
During this module, I learned how to:

Model database entities with SQLAlchemy relationships.

Validate user input robustly with Pydantic models.

Implement design patterns (Factory) for scalable logic.

Maintain continuous testing and security in a CI/CD pipeline.

Build, tag, and deploy a production-ready Docker image to Docker Hub.