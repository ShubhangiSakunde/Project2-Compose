# Docker Compose for Jenkins with Docker-in-Docker (DinD)

This repository contains the Docker Compose configuration to run Jenkins in a containerized environment with Docker-in-Docker (DinD) setup, allowing for seamless automation of CI/CD pipelines.

## Project Overview

This project sets up a secure CI/CD environment using Jenkins and Docker Compose. The Docker Compose configuration runs Jenkins with Docker-in-Docker (DinD) to enable Jenkins to execute Docker commands within containers.

### Project Structure

- `docker-compose.yml`: Defines the services, volumes, and network configuration for running Jenkins and Docker in Docker (DinD).

## Prerequisites

- Docker and Docker Compose installed
- Minimum system requirements: 
  - 1 GB RAM, 2 CPU cores, 10 GB free disk space
- GitHub account for managing repositories

## Setup Instructions

1. **Clone this repository** to your local machine:
    ```bash
    git clone https://github.com/YourUsername/Project2-Compose.git
    ```

2. **Navigate to the project directory**:
    ```bash
    cd Project2-Compose
    ```

3. **Run the Docker Compose setup** to start Jenkins and Docker-in-Docker containers:
    ```bash
    docker-compose up -d
    ```

4. **Access Jenkins**:
    - Open Jenkins on `http://localhost:8080`.
    - Retrieve the `initialAdminPassword` from the Jenkins container logs:
      ```bash
      docker logs jenkins-container-name
      ```
    - Install the required plugins and create your admin user.

5. **Configure Jenkins**:
   - Install the Blue Ocean plugin for improved pipeline visualization.
   - Install the Docker plugin to enable Jenkins to run Docker commands.

## Pipeline Setup

1. **Jenkinsfile**: Make sure the Jenkinsfile in your Node.js application repository is configured to automate the build, test, and deployment process. 
   - Node 16.x Docker image is used as the build agent.
   - Docker image for the application is built and pushed to Docker Hub.

2. **Docker-in-Docker Configuration**:
   - The `jenkins-docker` service runs Docker commands within the container.
   - The `jenkins-blueocean` service runs Jenkins with the Blue Ocean plugin enabled for better pipeline management.

## Pushing Docker Compose Configuration

The Docker Compose configuration is committed to the main branch of this repository. Ensure that you push updates using:
```bash
git add .
git commit -m "Updated Docker Compose configuration"
git push origin main
