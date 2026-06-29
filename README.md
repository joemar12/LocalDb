## Setup Instructions

### Set the password from host environment variables:

**Windows (PowerShell):**
```powershell
$env:MSSQL_PASSWORD = "YourStrong@Password123"
docker-compose up -d
```

**Windows (Command Prompt):**
```cmd
set MSSQL_PASSWORD=YourStrong@Password123
docker-compose up -d
```

**Linux/Mac (Bash):**
```bash
export MSSQL_PASSWORD="YourStrong@Password123"
docker-compose up -d
```

**Using .env file (optional, for easy reference):**
```
MSSQL_PASSWORD=YourStrong@Password123
```

## How it Works:
- Docker Compose reads `MSSQL_PASSWORD` from host environment variables
- Creates a Docker secret from that value
- Mounts it as `/run/secrets/db_password` in the container
- SQL Server reads the password from the secret file
- Password is never stored on disk or in the image

## Connection Details (MS SQL Server):
- **Server**: localhost,1433
- **Username**: sa
- **Password**: (from MSSQL_PASSWORD env var)

## Connection Details (PostgreSQL)
- **Server**: localhost,5432
- **Username**: (from POSTGRES_USER env var)
- **Password**: (from POSTGRES_PASSWORD env var)

## Verify the setup:
```powershell
docker-compose ps
```

## Important:
- Set `MSSQL_PASSWORD` before running `docker-compose up`
- For **postgres**, the instructions are pretty much the same, but set the `POSTGRES_PASSWORD` and `POSTGRES_USER` variables in the `.env` file.
