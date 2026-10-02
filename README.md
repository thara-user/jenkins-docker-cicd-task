# Jenkins Docker CI/CD Pipeline

## Project Overview

This project demonstrates a basic CI/CD pipeline using Jenkins and Docker.

The pipeline automates the following process:

GitHub → Jenkins → Checkout → Build → Test → Deploy → Docker Container

The application is a simple HTML web application served using Nginx.

## Objective

The objective of this project is to create a simple Jenkins CI/CD pipeline that automates the build, test, and deployment of a Dockerized web application.

## Technologies Used

- Jenkins
- Docker
- Docker Desktop
- Git
- GitHub
- Nginx
- Windows
- PowerShell

## Project Structure

```text
jenkins-docker-cicd-task/
│
├── app/
│   └── index.html
│
├── screenshots/
│   ├── Screenshot 2026-10-02 140202.png
│   ├── Screenshot 2026-10-02 140300.png
│   ├── Screenshot 2026-10-02 140332.png
│   └── Screenshot 2026-10-02 141058.png
│
├── Dockerfile
├── Jenkinsfile
└── README.md
