# Meridian Voyage Internship Project

This is a full-stack web application built as part of an internship project. The application consists of:
- **Frontend**: A React-based user interface.
- **Backend**: A Python Flask API that interacts with a PostgreSQL database.
- **Database**: PostgreSQL for storing user data.
- **Docker**: The entire application is containerized using Docker for easy deployment.

## Features

- Fetches data from a PostgreSQL database via a Python backend API.
- Displays the data in a clean and responsive React frontend.
- Fully containerized with Docker for seamless development and deployment.

## Prerequisites

Before running the application, ensure you have the following installed:
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Installation and Usage

### Option 1: Run Locally with Docker

1. Clone the repository:
   ```bash
   git clone https://github.com/Karthik-099/Meridian-Voyage.git
   cd Meridian-Voyage
2.Build and start the application using Docker Compose:
  
  docker-compose up --build  .
  
3.Access the application.
    Frontend: http://localhost:3000   .
    Backend API: http://localhost:5000/data   .


# Pull Pre-Built Docker Images
1.Pull the images:
   docker pull karthik75/frontend:latest  .
   docker pull karthik75/backend:latest  .
2.Update the docker-compose.yml file to use the pulled images
  
    services:
    db:
    image: postgres:13-alpine
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    backend:
    image: karthik75/backend:latest
    ports:
      - "5000:5000"
    depends_on:
      - db
    frontend:
    image: karthik75/frontend:latest
    ports:
      - "3000:80"
    depends_on:
      - backend
    volumes:
    postgres_data:

3.Start the application:
   docker-compose up .
