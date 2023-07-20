# PostgreSQL and pgAdmin Installation Guide using Docker Compose

This repository contains a Docker Compose configuration to help you quickly set up a PostgreSQL database and pgAdmin web interface for easy database management.

## What is Docker?

Docker is an open-source platform that enables developers to automate the deployment, scaling, and management of applications using containerization technology. Containers are lightweight, isolated environments that package applications and their dependencies, ensuring consistent execution across various environments.

## Prerequisites

Before getting started, ensure you have the following prerequisites installed on your system:

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

## Ensure Installation Completes

To verify that the installation has completed successfully and PostgreSQL is running:

1. Open pgAdmin in your web browser (`localhost:5050`).

2. On the left-hand side of the pgAdmin interface, right-click on the "Servers" option under the "Browser" section.

3. Select "Register Server" from the context menu.

4. In the "General" tab, provide a name for your server (e.g., My PostgreSQL Server).

5. Switch to the "Connection" tab and enter the following details:

   - Host name/address: `db`
   - Port: `5432`
   - Username: `root`
   - Password: `Root` (Note the capital "R")

6. Click the "Save" button to add the server.

7. In the pgAdmin interface, navigate to `Server -> db -> Database -> test_db`. Right-click on the `test_db` database and select "Query Tool" to open a new tab.

8. Copy and paste the following SQL query into the Query Tool tab:

```sql
CREATE TABLE accounts (
    user_id serial PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(50) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_on TIMESTAMP NOT NULL,
    last_login TIMESTAMP
);
```

9. Execute the query by clicking the "Execute" button or pressing `F5`.

10. To ensure that the table was created successfully, navigate to `Server -> db -> Database -> test_db -> Schemas -> public -> Tables`. You should see the `accounts` table listed.

If you can see the `accounts` table, congratulations! You have successfully completed the installation and configuration of PostgreSQL and pgAdmin using Docker Compose.

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

## Conclusion

Congratulations! You have successfully set up PostgreSQL and pgAdmin using Docker Compose. Now you can manage your databases with ease through the pgAdmin web interface. Docker's containerization technology provides a consistent and efficient way to develop, deploy, and manage applications across different environments.

Happy coding!