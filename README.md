# Where To Live

A web application that helps users find ideal cities based on customizable dimensions and weights. This project transforms census and demographic data into an interactive tool for city selection.

## Project Structure

```
where-to-live/
├── backend/           # FastAPI application
├── frontend/          # Svelte application
├── shared/            # Shared types and utilities
├── scripts/          # Data collection scripts
├── data/             # Raw data and schemas
└── docker-compose.yml
```

## Prerequisites

- Docker and Docker Compose
- Node.js 20+ (for local frontend development)
- Python 3.11+ (for local backend development)
- PostgreSQL 16+ (if running locally)

## Quick Start

1. Clone the repository:
   ```bash
   git clone [repository-url]
   cd where-to-live
   ```

2. Start the development environment:
   ```bash
   docker compose up
   ```

3. Access the applications:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:8000
   - API Documentation: http://localhost:8000/docs

## Development

### Backend (FastAPI)

- Built with FastAPI and SQLAlchemy
- Uses PostgreSQL for data storage
- Managed with uv package manager

Local setup:
```bash
cd backend
uv venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
uv pip install -e ".[dev]"
```

### Frontend (Svelte)

- Built with Svelte and TypeScript
- Uses Chart.js for visualizations
- Vite for development server

Local setup:
```bash
cd frontend
npm install
npm run dev
```

### Database

The application uses PostgreSQL for data storage. The schema includes:
- Cities table for core city data
- Dimension values table for specific metrics
- Optimized for complex scoring calculations

## Data Pipeline

1. Data Collection
   - Census API integration
   - Automated data updates
   - Data validation and transformation

2. Data Processing
   - Normalization of raw data
   - Pre-calculation of common metrics
   - Efficient storage in PostgreSQL

## Contributing

1. Create a feature branch
2. Make your changes
3. Run tests
4. Submit a pull request

## Testing

Backend:
```bash
cd backend
pytest
```

Frontend:
```bash
cd frontend
npm run test
```

## Deployment

The application can be deployed using Docker Compose:

```bash
docker compose -f docker-compose.prod.yml up -d
```

## License

[License information]
