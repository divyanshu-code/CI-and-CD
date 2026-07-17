# CI and CD

This repository contains two Node.js Express backends and example GitHub Actions workflows for continuous integration and continuous deployment.

## Project Structure

- `.github/workflows/ci.yml` - CI workflow for the `Backend` folder and Render deploy hook trigger
- `.github/workflows/docker_aws.yml` - CI/CD workflow for the `Backend_docker` folder with AWS ECR/ECS deployment
- `Backend/` - simple Express backend with `npm start` support
- `Backend_docker/` - Docker-enabled backend for container build and AWS deployment

## Backend (Local Development)

1. Open a terminal in `Backend`
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the server:
   ```bash
   npm start
   ```
4. Open `http://localhost:3000`

The application responds with `hello world`.

## Backend_docker (Docker + AWS Deployment)

1. Open a terminal in `Backend_docker`
2. Install dependencies:
   ```bash
   npm install
   ```
3. Build and run locally with Docker:
   ```bash
   docker build -t backend-docker .
   docker run -p 4000:4000 backend-docker
   ```
4. Open `http://localhost:4000`

This variant exposes port `4000` and is configured for containerized deployment.

## GitHub Actions Workflows

- `ci.yml` runs CI for the `Backend` folder on pushes and pull requests to `main`.
- `docker_aws.yml` runs tests and deploys the `Backend_docker` container to AWS ECR/ECS on changes to `Backend_docker`.

### Secrets Used

- `RENDER_DEPLOY_HOOK` for Render webhook deployment in `ci.yml`
- `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` for AWS deployment in `docker_aws.yml`

## Notes

- `Backend/package.json` includes:
  - `start`: `node index.js`
- `Backend_docker/package.json` is set up for Docker build and local testing.
- The `Backend_docker/Dockerfile` uses `node:18-alpine`, installs dependencies, copies source, exposes port `4000`, and runs `node index.js`.
- Workflow files are stored in `.github/workflows/` and should remain in the repo root.

## Learning Points

- How to structure a repository with separate local and containerized backends.
- How to configure GitHub Actions for different folders and workflow triggers.
- The importance of using repository secrets for deployment hooks and AWS credentials.
- How to use working directories in GitHub Actions to run commands from subfolders.
