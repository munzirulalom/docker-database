# MySQL Docker Setup with Adminer

This directory contains a Docker Compose setup for **MySQL**, a popular open-source relational database, and **Adminer**, a lightweight web-based database management tool.

---

# Table of Contents

- [MySQL Docker Setup with Adminer](#mysql-docker-setup-with-adminer)
- [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Access MySQL](#access-mysql)
    - [From Local Machine](#from-local-machine)
    - [From Another Container on the Same Docker Network](#from-another-container-on-the-same-docker-network)
    - [From a Container on a Different Docker Network](#from-a-container-on-a-different-docker-network)
    - [From Any Device on the Local Network](#from-any-device-on-the-local-network)
  - [Access Adminer](#access-adminer)
    - [Access UI](#access-ui)
    - [Connecting MySQL Database to Adminer](#connecting-mysql-database-to-adminer)
  - [Connecting via MySQL CLI (Command Line)](#connecting-via-mysql-cli-command-line)
  - [Stopping and Restarting](#stopping-and-restarting)
  - [Conclusion](#conclusion)

---

## Installation

> ⚠️ **Make sure Docker or the Docker daemon is running on your device before proceeding.**

1. Navigate to the `docker-database/mysql` directory:

   ```bash
   cd docker-database/mysql
   ```

2. Start the MySQL and Adminer containers:

   ```bash
   docker compose up -d
   ```

3. Verify that the containers are running:

   ```bash
   docker ps
   ```

   This command should list the `mysql` and `adminer` containers as running.

---

## Access MySQL

You can connect to the MySQL database using any MySQL client, such as **MySQL Workbench**, **TablePlus**, or **MySQL CLI**.

> **Note**: The default database created is `my_database`. You can modify this in the `docker-compose.yml` file if needed or create a new database after the setup to fit your needs.

### From Local Machine

Use the following host and port to connect to MySQL from any MySQL client:

```
Host: <HOST_IP>  # Replace with your machine's IP, e.g., 192.168.x.x or 127.0.0.1 or localhost
Port: 3306
Database: my_database
User: admin
Password: password
```

### From Another Container on the Same Docker Network

Use the following host and port:

```
Host: mysql
Port: 3306
Database: my_database
User: admin
Password: password
```

Since both containers are on the same Docker network, `mysql` is automatically resolvable as the hostname.

### From a Container on a Different Docker Network

Use the host and port of the host machine running Docker:

```
Host: <HOST_IP>  # Replace with the local network IP of the host machine, e.g., 192.168.x.x
Port: 3306
Database: my_database
User: admin
Password: password
```

### From Any Device on the Local Network

Use the following:

```
Host: <HOST_IP>  # The IP address of the host machine on the local network
Port: 3306
Database: my_database
User: admin
Password: password
```

Ensure that the host's firewall allows incoming connections on port `3306`.

---

## Access Adminer

### Access UI

Adminer is a web-based database management tool for MySQL. Once the containers are running, you can access Adminer from your browser.

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

### Connecting MySQL Database to Adminer

1. Open your browser and go to `http://localhost:8080` or `http://127.0.0.1:8080` or `<HOST_IP>:8080`.
2. In the Adminer interface, enter the following details:
   - **System**: MySQL
   - **Server**: `mysql` (or `<HOST_IP>` if connecting from another device)
   - **Username**: `admin`
   - **Password**: `password`
   - **Database**: `my_database`
3. Click **"Login"** to access and manage your MySQL database.

---

## Connecting via MySQL CLI (Command Line)

From a terminal on the host machine:

```bash
mysql -h <HOST_IP> -P 3306 -u admin -p my_database
```

Example:

```bash
mysql -h 127.0.0.1 -P 3306 -u admin -p my_database
```

After running this command, you will be prompted to enter the password (`password`).

This provides direct access to MySQL for running SQL commands and managing the database.

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

## Conclusion

With this setup, you have a fully functional MySQL database and a user-friendly interface through Adminer for managing and interacting with your data. This environment is ideal for local development, testing, and learning purposes. Feel free to customize the configuration as needed to suit your project requirements.

Happy coding! 🚀