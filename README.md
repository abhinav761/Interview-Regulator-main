# Talent Match — Interview Regulator AI System

## Introduction

Large institutions like DRDO receive thousands of applicants for their technical interviews. These are mostly boardroom interviews where candidates are manually matched with interviewers based on the interviewers' expertise and the candidates' experience, education, and job role — all to ensure that the right person is hired. A single mis-hire can cause significant loss to an organisation. However, this manual matching process is time-consuming, cost-inefficient, and highly prone to human error.

**Interview Regulator / Talent Match** solves this problem by leveraging advanced AI-driven candidate-to-interviewer mapping using:

- **Semantic search** and **NLP models** for best-in-class contextual and relevance matching
- **Large Language Models (LLMs)** — which have seen significant recent advancements — that now surpass traditional NLP models and even human judgment in precision, while operating at machine speed; this directly addresses the twin challenges of time and accuracy

### Fairness & Scoring

To ensure fairness in interviews, Talent Match does not only evaluate the candidate. It also analyses the **interviewer** across dimensions such as:

- Relevance, depth, and difficulty of questions asked
- Expertise level of the interviewer who asked each question

These factors are used to **normalise candidate scores**, ensuring a level playing field. Final scores are produced by a **complex weighted, priority-based scoring algorithm** that drives the ultimate hiring decision.

### Candidate Profile Validation

Candidate profiles are validated using AI to detect and prevent **fraudulent submissions**, ensuring the integrity of the entire process.

---

## Quantifiable Impact

### Impact on the Organisation

| Metric | Estimated Impact |
|---|---|
| **Time savings** | Up to **70–80% reduction** in manual matching time; what takes days can be completed in minutes |
| **Cost efficiency** | Reduction in HR operational costs by **30–50%** through automation of screening and matching |
| **Mis-hire reduction** | AI-driven precision matching can lower mis-hire rates by **40–60%**, avoiding costs that typically equal **1–3× the annual salary** of the role |
| **Interviewer utilisation** | Ensures interviewers are matched only to candidates within their domain, improving panel **utilisation efficiency by 50%+** |
| **Bias mitigation** | Normalised scoring reduces subjective bias, improving **diversity hiring outcomes** |
| **Fraud prevention** | AI profile validation can detect fraudulent credentials, protecting against costly bad hires |

### Market Opportunity

| Dimension | Data Point |
|---|---|
| **Global HR Tech market size** | ~**$40 billion** (2024), projected to exceed **$90 billion by 2030** (CAGR ~13%) |
| **AI in recruitment market** | Expected to grow from ~$590 million (2022) to **$1.1 billion by 2030** |
| **Target segments** | Government defence organisations (DRDO, ISRO), PSUs, large enterprises, IT firms, MNCs |
| **Enterprise recruitment spend** | Large organisations spend **$4,000–$10,000 per hire**; automation can cut this by up to **50%** |
| **Scalability** | SaaS model enables rapid scaling across industries with minimal incremental cost |

---

## 🛠️ Installation — Local Development

### Prerequisites

| Tool | Version | Notes |
|---|---|---|
| **Node.js** | `v18+` | LTS recommended |
| **npm** | `v9+` | Bundled with Node.js |
| **Git** | Any recent version | For cloning the repo |
| **Docker** *(optional)* | `v20+` | Required only for container builds |

### Local Setup (Without Docker)

1. **Clone the Repository**
   ```bash
   git clone https://github.com/abhinav761/Interview-Regulator-main.git
   cd Interview-Regulator-main
   ```

2. **Install Dependencies**
   ```bash
   npm ci
   ```

3. **Start the Development Server**
   ```bash
   npm run dev
   ```
   The app will be available at **http://localhost:5173**.

---

## 🐳 Running with Docker

This project comes fully containerized with a production-ready, multi-stage Docker build utilizing **Node** and **Nginx**.

### Using Docker Compose (Recommended)

To run the application locally on **Port 3000** without installing any Node modules:

```bash
# Build and start the container in the background
docker-compose up -d --build

# Stop the container
docker-compose down
```
Access the application at **http://localhost:3000**.

### Using Docker CLI Manually

```bash
# 1. Build the production image
docker build -t interview-regulator-app:latest .

# 2. Run the container locally
docker run -p 3000:80 -d --name interview-regulator-web interview-regulator-app:latest
```

---

## 🚀 Automated CI/CD Pipelines

This repository is configured with two professional deployment pipelines that handle build generation and isolated testing.

### 1. GitHub Actions (Cloud)
Located in `.github/workflows/ci.yml`. This pipeline triggers automatically on all pushes and pulls requests to the `main` branch. It securely builds the Docker container utilizing GitHub's infrastructure and `buildx` caching to ensure code integrity.

### 2. Jenkins (Local)
Located in the `Jenkinsfile` at the root of the project. It handles cloning the repository and running local batch commands to orchestrate building the image and tearing down/deploying the new Nginx container seamlessly onto Port `3000`.

---

## 📁 Project Structure

```
Interview-Regulator-main/
├── .github/workflows/         
│   └── ci.yml                 # GitHub Actions Pipeline
├── src/                       # React Frontend + TypeScript Source Code
├── public/                    # Static Application Assets
├── Dockerfile                 # Multi-stage Nginx Image Build
├── docker-compose.yml         # Container Orchestration
├── Jenkinsfile                # Local Deploy Pipeline
├── package.json               # Project Dependencies & Vite Scripts
├── tailwind.config.ts         # Tailwind Styling Defaults
└── vite.config.ts             # Vite Bundler System Configuration
```
