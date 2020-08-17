# 1. Install postgres in environment

``` bash
# Create the file repository configuration:
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

# Import the repository signing key:
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

# Update the package lists:
sudo apt-get update

# Install the latest version of PostgreSQL.
# If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':
sudo apt-get -y install postgresql
```


# 2. Run to start test cluster
```
sudo systemctl start postgresql@12-main  
```

# 3. Log into cluster
```
sudo -u postgres psql
```

# 4. Alter Password for postgres user
```
ALTER ROLE postgres PASSWORD '123';
```

# 5. Create database and make postgres the owner
```
CREATE DATABASE testdb OWNER postgres
```

# 6. After migration run commands in cluster to verify that migration was successful
```
# Connect to testdb
\c testdb
# Describe table
\d tutorials_tutorial
```
