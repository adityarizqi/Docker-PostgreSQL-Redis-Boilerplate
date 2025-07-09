# 1. PostgreSQL Tuning (via PGTune)
You can generate an optimized configuration using PGTune tool (https://pgtune.leopard.in.ua) based on your server specifications. Example tuning output:
```SQL
ALTER SYSTEM SET max_connections = '200';
ALTER SYSTEM SET shared_buffers = '512MB';
ALTER SYSTEM SET effective_cache_size = '1536MB';
ALTER SYSTEM SET maintenance_work_mem = '128MB';
ALTER SYSTEM SET checkpoint_completion_target = '0.9';
ALTER SYSTEM SET wal_buffers = '16MB';
ALTER SYSTEM SET default_statistics_target = '100';
ALTER SYSTEM SET random_page_cost = '1.1';
ALTER SYSTEM SET effective_io_concurrency = '200';
ALTER SYSTEM SET work_mem = '2520kB';
ALTER SYSTEM SET huge_pages = 'off';
ALTER SYSTEM SET min_wal_size = '1GB';
ALTER SYSTEM SET max_wal_size = '4GB';
```

# 2. Apply Tuning Settings in Docker Container
Follow these steps:
- Make sure the PostgreSQL container is running.
- Access the PostgreSQL shell inside the container:
```bash 
docker exec -it postgres_db psql -U ${POSTGRES_USER}
```
- Paste and run the SQL tuning statements listed above.
- Restart the PostgreSQL container to apply the changes:
```bash
docker restart postgres_db
```
**Note:** Replace `${POSTGRES_USER}` with your actual container name and PostgreSQL username.