# Go Web Application

A lightweight, production-ready web application built with Go. This application demonstrates a multi-page website with static HTML rendering, containerization, and Kubernetes deployment capabilities.

## Features

- **Simple & Fast**: Built with Go's standard `net/http` package for minimal dependencies
- **Multi-page Website**: Home, Courses, About, and Contact pages
- **Docker Support**: Multi-stage Dockerfile using distroless base image for minimal image size
- **Kubernetes Ready**: Includes Kubernetes manifests and Helm charts for easy deployment
- **Production Grade**: Includes CI/CD pipeline configuration

## Prerequisites

- Go 1.22 or higher
- Docker (for containerization)
- kubectl (for Kubernetes deployment)
- Helm (optional, for Helm deployments)

## Project Structure

```
go-web-app/
├── main.go                 # Application entry point and route handlers
├── main_test.go            # Go unit tests
├── Dockerfile              # Multi-stage Docker build configuration
├── go.mod                  # Go module definition
├── static/                 # Static assets
│   ├── home.html          # Home page
│   ├── courses.html       # Courses page
│   ├── about.html         # About page
│   ├── contact.html       # Contact page
│   └── images/            # Image assets
├── K8s/                   # Kubernetes manifests
│   └── manifests/
│       ├── deployment.yaml
│       ├── service.yaml
│       └── ingress.yaml
└── helm/                  # Helm chart
    └── go-web-app-chart/
        ├── Chart.yaml
        ├── values.yaml
        └── templates/
```

## Quick Start

### Running Locally

1. **Clone the repository**
   ```bash
   git clone https://github.com/iam-veeramalla/go-web-app.git
   cd go-web-app
   ```

2. **Run the application**
   ```bash
   go run main.go
   ```

3. **Access the application**
   - Home: http://localhost:8080/home
   - Courses: http://localhost:8080/courses
   - About: http://localhost:8080/about
   - Contact: http://localhost:8080/contact

### Running with Docker

1. **Build the Docker image**
   ```bash
   docker build -t go-web-app:latest .
   ```

2. **Run the container**
   ```bash
   docker run -p 8080:8080 go-web-app:latest
   ```

3. **Access the application**
   Open your browser and navigate to `http://localhost:8080/home`

## API Routes

| Route | Method | Description |
|-------|--------|-------------|
| `/home` | GET | Home page |
| `/courses` | GET | Courses page |
| `/about` | GET | About page |
| `/contact` | GET | Contact page |

## Kubernetes Deployment

### Using kubectl

Deploy using Kubernetes manifests:

```bash
kubectl apply -f K8s/manifests/
```

### Using Helm

Deploy using Helm chart:

```bash
helm install go-web-app ./helm/go-web-app-chart/
```

To customize the deployment, update the values:

```bash
helm install go-web-app ./helm/go-web-app-chart/ -f custom-values.yaml
```

## Testing

Run the unit tests:

```bash
go test -v
```

## Building the Application

### Build the Go binary

```bash
go build -o main .
```

### Run the binary

```bash
./main
```

## Docker Image Details

The application uses a multi-stage Docker build:

- **Build Stage**: Uses `golang:1.22` to compile the application
- **Final Stage**: Uses `gcr.io/distroless/base` for a minimal runtime image (~20MB)

This approach significantly reduces the final image size while maintaining security and functionality.

## Environment

The application listens on:
- **Host**: 0.0.0.0
- **Port**: 8080

## Performance Considerations

- The application serves static HTML files efficiently using Go's built-in HTTP server
- Distroless base image reduces attack surface and container size
- Minimal dependencies for quick startup and deployment

## License

This project is open source and available under the terms specified in the [LICENSE](LICENSE) file.

## Preview

![Website](static/images/golang-website.png)


