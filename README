# Docker and Docker Compose Setup for PostgreSQL and pgAdmin

This repository provides a Docker Compose configuration to quickly set up a PostgreSQL database and pgAdmin web interface for easy database management.

## What is Docker?

Docker is an open-source platform that enables developers to automate the deployment, scaling, and management of applications using containerization technology. Containers are lightweight, isolated environments that package applications and their dependencies, ensuring consistent execution across various environments.

## Prerequisites

Before getting started, make sure you have the following prerequisites installed on your system:

1. **Docker**: Install Docker on your machine by following the instructions for your specific operating system:

   - [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)
   - [Docker for macOS](https://docs.docker.com/docker-for-mac/install/)
   - [Docker for Linux](https://docs.docker.com/engine/install/)

## Installation

Follow these steps to set up PostgreSQL and pgAdmin using Docker Compose:

1. Clone this repository to your local machine or download the `docker-compose.yml` file from this repository.

2. Open a terminal or command prompt, navigate to the directory containing the `docker-compose.yml` file.

3. Run the following command to start the PostgreSQL and pgAdmin containers:

   ```bash
   docker-compose up -d
   ```

4. Docker Compose will download the required Docker images and start the containers in the background.

5. Once the containers are up and running, you can access the following services:

   - PostgreSQL: `localhost:5432`
   - pgAdmin: `localhost:5050`

6. Access the pgAdmin web interface by navigating to `localhost:5050` in your web browser. Log in using the following credentials:

   - Email: `admin@admin.com`
   - Password: `root`

7. In the pgAdmin interface, you can add a new server and manage your PostgreSQL database effortlessly.

## Stopping and Removing Containers

To stop and remove the containers while keeping the data volumes intact, use the following command:

```bash
docker-compose down
```

If you also want to remove the data volumes along with the containers, use the `--volumes` flag:

```bash
docker-compose down --volumes
```

**Note:** Be cautious when using the `--volumes` flag, as it will delete all data stored in PostgreSQL and pgAdmin.