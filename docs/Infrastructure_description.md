# Infrastructure Description

## Overview

This document describes the infrastructure requirements and AWS services used for hosting the Udagram application, which consists of a frontend, backend API, and database.

## AWS Services Used

### 1. Amazon S3 (Simple Storage Service)

**Purpose**: Hosts the static frontend application and stores user-uploaded media files.

**Configuration**:

- **Bucket Name**: `shaher1327865590049`
- **Region**: `us-east-1`
- **Use Cases**:
  - Static Website Hosting for the front-end app
  - Media file storage for user uploads (images, etc.)
- **Access**: Public read access for static website files

**Features**:

- CORS enabled for cross-origin requests
- Bucket policy allows public access to static content

### 2. AWS Elastic Beanstalk

**Purpose**: Hosts and manages the Node.js backend API application.

**Configuration**:

- **Application Name**: `udagram-api`
- **Environment Name**: `udagram-api-dev`
- **Platform**: Node.js 20 running on 64bit Amazon Linux 2023/6.7.1
- **Region**: `us-east-1`
- **Instance Type**: t2.micro (or configured type)

### 3. Amazon RDS (Relational Database Service)

**Purpose**: Provides managed PostgreSQL database for application data.

**Configuration**:

- **Engine**: PostgreSQL
- **Instance Identifier**: `database-1`
- **Endpoint**: `database-1.cxyihszqobc4.us-east-1.rds.amazonaws.com`
- **Port**: 5432 (default PostgreSQL port)
- **Region**: `us-east-1`
- **Database Name**: `postgres`

### CI/CD Pipeline (CircleCI)

1. **Build Job**:

   - Install dependencies for frontend and backend
   - Validate code quality
   - Prepare for deployment

2. **Manual Approval**:

   - Human approval step before deployment
   - Ensures controlled releases

3. **Deploy Job**:
   - Build frontend: `npm run frontend:build`
   - Deploy frontend to S3: `aws s3 cp --recursive ./www s3://bucket-name/`
   - Build backend: `npm run api:build`
   - Deploy backend to EB: `eb deploy`
