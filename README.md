# Project Overview

This project contains a full-stack web appliation:

- Frontend application
- Back-end API application
- Pipeline setup over CircleCi for automating tests and deployments

## Techstack & Links

- AWS is used as infrastructure provider, the following components are used:
  - RDS for hosting the Postgres database
  - S3 for hosting the static website(frontend) and storing uploaded images
  - ElasticBeanstalk for hosting the backend api
- CircleCi is used as CI/CD tool for automating tests and deployments

This is a [Link to the front-end application](http://shaher1327865590049.s3-website-us-east-1.amazonaws.com)

## Screenshots

1. The front-end page sign up process

   ![Sign Up Page](./docs/screenshots/FE-1.jpg)

2. The front-end page after login / sign up

   ![Home Page](./docs/screenshots/FE-2.jpg)

3. A post creted using the application

   ![Create Post](./docs/screenshots/FE-3.jpg)

4. The back-end API application hosted on ElasticBeanstalk

   ![ElasticBeanstalk Dashboard](./docs/screenshots/EB-App.jpg)

5. The RDS database instance hosting Postgres

   ![RDS Dashboard](./docs/screenshots/RDS-DB.jpg)

6. The S3 bucket hosting the frontend static website and uploaded images

   ![S3 Dashboard](./docs/screenshots/S3.jpg)

7. Environment vars on CircleCi

   ![CircleCi env vars](./docs/screenshots/env-vars.jpg)

8. The deployment pipeline on CircleCi

![CircleCi pipeline](./docs/screenshots/CircleCi.jpg)

![CircleCi build step](./docs/screenshots/CircleCi-build.jpg)
![CircleCi deploy step](./docs/screenshots/CircleCi-deploy.jpg)

## Architecture

The following diagram illustrates:

- An architecture diagram showing a high-level overview of the infrastructure

![The over all architecture](./docs/architecture.jpg)

- Pipeline diagram
  ![Pipeline diagram](./docs/pipeline.jpg)
