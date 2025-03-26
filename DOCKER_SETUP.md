# Docker Setup Guide

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Quick Start

1. Clone the repository
2. Navigate to the project directory
3. Run the following command:

```bash
docker-compose up
```

This will build and start the container. The application will be available at http://localhost:3000

## Environment Variables

To use the Google AI Studio API, you need to set up your API key. You can do this in two ways:

### Option 1: Using .env file (Recommended for development)

1. Create a `.env` file in the root directory
2. Add your API key: `VITE_GOOGLE_AI_STUDIO_KEY=your_api_key_here`
3. Rebuild the Docker container: `docker-compose up --build`

### Option 2: Using environment variables in docker-compose.yml

1. Open `docker-compose.yml`
2. Uncomment the environment variable line and set your API key:

```yaml
environment:
  - NODE_ENV=production
  - VITE_GOOGLE_AI_STUDIO_KEY=your_api_key_here
```

3. Restart the container: `docker-compose up`

## Troubleshooting

- **Container fails to start**: Check if port 3000 is already in use
- **API not working**: Verify your API key is correctly set
- **Changes not reflecting**: Try rebuilding the container with `docker-compose up --build`