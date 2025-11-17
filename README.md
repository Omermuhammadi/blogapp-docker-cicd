# BlogApp - Dockerized Web Application

# BlogApp - ASSIGNMENT COMPLETED ✅

A simple blog application built with Node.js, Express, and PostgreSQL.

## 🎯 Successfully Implemented:
- ✅ Docker containerization
- ✅ Jenkins CI/CD Pipeline  
- ✅ GitHub webhook automation
- ✅ AWS EC2 deployment
- ✅ Database persistence with volumes
- ✅ Full application functionality
- 

**Live Demo**: http://18.212.93.75:3000
**Jenkins Pipeline**: http://18.212.93.75:8080

Last Updated: November 6, 2025 - Pipeline Test

## Features
- User registration and authentication
- Create, read blog posts
- Comment system
- Session management
- Responsive web interface

## Technology Stack
- **Backend**: Node.js, Express.js
- **Database**: PostgreSQL
- **Frontend**: EJS templating
- **Containerization**: Docker, Docker Compose
- **CI/CD**: Jenkins
- **Deployment**: AWS EC2

## Quick Start with Docker

### Prerequisites
- Docker Desktop installed
- Git

### Local Development
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd blogApp
   ```

2. Start the application:
   ```bash
   docker-compose up -d
   ```

3. Access the application:
   - Web app: http://localhost:3000
   - Database: localhost:5432

### Environment Variables
Copy `.env.example` to `.env` and configure:
```
NODE_ENV=development
PORT=3000
SESSION_SECRET=your-secret-key
DB_HOST=db
DB_PORT=5432
DB_NAME=blogapp
DB_USER=bloguser
DB_PASSWORD=blogpass123
```

## Project Structure
```
blogApp/
├── app.js                 # Main application file
├── package.json          # Dependencies and scripts
├── Dockerfile            # Container configuration
├── docker-compose.yml    # Multi-container setup
├── docker-entrypoint.sh  # Container startup script
├── config/               # Database configuration
├── models/               # Sequelize models
├── migrations/           # Database migrations
└── views/                # EJS templates
```

## Docker Commands
- `docker-compose up -d` - Start containers in background
- `docker-compose down` - Stop and remove containers
- `docker-compose logs web` - View application logs
- `docker-compose exec web npm run migrate` - Run migrations

## CI/CD Pipeline
This project includes Jenkins automation for:
- Automated builds on Git push
- Docker image creation
- Deployment to AWS EC2
- Build notifications

## Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test with Docker
5. Submit a pull request

## License
MIT License
