# School Project Docker Setup

A containerized school management application built with Flask, PostgreSQL, and Cloudflare tunnel for secure access.

## 🏗️ Architecture

This project consists of three main services:

- **Flask Application** (`flask-app`): The main web application
- **PostgreSQL Database** (`db`): Data persistence layer
- **Cloudflare Tunnel** (`cloudflared`): Secure tunnel for external access

## 📋 Prerequisites

Before running this project, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/) (version 20.10 or higher)
- [Docker Compose](https://docs.docker.com/compose/install/) (version 2.0 or higher)

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/CyberLeafy/school_management_system_docker.git
   cd school_management_system_docker
   ```

2. **Start the services**
   ```bash
   docker-compose up -d
   ```

3. **Access the application**
   - Local access: http://localhost:8000
   - External access: Via Cloudflare tunnel (URL will be displayed in logs)

## 🔧 Configuration

### Environment Variables

The application uses the following environment variables:

| Variable | Description | Default Value |
|----------|-------------|---------------|
| `POSTGRES_USER` | PostgreSQL username | `postgres` |
| `POSTGRES_PASSWORD` | PostgreSQL password | `aadi7525` |
| `POSTGRES_DB` | Database name | `school_db` |
| `DATABASE_URL` | Full database connection string | `postgresql+psycopg2://postgres:aadi7525@db:5432/school_db` |

### Ports

- **Flask App**: 8000 (mapped to host port 8000)
- **PostgreSQL**: 5432 (mapped to host port 5432)

## 📊 Services Details

### Flask Application
- **Image**: `cyberleafy/flask-school-app:latest`
- **Port**: 8000
- **Dependencies**: PostgreSQL database
- **Purpose**: Main web application for school management

### PostgreSQL Database
- **Image**: `postgres:15`
- **Port**: 5432
- **Volume**: `pgdata` for data persistence
- **Purpose**: Data storage for the school management system

### Cloudflare Tunnel
- **Image**: `cloudflare/cloudflared:latest`
- **Purpose**: Provides secure external access to the application
- **Dependencies**: Flask application

## 🛠️ Development Commands

### Start services in detached mode
```bash
docker-compose up -d
```

### View logs
```bash
# View all logs
docker-compose logs

# View specific service logs
docker-compose logs flask-app
docker-compose logs db
docker-compose logs cloudflared
```

### Stop services
```bash
docker-compose down
```

### Stop and remove volumes (⚠️ This will delete all data)
```bash
docker-compose down -v
```

### Rebuild services
```bash
docker-compose up --build
```

## 🔍 Troubleshooting

### Common Issues

1. **Port already in use**
   - Check if ports 8000 or 5432 are already in use
   - Modify port mappings in `docker-compose.yml` if needed

2. **Database connection issues**
   - Ensure the database service is running: `docker-compose ps`
   - Check database logs: `docker-compose logs db`

3. **Flask app not accessible**
   - Verify the Flask service is running: `docker-compose logs flask-app`
   - Check if the application is binding to the correct host/port

### Useful Commands

```bash
# Check service status
docker-compose ps

# Access database directly
docker-compose exec db psql -U postgres -d school_db

# Access Flask app container
docker-compose exec flask-app bash

# View resource usage
docker stats
```

## 📁 Project Structure

```
school_project_docker/
├── docker-compose.yml    # Docker Compose configuration
├── readme.md            # This file
└── (other project files)
```

## 🔒 Security Notes

- **Database Password**: The default password `aadi7525` should be changed in production
- **Environment Variables**: Consider using Docker secrets or environment files for sensitive data
- **Network Security**: The Cloudflare tunnel provides secure external access

<!-- ## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test with `docker-compose up --build`
5. Submit a pull request -->

<!-- ## 📝 License

This project is part of a school assignment. Please check with your institution for usage guidelines. -->

## 🆘 Support

If you encounter any issues:

1. Check the troubleshooting section above
2. Review the Docker and Docker Compose logs
3. Ensure all prerequisites are properly installed
4. Contact your instructor or project maintainer

---


**Note**: This is a development setup. For production deployment, additional security measures and configuration optimizations should be implemented.


## 🧑‍💼 Author

- [@CyberLeafy](https://www.github.com/cyberleafy)
- Aditya Jaiswal

---

<div align="center">
Made with ❤️ for Jawahar Navodaya Vidyalaya (Gopalganj)
</div>

