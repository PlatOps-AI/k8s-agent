# k8s-agent

A lightweight Kubernetes agent that provides a REST API interface for executing kubectl commands securely within a cluster.

## Features

- REST API interface for executing kubectl commands
- Secure command validation and execution
- Kubernetes RBAC integration
- Containerized deployment ready

## Prerequisites

- Python 3.11+
- Poetry for dependency management
- Kubernetes cluster with RBAC enabled
- kubectl CLI tool

## Installation

### Local Development

1. Clone the repository:
```bash
git clone https://github.com/yourusername/k8s-agent.git
cd k8s-agent
```

2. Install dependencies using Poetry:
```bash
poetry install
```

3. Start the development server:
```bash
poetry run start
```

### Kubernetes Deployment

1. Apply the RBAC configuration:
```bash
kubectl apply -f example/rbac.yaml
```

2. Deploy the k8s-agent:
```bash
kubectl apply -f example/k8s-agent.yaml
```

## Usage

The API exposes the following endpoints:

### Health Check
```bash
GET /
```

### Execute kubectl Command
```bash
POST /command
Content-Type: application/json

{
    "command": "kubectl get pods"
}
```

## Security

The agent includes several security features:
- Command validation to ensure only kubectl commands are executed
- RBAC configuration limiting access to specific Kubernetes resources
- Containerized execution environment

## Configuration

The service runs on port 3000 by default and can be configured through the following environment variables:
- PORT: API server port (default: 3000)
- HOST: API server host (default: 0.0.0.0)

## Development

### Code Style and Linting

The project uses several tools for code quality:
- Black for code formatting
- Ruff for linting
- Pre-commit hooks for code quality checks

### Running Tests

Run tests using:
```bash
poetry run pytest
```

## Docker

Build the Docker image:
```bash
docker build -t k8s-agent .
```

Run the container:
```bash
docker run -p 3000:3000 k8s-agent
```

## License

MIT License

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes using conventional commits
4. Push to the branch
5. Create a new Pull Request
