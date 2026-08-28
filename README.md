<p align="center"> <img src="assets/logo.png" alt="Yapwave logo" width="120"> </p>

# Yapwave

![.NET](https://img.shields.io/badge/.NET-8-512BD4?logo=dotnet&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-DD0031?logo=angular&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-4285F4?logo=grpc&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white)

A social app, built on Angular, .NET, and a gRPC-based microservices backend.

## About

Yapwave is a personal project built to get hands on with a service oriented architecture end to end: independently deployable backend services, real time client updates, and a fully containerized deployment pipeline, instead of a single monolithic CRUD app. It's a learning-focused build, not a finished product, see Roadmap below for current status.

## Features

- **Posts** - create, view, and interact with a feed
- **Messaging** - direct messages delivered in real time
- **Likes** - react to posts with live count updates

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Angular |
| Backend | .NET (ASP.NET Core) |
| Service-to-service | gRPC |
| Real-time push | SignalR |
| Database | MongoDB |
| Cache / pub-sub | Redis |
| Containerization | Docker |
| Orchestration | Kubernetes |
| CI/CD | GitHub Actions |

## Architecture

Backend is split into independent services — Posts, Messaging, and Likes — communicating over gRPC and persisting to MongoDB. Redis handles caching and real-time fan-out. SignalR pushes live updates (new messages, live like counts) to the Angular client. Every service is containerized and deployed to Kubernetes.

```mermaid
flowchart LR
    A[Angular Client] -- SignalR/HTTPS --> B[API Gateway]
    B -- gRPC --> C[Posts Service]
    B -- gRPC --> D[Messaging Service]
    B -- gRPC --> E[Likes Service]
    C --> F[(MongoDB)]
    D --> F
    E --> F
    C --> G[(Redis)]
    D --> G
    E --> G
```

## Project Structure (planned)

```
yapwave/
├── client/                  # Angular app
├── services/
│   ├── posts/                # Posts microservice (.NET)
│   ├── messaging/             # Messaging microservice (.NET)
│   └── likes/                  # Likes microservice (.NET)
├── protos/                   # gRPC contract definitions
├── k8s/                          # Kubernetes manifests
├── docker-compose.yml
└── .github/workflows/         # CI/CD pipelines
```

## Getting Started

Prerequisites:
- .NET SDK 8+
- Node.js + Angular CLI
- Docker
- kubectl (for local Kubernetes - Minikube or Kind)

Setup and run instructions will be added as each service is implemented.

## Roadmap

- [ ] Auth
- [ ] Posts service
- [ ] Messaging service (real-time)
- [ ] Likes service
- [ ] Redis caching / pub-sub
- [ ] Dockerize all services
- [ ] Kubernetes manifests
- [ ] CI/CD pipeline

## License

MIT [LICENSE](LICENSE.md)
