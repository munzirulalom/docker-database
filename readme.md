# Docker Databases

This repository contains pre-configured Docker Compose setups for popular database systems to streamline local development and testing. Each database setup includes a database server and, where applicable, a web-based management tool for ease of use.

---

## Table of Contents

- [Docker Databases](#docker-databases)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Available Databases](#available-databases)
    - [1. Redis](#1-redis)
    - [2. PostgreSQL](#2-postgresql)
    - [3. MySQL](#3-mysql)
  - [Getting Started](#getting-started)
    - [Installation](#installation)
    - [Stopping and Restarting](#stopping-and-restarting)
      - [To stop the containers:](#to-stop-the-containers)
      - [To restart the containers:](#to-restart-the-containers)
  - [Accessing the Services](#accessing-the-services)

---

## Overview

This repository provides Docker Compose configurations for the following database systems:

1. **Redis** - A high-performance in-memory data structure store, with **RedisInsight** for visual management.
2. **PostgreSQL** - A powerful open-source relational database, with **Adminer** for web-based administration.
3. **MySQL** - A widely-used open-source relational database, also paired with **Adminer**.

Each setup is self-contained within its directory and ready for deployment with minimal configuration.

---

## Available Databases

### 1. Redis
- **Directory**: [`docker-database/redis`](./docker-database/redis)
- **Management Tool**: RedisInsight
- **Default Port**: 6379
- [See full README](./docker-database/redis/README.md)

### 2. PostgreSQL
- **Directory**: [`docker-database/postgresql`](./docker-database/postgresql)
- **Management Tool**: Adminer
- **Default Port**: 5432
- [See full README](./docker-database/postgresql/README.md)

### 3. MySQL
- **Directory**: [`docker-database/mysql`](./docker-database/mysql)
- **Management Tool**: Adminer
- **Default Port**: 3306
- [See full README](./docker-database/mysql/README.md)

---

## Getting Started

### Installation

> ⚠️ **Ensure Docker or the Docker daemon is running on your device before proceeding.**

1. Clone the repository:

   ```bash
   git clone https://github.com/munzirulalom/docker-databases.git
   ```

2. Navigate to the desired database directory (e.g., Redis, PostgreSQL, or MySQL):

   ```bash
   cd docker-databases/<database-name>
   ```

3. Start the services using Docker Compose:

   ```bash
   docker compose up -d
   ```

### Stopping and Restarting

#### To stop the containers:
```bash
docker compose down
```

#### To restart the containers:
```bash
docker compose up -d
```

---

## Accessing the Services

Each database has specific instructions for connecting to the database server and accessing web-based management tools:

- [Redis README](./docker-database/redis/README.md)
- [PostgreSQL README](./docker-database/postgresql/README.md)
- [MySQL README](./docker-database/mysql/README.md)

Refer to the respective `README.md` files in each directory for detailed connection instructions.

---

With this repository, you can easily set up and run popular databases for local development. Simply navigate to the desired directory, start the services, and connect to your environment. Happy coding! 🚀