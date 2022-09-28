# Discorder Website Concept
A proof of concept website built for an eSports team called "Discorder"

## Deployment
`bin/deploy` - Builds and brings up docker-compose stack

## Database environment variables
Rename **.env-example** to **.env** and replace the contents with your required variables for the database

## Database
### Persistence
A volume called db is created and all logs are stored there

### Dump database from host
`mysqldump --no-tablespaces -h 0.0.0.0 -P 3306 -u MYSQL_USER -p MYSQL_DATABASE > $(date +"%y-%m-%d_%H:%M:%S").sql`

### Import database from local file
`mysql -h 0.0.0.0 -P 3306 -u MYSQL_USER -p MYSQL_DATABASE < FILE.sql`