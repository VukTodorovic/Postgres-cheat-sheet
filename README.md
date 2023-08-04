# Postgres Cheat Sheet
Cheat sheet for PostgreSQL CLI tool

## Install PostgreSQL
```bash
sudo apt install postgresql postgresql-contrib
```

## Switch to 'postgres' user
```bash
sudo -i -u postgres
```

## Start PostgreSQL CLI
```bash
psql
```

## Create new database
```bash
CREATE DATABASE your_database
```

## Make sure to enable it so it starts on startup (even though this is default behaviour)
```bash
sudo systemctl enable postgresql
```

## Set password
```bash
\password your_postgres_password
```

## Connection URI
```bash
postgresql://postgres:your_postgres_password@your_server_ip:5432/your_database
```

## List all databases
```bash
\l
```

## Connect to the database
```bash
\c your_database
```

## List all tables inside database
```bash
\dt
```

## Describe a table
```bash
\d+ products
```

## Backup database
```bash
pg_dump -U postgres -d your_database > backup.sql # Local
pg_dump --verbose --no-owner --no-acl "<connection_string>" -f output_file #Remote, koristiti verbose uvek!
```


## Restore database from a backup
```bash
dropdb your_database
createdb your_database
psql -U postgres -d your_database < backup.sql # Local
psql --verbose "<connection_string>" -f input_file # Remote
```


## Restore can be done with using following params to just load or append data without making changes to the schema
```bash
--data-only
--inserts
```

## Exit PostgreSQL CLI
```bash
\q
```

## Force go to superuser
```bash
su
```

## Try logging out to go back to root
```bash
exit
```
