# Jenkins Pipeline for CI/CD

## Project Overview

This project demonstrates a basic CI/CD pipeline using Jenkins and Docker to automate the build, test, and deployment of a Node.js application.

## Tools & Technologies

* Jenkins
* Docker
* Node.js & npm
* Git & GitHub
* Jest

## Pipeline Stages

1. **Checkout:** Pulls the source code from GitHub.
2. **Install Dependencies:** Installs packages using `npm ci`.
3. **Test:** Runs automated tests using Jest.
4. **Docker Build:** Builds a Docker image of the application.
5. **Deploy:** Runs the application inside a Docker container.
6. **Verify:** Checks the running container.

## How to Run Locally

```bash
npm ci
npm test
docker build -t nodejs-demo-app:jenkins .
docker run -d --name nodejs-demo-container -p 3000:3000 nodejs-demo-app:jenkins
```

## Application Endpoints

* **Home:** http://localhost:3000/
* **Health Check:** http://localhost:3000/health

## Jenkins Configuration

* Jenkins runs in a Docker container.
* Docker is used to build and run the application.
* The pipeline is defined in the `Jenkinsfile`.
* The pipeline can be triggered by source-code changes.

## Result

The Jenkins pipeline completed successfully. Dependency installation, automated testing, Docker image creation, and container deployment were verified.

## Author

Sumeet Rawal
