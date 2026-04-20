# Hello Docker

A simple static website containerized using Docker.

## Build
docker build -t hello-world-app .

## Run
docker run -p 8080:80 hello-world-app

## Explanation of Dockerfile Instructions

FROM: Uses an existing image (Nginx) as the base. It already has a web server installed.
RUN: Executes commands while building the image. Here, it removes default files.
COPY: Copies your index.html from your computer into the container.
CMD: Tells the container what to run when it starts (starts the web server).

## Image Tagging Strategy

Docker images are tagged with:

- `latest`: represents the most recent successful build
- Git commit SHA: uniquely identifies each version of the application

The commit SHA is generated using:

git rev-parse --short HEAD

This allows traceability and easy rollback to previous versions.

## CI/CD Pipeline

This project uses GitHub Actions to:

- Checkout code on every push
- Run a basic test step
- Build Docker images
- Tag images with `latest` and commit SHA
- Push images to Docker Hub


