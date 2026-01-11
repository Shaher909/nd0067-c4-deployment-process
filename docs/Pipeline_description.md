# Pipeline Description

## Overview

This document describes the CI/CD pipeline implemented using CircleCI for the Udagram application.

## Pipeline Workflow

The pipeline consists of three main stages:

```
Developer Push → Build Job → Manual Approval → Deploy Job
```

## Pipeline Steps

### 1. Build Job

**Trigger**: Automatically runs when code is pushed to any branch.

**Environment**: Docker container with Node.js 14.15

**Steps**:

1. **Install Node.js**: Sets up Node.js version 14.15
2. **Checkout Code**: Clones the repository code
3. **Install Frontend Dependencies**: Runs `npm run frontend:install` to install Angular/Ionic dependencies
4. **Install API Dependencies**: Runs `npm run api:install` to install backend Node.js dependencies

**Purpose**: Validates that all dependencies can be installed successfully.

---

### 2. Hold (Manual Approval)

**Trigger**: Automatically created after build job completes, only on `master` branch.

**Action Required**: A team member must manually approve the deployment before proceeding.

**Purpose**: Provides a gate to prevent automatic deployments to production, allowing for human verification.

---

### 3. Deploy Job

**Trigger**: Runs after manual approval is granted.

**Environment**: Docker container with Node.js 14.15, AWS CLI, and Elastic Beanstalk CLI

**Setup Steps**:

1. **Install Node.js**: Sets up Node.js version 14.15
2. **Setup Elastic Beanstalk CLI**: Configures `eb` command
3. **Setup AWS CLI**: Configures `aws` command
4. **Checkout Code**: Clones the repository code

**Deployment Step**:

- **Deploy App**: Runs `npm run deploy` which:
  - Deploys API to Elastic Beanstalk (`npm run api:deploy`)
  - Deploys Frontend to S3 (`npm run frontend:deploy`)

**What Happens**:

**API Deployment**:

1. Installs dependencies
2. Builds TypeScript to JavaScript
3. Creates deployment package
4. Deploys to Elastic Beanstalk using `eb deploy`

**Frontend Deployment**:

1. Installs dependencies
2. Builds Angular application
3. Uploads built files to S3 bucket using `aws s3 cp`

---

## Environment Variables Required

The following environment variables must be configured in CircleCI:

- `AWS_ACCESS_KEY_ID`: AWS access key
- `AWS_SECRET_ACCESS_KEY`: AWS secret key
- `AWS_DEFAULT_REGION`: us-east-1

* the Application related envs - refer to `set_env.sh` file for details.

---

## Pipeline Diagram

```
┌─────────────┐
│   Push to   │
│   GitHub    │
└──────┬──────┘
       │
       ▼
┌─────────────────────────────┐
│      Build Job              │
│  - Install Dependencies     │
│  - Frontend & API           │
└──────┬──────────────────────┘
       │
       ▼
┌─────────────────────────────┐
│   Manual Approval           │
│   (master branch only)      │
└──────┬──────────────────────┘
       │
       ▼
┌─────────────────────────────┐
│      Deploy Job             │
│  - Build & Deploy API       │
│  - Build & Deploy Frontend  │
└─────────────────────────────┘
       │
       ├──────────────┐
       ▼              ▼
┌─────────────┐  ┌─────────────┐
│ S3 Bucket   │  │  Elastic    │
│  Frontend   │  │  Beanstalk  │
└─────────────┘  └─────────────┘
```

---
