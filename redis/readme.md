# Redis Docker Setup with RedisInsight
This repository contains the Docker Compose configuration to run **Redis** and **RedisInsight** in a containerized environment. It provides an easy way to set up a local Redis server with a graphical interface for managing Redis data using RedisInsight.

# Table of Contents

- [Redis Docker Setup with RedisInsight](#redis-docker-setup-with-redisinsight)
- [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [How to Connect to Redis](#how-to-connect-to-redis)
    - [From Local Machine](#from-local-machine)
    - [From Another Container on the Same Docker Network](#from-another-container-on-the-same-docker-network)
    - [From a Container on a Different Docker Network](#from-a-container-on-a-different-docker-network)
    - [From Any Device on the Local Network](#from-any-device-on-the-local-network)
  - [RedisInsight GUI](#redisinsight-gui)
    - [Access UI](#access-ui)
    - [Connecting Redis Database to RedisInsight](#connecting-redis-database-to-redisinsight)
  - [Connecting via redis-cli](#connecting-via-redis-cli)
  - [Stopping and Restarting](#stopping-and-restarting)
  - [Conclusion](#conclusion)

---

## Installation

<div style="padding: 4px 8px; border-radius: 4px; margin-bottom: 4px; background-color: #fbe9e7; color: #f04438">
    <strong>Warning:</strong> Before proceeding, ensure that Docker or the Docker daemon is running on your device.
</div>

If Docker is not running, start the Docker service or open the Docker Desktop application to begin.

1. Navigate to the `docker-database/redis` directory.
2. Run Docker Compose to start Redis and RedisInsight containers:
    ```bash
    docker compose up -d
    ```

    This command will download the necessary images, create containers, and start them in the background.

---

## How to Connect to Redis

### From Local Machine
   Use the following host and port to connect to Redis from any Redis client:
   ```
   Host: <HOST_IP>
   Port: 6379
   ```
   **Example**:  
   If you're using a GUI client like TablePlus, RedisInsight, or another Redis client:
   ```
   Host: <HOST_IP>  # Replace with your machine's IP, e.g., 192.168.x.x or 127.0.0.1 or localhost
   Port: 6379
   ```

### From Another Container on the Same Docker Network
   Use the following host and port:
   ```
   Host: redis
   Port: 6379
   ```
   Since both containers are on the same Docker network, `redis` is automatically resolvable as the hostname.

### From a Container on a Different Docker Network
   Use the host and port of the host machine running Docker:
   ```
   Host: <HOST_IP>
   Port: 6379
   ```
   **Example**:  
   ```
   Host: <HOST_IP>  # Replace with the local network IP of the host machine's IP, e.g., 192.168.x.x
   Port: 6379
   ```

### From Any Device on the Local Network
   Use the following:
   ```
   Host: <HOST_IP>  # The IP address of the host machine on the local network
   Port: 6379
   ```
   Ensure that the host's firewall allows incoming connections on port `6379`.

---

## RedisInsight GUI
### Access UI
Once you’ve started the containers, you can access RedisInsight by navigating to `http://localhost:5540` or `http://127.0.0.1:5540` or `<HOST_IP>::5540` in your web browser. This web interface allows you to:

- View and manage Redis keys and data structures.
- Monitor Redis performance and key statistics.
- Perform Redis operations like querying and deleting keys.

### Connecting Redis Database to RedisInsight
To connect your Redis database to RedisInsight via the web interface:

1. Open RedisInsight by navigating to `http://localhost:5540` or `http://127.0.0.1:5540` in your browser.
2. Click on **"Add Redis Database"** or the **"+"** icon.
3. In the "Add Database" dialog:
   - **Host**: Enter `redis`
   - **Port**: Set this to `6379`.
   - **Password**: Leave this blank unless you have set a password for your Redis instance.
4. Click **"Test Connection"** to verify that the connection is successful. If the test is successful, RedisInsight will show a "Connection successful" message.
5. If the test connection is successful, click **"Connect"** to finalize the setup.

Once connected, you will be able to see and interact with your Redis data directly from the RedisInsight UI.

---

## Connecting via redis-cli

You can also connect directly to Redis from your terminal using the `redis-cli` tool.

```bash
redis-cli -h <HOST_IP> -p 6379
```

**Example**:
```bash
redis-cli -h 127.0.0.1 -p 6379
```

This will provide direct access to the Redis CLI for quick commands and queries.

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

This Docker setup provides a simple, self-contained Redis environment with an easy-to-use web interface via RedisInsight. You can quickly set up Redis for development and connect multiple services to it, all while having the convenience of managing data visually.
