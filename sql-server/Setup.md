# SQL Server 2025 Docker Setup - Environment Variable Secrets

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

## Connection Details:
- **Server**: localhost,1433
- **Username**: sa
- **Password**: (from MSSQL_PASSWORD env var)

## Verify the setup:
```bash
docker-compose ps
docker logs sql-server-2025
```

## Important:
- Set `MSSQL_PASSWORD` before running `docker-compose up`
- Optional: Add `.env` to `.gitignore` if you use it for reference
- Use strong passwords (min 8 chars: uppercase, lowercase, digits, special chars)
- Change passwords regularly in production
