# Main N8N Application.
AI-driven workflow automation using n8n to orchestrate inference tasks, APIs, and local models.

# n8n Deployment Instructions

## Prerequisites
- Docker and Docker Compose installed
- External Docker network named `infernet` (create with `docker network create infernet` if it doesn't exist)
- `.env.production` file with your secrets and configuration (copy from `.env-example` and fill in your values)

## Deploying n8n

1. **Copy the example environment file and edit it:**
   ```bash
   cp .env-example .env.production
   # Edit .env.production and set your secrets/values
   ```

2. **Create the external Docker network (if not already created):**
   ```bash
   docker network create infernet
   ```

3. **Start the n8n stack:**
   ```bash
   docker compose -f docker-compose.production.yaml up -d
   ```
   This will start n8n and its PostgreSQL database in the background.

4. **Access n8n:**
   - Open your browser and go to `http://localhost:5678` (or the host/port you configured).

## Stopping and Removing the Stack

To stop and remove the containers (but keep your data volumes):
```bash
docker compose -f docker-compose.production.yaml down
```

- Your workflow state and database will persist because they are stored in Docker volumes.

---

For more information, see the [n8n documentation](https://docs.n8n.io/).
