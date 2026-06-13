# Use the official SQL Server 2025 image as the base
FROM mcr.microsoft.com/mssql/server:2025-latest

# Set environment variables
ENV ACCEPT_EULA=Y

# Create volume mount point for persistent data
VOLUME ["/var/opt/mssql"]

# Run SQL Server
CMD ["/opt/mssql/bin/sqlservr"]
