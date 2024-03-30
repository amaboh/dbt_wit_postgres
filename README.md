**Custom ELT Project**

This project demonstrates a simple Extract, Load, Transform (ELT) process using DBT, with Docker, PostgreSQL, and a Python script.

**Components:**

- **docker-compose.yaml:** Orchestrates three Docker containers:
  - `source_postgres`: Source PostgreSQL database with sample data.
  - `destination_postgres`: Destination PostgreSQL database.
  - `elt_script`: Container running the ELT Python script.
- **elt_script/elt_script.py:**
  - Waits for the source database to become available.
  - Dumps data via `pg_dump`.
  - Loads data into the destination database using `psql`.
- **source_db_init/init.sql:** Sample data initialization for the source database.

**Workflow:**

1. `docker-compose up` brings up all containers.
2. The `elt_script.py` automatically executes the ELT process.
3. Access source and destination databases on ports 5433 and 5434.

**Automation (CRON):**

This branch includes a CRON job to automate the ELT process at scheduled intervals. Customize the schedule within the `elt_script/Dockerfile`.

**Getting Started:**

1. Install Docker and Docker Compose.
2. Clone this repository.
3. Run `docker-compose up`.
