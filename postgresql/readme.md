# PostgreSQL Docker Setup with Adminer

This directory contains a Docker Compose setup for **PostgreSQL**, a powerful open-source relational database, and **Adminer**, a lightweight web-based database management tool.

---

# Table of Contents

- [PostgreSQL Docker Setup with Adminer](#postgresql-docker-setup-with-adminer)
- [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Access PostgreSQL](#access-postgresql)
    - [From Local Machine](#from-local-machine)
    - [From Another Container on the Same Docker Network](#from-another-container-on-the-same-docker-network)
    - [From a Container on a Different Docker Network](#from-a-container-on-a-different-docker-network)
    - [From Any Device on the Local Network](#from-any-device-on-the-local-network)
  - [Access Adminer](#access-adminer)
    - [Access UI](#access-ui)
    - [Connecting PostgreSQL Database to Adminer](#connecting-postgresql-database-to-adminer)
  - [Connecting via psql (Command Line)](#connecting-via-psql-command-line)
  - [Stopping and Restarting](#stopping-and-restarting)
  - [Conclusion](#conclusion)

---

## Installation

> ⚠️ Make sure Docker or the Docker daemon is running on your device before proceeding.

1. Navigate to the `docker-database/postgresql` directory:

   ```bash
   cd docker-database/postgresql
   ```

2. Start the PostgreSQL and Adminer containers:

   ```bash
   docker compose up -d
   ```

3. Verify that the containers are running:

   ```bash
   docker ps
   ```

   This command should list the `postgres` and `adminer` containers as running.

---

## Access PostgreSQL

You can connect to the PostgreSQL database using any PostgreSQL client, such as **pgAdmin**, **TablePlus**, or **psql**.

> **Note:** The default database created is `my_database`. You can change this in the `docker-compose.yml` file if needed, or create a new database after the setup to fit your requirements.

### From Local Machine

Use the following host and port to connect to PostgreSQL from any PostgreSQL client:

```
Host: <HOST_IP>  # Replace with your machine's IP, e.g., 192.168.x.x or 127.0.0.1 or localhost
Port: 5432
Database: my_database
User: admin
Password: password
```

### From Another Container on the Same Docker Network

Use the following host and port:

```
Host: postgres
Port: 5432
Database: my_database
User: admin
Password: password
```

Since both containers are on the same Docker network, `postgres` is automatically resolvable as the hostname.

### From a Container on a Different Docker Network

Use the host and port of the host machine running Docker:

```
Host: <HOST_IP>  # Replace with the local network IP of the host machine, e.g., 192.168.x.x
Port: 5432
Database: my_database
User: admin
Password: password
```

### From Any Device on the Local Network

Use the following:

```
Host: <HOST_IP>  # The IP address of the host machine on the local network
Port: 5432
Database: my_database
User: admin
Password: password
```

Ensure that the host's firewall allows incoming connections on port `5432`.

---

## Access Adminer

### Access UI

Adminer is a web-based database management tool for PostgreSQL. Once the containers are running, you can access Adminer from your browser.

```
http://localhost:8080
```
or
```
http://127.0.0.1:8080
```
or
```
<HOST_IP>:8080
```

### Connecting PostgreSQL Database to Adminer

1. Open your browser and go to `http://localhost:8080` or `http://127.0.0.1:8080` or `<HOST_IP>:8080`.
2. In the Adminer interface, enter the following details:
   - **System**: PostgreSQL
   - **Server**: `postgres` (or `<HOST_IP>` if connecting from another device)
   - **Username**: `admin`
   - **Password**: `password`
   - **Database**: `my_database`
3. Click **"Login"** to access and manage your PostgreSQL database.

---

## Connecting via psql (Command Line)

From a terminal on the host machine:

```bash
psql -h <HOST_IP> -p 5432 -U admin -d my_database
```

Example:

```bash
psql -h 127.0.0.1 -p 5432 -U admin -d my_database
```

This provides direct access to PostgreSQL for running SQL commands and managing the database.

---

## Stopping and Restarting

To stop the containers:
```bash
docker compose down
```

To restart the containers:
```bash
docker compose up -d
```

---

Here's the conclusion section for the PostgreSQL `README.md` file:

---

## Conclusion

With this setup, you have a fully functional PostgreSQL database and a user-friendly interface through Adminer for managing and interacting with your data. This environment is ideal for local development, testing, and learning purposes. Feel free to customize the configuration as needed to suit your project requirements.

Happy coding! 🚀