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

   - PostgreSQL: `localhost:5433` (In this case we will access PostgreSQL via pgAdmin)
   - pgAdmin: `localhost:5050`

6. Access the pgAdmin web interface by navigating to `localhost:5050` in your web browser. Log in using the following credentials:

   - Email: `admin@admin.com`
   - Password: `root`
     
   <img width="1597" alt="image" src="https://github.com/TendonT52/postgreSQL-pgAdmin-installation-guide/assets/88754538/c10a1570-3242-45c4-9e78-db275ac62c7f">


7. In the pgAdmin interface, you can add a new server and manage your PostgreSQL database effortlessly.

## Ensure Installation Completes

To verify that the installation has completed successfully and PostgreSQL is running:

1. Open pgAdmin in your web browser (`localhost:5050`).

2. On the left-hand side of the pgAdmin interface, right-click on the "Servers" option under the "Browser" section.
   
3. Select "Register -> Server" from the context menu.
   
   <img width="610" alt="image" src="https://github.com/TendonT52/postgreSQL-pgAdmin-installation-guide/assets/88754538/d178f7f2-f01a-46c5-b764-760c00dcf31c">

5. In the "General" tab, provide a name for your server (e.g., My PostgreSQL Server).

6. Switch to the "Connection" tab and enter the following details:

   - Host name/address: `db`
   - Port: `5432`
   - Username: `admin`
   - Password: `root`
     
   <img width="436" alt="image" src="https://github.com/user-attachments/assets/c4795748-bc02-4510-b28d-fe2a9781c0b0">


7. Click the "Save" button to add the server.

8. In the pgAdmin interface, navigate to `Server -> db -> Database -> test_db`. Right-click on the `test_db` database and select "Query Tool" to open a new tab.

   <img width="436" alt="image" src="https://github.com/TendonT52/postgreSQL-pgAdmin-installation-guide/assets/88754538/0a4fd963-beb7-4d61-82e4-2cac697306ad">

10. Copy and paste the following SQL query into the Query Tool tab:

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

   <img width="1402" alt="image" src="https://github.com/TendonT52/postgreSQL-pgAdmin-installation-guide/assets/88754538/487c0730-42df-491b-9a85-c488738e99c1">

9. Execute the query by clicking the "Execute" button or pressing `F5`.

10. To ensure that the table was created successfully, navigate to `Server -> db -> Database -> test_db -> Schemas -> public -> Tables`. You should see the `accounts` table listed.
    
   <img width="389" alt="image" src="https://github.com/TendonT52/postgreSQL-pgAdmin-installation-guide/assets/88754538/c2d7d268-69b2-4631-a70e-1f2a53388192">

If you can see the `accounts` table, congratulations! You have successfully completed the installation and configuration of PostgreSQL and pgAdmin using Docker Compose.

## Troubleshooting

If you do not see the `accounts` table or encounter any issues, try the following steps:

1. Right-click on the "Servers" option under the "Browser" section in pgAdmin and select "Refresh." This action may update the list of databases and tables.
   
   <img width="360" alt="image" src="https://github.com/TendonT52/postgreSQL-pgAdmin-installation-guide/assets/88754538/4f5888d3-47e0-415b-8baa-9f1177da3c97">

3. Double-check the SQL query you copied into the Query Tool and ensure there are no typos or syntax errors.

4. If the issue persists, consider stopping and removing the containers using `docker-compose down`, and then try the installation process again.

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
