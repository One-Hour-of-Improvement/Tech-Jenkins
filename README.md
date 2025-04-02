# Jenkins CI/CD Demo Project

This is a simple Flask application that demonstrates CI/CD using Jenkins, Docker, and Docker Compose.

## Project Structure

- `app.py`: Main Flask application
- `test_app.py`: Unit tests for the application
- `requirements.txt`: Python dependencies
- `Dockerfile`: Container definition for the Flask app
- `docker-compose.yml`: Orchestration for both the Flask app and Jenkins
- `Jenkinsfile`: Pipeline definition for CI/CD
- `jenkins.yaml`: Jenkins configuration file

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Start the services:
```bash
docker-compose up -d
```

2. Access the applications:
   - Flask app: http://localhost:5000
   - Jenkins: http://localhost:8080
     - Username: admin
     - Password: admin

## Jenkins Pipeline

The pipeline consists of three stages:
1. Build: Builds the Docker container
2. Test: Runs the Python tests with coverage
3. Deploy: Deploys the application using Docker Compose

## Development

To run the application locally without Docker:
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

To run tests:
```bash
pytest
``` 