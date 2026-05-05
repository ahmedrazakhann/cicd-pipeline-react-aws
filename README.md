<div>

# CI/CD Pipeline — React + AWS Deployment

**A production-grade GitHub Actions pipeline for automating build, test, lint, and cloud deployment of React applications.**

![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=FF9900)
![ESLint](https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint&logoColor=white)

</div>

---

## Overview

This repository provides a fully automated CI/CD pipeline built with GitHub Actions for React applications using Vite. It covers the complete delivery lifecycle — from code commit to cloud deployment — with zero manual intervention.

Designed for teams and engineers who want a reliable, repeatable, and professional deployment workflow without the overhead of complex DevOps tooling.

---

## Pipeline Architecture

```
Push / Pull Request
        │
        ▼
┌───────────────────┐
│   Lint & Validate  │  ← ESLint static analysis
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│   Build & Test    │  ← Vite production build
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│   Deploy to AWS   │  ← S3 sync + CloudFront invalidation
└───────────────────┘
```

---

## What This Pipeline Does

| Stage | Action | Trigger |
|-------|--------|---------|
| **Lint** | Runs ESLint across all source files | Every push and PR |
| **Build** | Compiles and bundles via Vite | Every push and PR |
| **Deploy** | Syncs build artifacts to AWS S3 | Push to `main` only |
| **Invalidate** | Clears CloudFront CDN cache | Post-deploy on `main` |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend Framework | React 18 |
| Build Tool | Vite |
| CI/CD Automation | GitHub Actions |
| Cloud Storage | AWS S3 |
| CDN | AWS CloudFront |
| Code Quality | ESLint |

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ahmedrazakhann/cicd-pipeline-react-aws.git
cd cicd-pipeline-react-aws
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Run Locally

```bash
npm run dev
```

### 4. Run Linter

```bash
npm run lint
```

### 5. Production Build

```bash
npm run build
```

---

## GitHub Actions Setup

Configure the following secrets in your repository under **Settings → Secrets and Variables → Actions**:

| Secret | Description |
|--------|-------------|
| `AWS_ACCESS_KEY_ID` | AWS IAM access key |
| `AWS_SECRET_ACCESS_KEY` | AWS IAM secret key |
| `AWS_REGION` | Target AWS region (e.g. `us-east-1`) |
| `S3_BUCKET_NAME` | Target S3 bucket for deployment |
| `CLOUDFRONT_DISTRIBUTION_ID` | CloudFront distribution ID for cache invalidation |

---

## Workflow File Location

```
.github/
└── workflows/
    └── deploy.yml   ← Main CI/CD pipeline
```

---

## Why This Exists

Most deployment pipelines are either too complex for small teams or too simple for production environments. This pipeline sits precisely in the middle — straightforward enough to understand in one read, robust enough to deploy real applications with confidence.

---

## Author

**Ahmed Raza Khan** — Full-Stack Engineer · AWS Certified ML Associate

[theahmedraza.com](https://theahmedraza.com) · [LinkedIn](https://linkedin.com/in/ahmedrazakhannn) · [ahmed@theahmedraza.com](mailto:ahmed@theahmedraza.com)

---

<div align="center">
  <sub>Built with precision. Deployed with confidence.</sub>
</div>
