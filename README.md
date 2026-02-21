# KG Study Tool - Docker Compose Setup

This repository contains the Docker Compose orchestration for the KG Study Tool application.

## About the Application

KG Study Tool transforms scattered course materials (PDFs, slides, notes) into interactive knowledge graphs. Upload documents to visualize how concepts, theories, methods, and people relate across your entire course.

### Core Features

- Schema-constrained AI extraction using LinkML ontology
- Support for PDF, PowerPoint, and DOCX documents
- Entity resolution to merge duplicate concepts
- Interactive graph visualization with d3.js
- Click nodes to jump to source material
- Study path generation based on prerequisite chains
- Export graphs as PNG or PDF

### Knowledge Graph Schema

**Entity Types:**
- Concept: Core ideas and topics
- Theory: Scientific frameworks and paradigms
- Person: Researchers and notable figures
- Method: Techniques and procedures

**Relationship Types:**
- prerequisite_of: Must learn A before B
- example_of: A is a concrete instance of B
- contrasts_with: A is similar but different from B
- located_in: A is found within or part of B
- produces: A creates B as output
- consumes: A uses B as input
- applies_to: Theory or method applies to a domain

## Technology Stack

- Schema Definition: LinkML + YAML
- Model Generation: LinkML to Pydantic
- Document Parsing: PyPDF2, python-docx, pdfplumber
- AI Extraction: OpenAI GPT-4o Function Calling
- Validation: Pydantic Models
- Graph Storage: NetworkX + DuckDB
- Visualization: d3.js + React
- Backend: FastAPI + Python
- DevOps: Docker + GitHub Actions

## Quick Start with Docker Compose

### Prerequisites

- Docker
- Docker Compose
- OpenAI API key (set in .env file)

### Setup

1. Clone the repository

```bash
git clone <repository-url>
cd DockerCompose
```

2. Create environment file

Create a `.env` file in the root directory:

```bash
# OpenAI API Configuration
OPENAI_API_KEY=your_api_key_here

# Application Configuration
API_HOST=0.0.0.0
API_PORT=8000
```

3. Start the application

```bash
docker-compose up -d
```

This will start:
- Backend service on http://localhost:8000
- Frontend service on http://localhost:3000

4. Access the application

Open your browser and navigate to http://localhost:3000

### Stopping the Application

```bash
docker-compose down
```

### Viewing Logs

```bash
# View all logs
docker-compose logs -f

# View specific service logs
docker-compose logs -f backend
docker-compose logs -f frontend
```

## Project Structure

``
.
compose.yml           # Docker Compose configuration
.env                 # Environment variables (not tracked)
.gitignore          # Git ignore rules
README.md            # This file
LICENSE              # Apache 2.0 license
```

## Services

### Backend

- Image: ghcr.io/poly-prompt-team-7/backend-placeholder:latest
- Port: 8000
- Provides REST API for document upload, extraction, and graph queries

### Frontend

- Image: ghcr.io/yourorg/frontend-placeholder:latest
- Port: 3000
- React-based UI for document upload and graph visualization
- Connects to backend via API_URL environment variable

## Development

For full development setup (backend code, frontend code, schema definitions), refer to the main application repositories.

## License

Apache 2.0
