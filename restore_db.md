## PostgreSQL Database Restore Using Docker
### 1. Duplicate Your Docker Compose File

Copy your existing `docker-compose.yaml` file and name it `docker-compose.database.yml`:

```bash
cp docker-compose.yaml docker-compose.database.yml
```

### 2. Edit the Compose File
Open `docker-compose.database.yml` and remove all services except the PostgreSQL service.

Save and close the file.

### 3. Start the PostgreSQL Container
```bash 
docker compose -f docker-compose.database.yml up -d
```

### 4. Prepare Your SQL Backup
Ensure your SQL backup file is ready, e.g., backup.sql.

### 5. Restore the Backup into PostgreSQL
- Find the Container Name or ID
Run the following command to list running containers `docker ps`

Look for the name or ID of the PostgreSQL container.

- Copy the Backup File into the Container
```bash 
docker cp backup.sql <postgres_container>:/backup.sql
```

- Run the Restore Command Inside the Container
```bash 
docker exec -i <postgres_container> psql -U postgres -d mydb -f /backup.sql
```

`-U postgres`: Replace if you use a different PostgreSQL user.
`-d mydb`: Replace with your actual database name.