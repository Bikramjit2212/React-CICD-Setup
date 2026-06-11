# 🚀 React CI/CD Setup

A production-oriented CI/CD implementation for a React application demonstrating modern DevOps practices using **GitHub Actions**, **Jenkins**, **Docker**, **Vitest**, and **Vercel**.

> ⚠️ The React application itself is intentionally simple. The primary objective of this repository is to showcase end-to-end CI/CD automation and deployment strategies for frontend applications.

---

## 📌 Project Overview

This project demonstrates how a React application can move from code commit to production deployment through automated pipelines.

The repository implements multiple CI/CD approaches:

- GitHub Actions based Continuous Integration
- GitHub Actions based Continuous Deployment
- Artifact-based deployment workflows
- Jenkins Declarative Pipelines
- Dockerized Jenkins agents
- Manual approval gates
- Automated testing and linting
- Secure deployment using secrets
- Production deployment to Vercel

---

## 🏗️ Architecture

```text
                 Developer
                     │
                     ▼
           Push Code to GitHub
                     │
                     ▼
       ┌────────────────────────┐
       │ GitHub Actions CI      │
       │────────────────────────│
       │ Checkout Code          │
       │ Install Dependencies   │
       │ Run ESLint             │
       │ Run Unit Tests         │
       │ Build React App        │
       │ Upload Artifacts       │
       └──────────┬─────────────┘
                  │
                  ▼
       ┌────────────────────────┐
       │ GitHub Actions CD      │
       │────────────────────────│
       │ Download Artifacts     │
       │ Authenticate Vercel    │
       │ Deploy to Production   │
       └──────────┬─────────────┘
                  │
                  ▼
             Vercel Production



Alternative Deployment Flow

Developer
    │
    ▼
 Jenkins Pipeline
    │
    ├── Workspace Cleanup
    ├── SCM Checkout
    ├── Approval Gate
    ├── Docker Agent
    ├── Build
    ├── Test
    └── Deploy
```

---

## 📂 Repository Structure

```text
React-CICD-Setup/
│
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── cd.yml
│
├── public/
│
├── src/
│   ├── __tests__/
│   │   └── App.test.jsx
│   ├── App.jsx
│   ├── main.jsx
│   └── setupTests.js
│
├── Jenkinsfile
├── eslint.config.js
├── index.html
├── package.json
├── package-lock.json
├── vite.config.js
└── README.md
```

---

# 🛠 Tech Stack

## Frontend

- React
- Vite
- JavaScript

## Testing

- Vitest
- React Testing Library

## Code Quality

- ESLint

## CI/CD

- GitHub Actions
- Jenkins

## Containerization

- Docker

## Deployment

- Vercel

---

# ✨ Features

## Application Features

- Interactive React counter application
- Production build support
- Automated unit tests

---

## DevOps Features

- Automated Continuous Integration
- Automated Continuous Deployment
- Artifact promotion strategy
- Secure secret handling
- Dockerized Jenkins builds
- Manual approval gates
- Build validation
- Production deployments
- Environment separation

---

# 🔄 CI Pipeline (GitHub Actions)

The Continuous Integration pipeline executes automatically whenever code is pushed to the `main` branch.

## Workflow Steps

### 1. Checkout Source Code

```yaml
uses: actions/checkout
```

Fetches the latest version of the repository.

---

### 2. Setup Node.js

```yaml
uses: actions/setup-node
```

Configures the Node.js runtime.

---

### 3. Install Dependencies

```bash
npm install
```

Installs all required packages.

---

### 4. Run ESLint

```bash
npm run lint
```

Ensures coding standards are maintained.

---

### 5. Execute Unit Tests

```bash
npm test
```

Validates application functionality.

---

### 6. Build Application

```bash
npm run build
```

Creates an optimized production build.

---

### 7. Upload Build Artifacts

The generated `dist` folder is uploaded for later deployment.

Benefits:

- Build once
- Deploy many
- Ensures deployment consistency

---

# 🚀 CD Pipeline (GitHub Actions)

The deployment workflow starts only after successful completion of the CI workflow.

## Workflow Triggers

### Automatic Deployment

```yaml
workflow_run
```

Deploys after CI succeeds.

---

### Manual Deployment

```yaml
workflow_dispatch
```

Allows on-demand deployments.

---

## Deployment Steps

### Download Build Artifacts

Retrieves previously validated artifacts.

---

### Authenticate with Vercel

Uses GitHub Secrets.

Example:

```yaml
VERCEL_TOKEN
```

---

### Deploy to Production

```bash
vercel --prod
```

Publishes the application to Vercel.

---

# ⚙️ Jenkins Pipeline

The repository also demonstrates a Jenkins Declarative Pipeline implementation.

## Pipeline Stages

### Workspace Cleanup

```groovy
cleanWs()
```

Prevents issues caused by leftover files.

---

### Source Checkout

```groovy
checkout scm
```

Retrieves source code.

---

### Manual Approval

```groovy
input
```

Introduces human verification before deployment.

---

### Docker Agent

```groovy
docker {
    image 'node:22.11.0-alpine3.20'
}
```

Provides isolated and reproducible builds.

---

### Build Stage

```bash
npm install
npm run build
```

Generates the production build.

---

### Testing Stage

```bash
npm run test
```

Executes automated tests.

---

### Deployment Stage

```bash
vercel --prod
```

Deploys the application to production.

---

# 🧪 Testing

Unit testing is implemented using Vitest and React Testing Library.

## Test Coverage

### Component Rendering

Verifies that the React application renders correctly.

---

### Counter Behaviour

Validates button interactions and state updates.

Example:

```text
count is 0
count is 1
count is 2
```

---

# 💻 Local Development Setup

## Clone Repository

```bash
git clone https://github.com/Bikramjit2212/React-CICD-Setup.git
```

---

## Navigate to Project

```bash
cd React-CICD-Setup
```

---

## Install Dependencies

```bash
npm install
```

---

## Start Development Server

```bash
npm run dev
```

Application runs locally.

---

## Run Tests

```bash
npm test
```

---

## Run Linter

```bash
npm run lint
```

---

## Create Production Build

```bash
npm run build
```

---

## Preview Production Build

```bash
npm run preview
```

---

# 🔐 Secrets Required

The following secrets are required for deployment:

| Secret Name | Purpose |
|------------|-----------|
| VERCEL_TOKEN | Authenticate Vercel CLI |
| VERCEL_ORG_ID | Vercel Organization ID |
| VERCEL_PROJECT_ID | Target Project Identifier |

---

# 📈 DevOps Concepts Demonstrated

- Continuous Integration
- Continuous Deployment
- Pipeline Automation
- Shift-Left Testing
- Artifact Promotion
- Deployment Gating
- Secret Management
- Dockerized Build Agents
- Production Releases
- Frontend Deployment Automation

---

# 🎯 Resume Highlights

This project demonstrates hands-on experience with:

- Designing CI/CD pipelines using GitHub Actions
- Building Jenkins Declarative Pipelines
- Implementing automated testing strategies
- Managing deployment artifacts
- Deploying React applications to production
- Securing deployments using secrets
- Using Docker for reproducible build environments

---

# 🔮 Future Enhancements

- Add code coverage reporting
- Integrate SonarQube for static analysis
- Implement Slack notifications
- Add staging environments
- Introduce blue-green deployments
- Deploy using Kubernetes
- Implement Infrastructure as Code using Terraform

---

# 👨‍💻 Author

**Bikramjit Roy**

DevOps & Cloud Engineering Enthusiast passionate about automation, CI/CD, cloud-native practices, and building reliable software delivery pipelines.

GitHub:
https://github.com/Bikramjit2212

---

## ⭐ If you found this project useful, consider giving it a star.
