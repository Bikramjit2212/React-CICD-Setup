# React CI/CD Setup

A hands-on DevOps project demonstrating the implementation of a **Continuous Integration and Continuous Delivery (CI/CD) pipeline** for a React application using Jenkins and GitHub Actions.

This project was developed to gain practical experience in automating software delivery workflows, integrating code quality checks, and understanding modern DevOps practices.

---

## Project Overview

Modern software development relies heavily on CI/CD pipelines to ensure faster, reliable, and repeatable deployments. In this project, a React application built with Vite is integrated with automated workflows to streamline the software delivery process.

The pipeline automates various stages of the development lifecycle, including code integration, testing, build validation, approval gates, and deployment readiness.

---

## Key Features

* Automated CI/CD pipeline implementation.
* React application built using Vite.
* Jenkins pipeline integration using Jenkinsfile.
* GitHub Actions workflow automation.
* Automated build execution.
* Manual approval stage before deployment.
* Time-based approval window implementation.
* Dependency management using npm.
* Code quality validation using ESLint.
* Demonstrates modern DevOps practices.

---

## Technologies Used

### Frontend

* React
* Vite
* JavaScript
* HTML
* CSS

### DevOps & Automation

* Jenkins
* GitHub Actions
* CI/CD Pipelines
* Jenkins Pipeline (Declarative)
* GitHub Workflows

### Development Tools

* npm
* ESLint
* Git
* GitHub

---

## Repository Structure

```text
React-CICD-Setup/
├── .github/
│   └── workflows/               # GitHub Actions workflows
├── public/                      # Static assets
├── src/                         # React application source code
├── Jenkinsfile                  # Jenkins CI/CD pipeline definition
├── package.json                 # Project dependencies and scripts
├── package-lock.json            # Dependency lock file
├── vite.config.js               # Vite configuration
├── eslint.config.js             # ESLint configuration
├── index.html                   # Application entry point
├── .gitignore
└── README.md
```

---

## CI/CD Pipeline Workflow

```text
Developer Pushes Code
          ↓
     GitHub Repository
          ↓
GitHub Actions Triggered
          ↓
Dependency Installation
          ↓
Code Validation & Checks
          ↓
Application Build
          ↓
Jenkins Pipeline Execution
          ↓
Manual Approval Stage
          ↓
Approval Timeout Validation
          ↓
Deployment Ready
```

---

## Jenkins Pipeline Highlights

The Jenkins pipeline demonstrates:

* Automated pipeline execution.
* Multi-stage workflow implementation.
* Build automation.
* Manual approval gate before deployment.
* Timer-based approval handling.
* Improved control over release processes.

---

## GitHub Actions Workflow

The GitHub Actions workflow automates:

* Triggering pipeline execution on repository events.
* Installing dependencies.
* Running project validation steps.
* Building the React application.
* Supporting continuous integration practices.

---

## Prerequisites

Before running this project, ensure you have:

* Node.js installed
* npm installed
* Jenkins configured
* Git installed
* GitHub repository access

---

## How to Run Locally

### Clone the Repository

```bash
git clone https://github.com/Bikramjit2212/React-CICD-Setup.git
```

### Navigate to the Project Directory

```bash
cd React-CICD-Setup
```

### Install Dependencies

```bash
npm install
```

### Start the Development Server

```bash
npm run dev
```

### Build the Application

```bash
npm run build
```

---

## What I Learned

Through this project, I gained practical exposure to:

* Designing CI/CD workflows.
* Building Jenkins pipelines.
* Configuring GitHub Actions.
* Automating software delivery processes.
* Implementing approval gates.
* Managing JavaScript application dependencies.
* Integrating DevOps practices into application development.
* Understanding deployment readiness checks.

---

## Use Cases

* Learning CI/CD implementation.
* Demonstrating DevOps pipeline skills.
* Understanding Jenkins and GitHub Actions integration.
* Practicing release approval workflows.
* Preparing for DevOps interviews.
* Building a foundation for enterprise deployment pipelines.

---

## Future Improvements

I plan to enhance this project by adding:

* Docker containerization.
* Automated deployment to Kubernetes.
* SonarQube integration for code quality analysis.
* Security scanning using Trivy.
* Artifact storage using Nexus.
* Deployment to AWS infrastructure.
* Slack or email notifications for pipeline status.

---

## About This Project

This project was created as part of my transition into DevOps and Cloud Engineering. As a fresher, my focus has been on learning by building practical projects that reflect real-world software delivery workflows and automation practices.

It represents my understanding of how development and operations teams collaborate to deliver applications efficiently through CI/CD pipelines.

---

## Author

**Bikramjit Roy**
Aspiring DevOps & Cloud Engineer

GitHub: https://github.com/Bikramjit2212
LinkedIn: https://www.linkedin.com/in/bikramjitroy/

---

## License

This project is intended for educational and portfolio purposes.
