## Developing WordPress sites with Docker :point_down:

#### :file_folder: Project Structure:
- app/ – The WordPress application files are in this directory.
- bin/ – Useful command-line scripts
- data/ – MySQL dump files go here.
- docker/ – Files required by the Docker setup are in this directory.
- README.md – Every project needs a README!
- docker-compose.yml – Development orchestration config file.

*Recommended add "data" folder to .gitignore*

## :floppy_disk: Docker
Docker Install: https://docs.docker.com/install/
Docker Compose Install: https://docs.docker.com/compose/install/

#### Hostname
Set up a host name pointing at 127.0.0.1 in your /etc/hosts for the dev site.
```bash
127.0.0.1 example.loc
```

####  Docker Commands:
Start up with
```bash
$ docker-compose up
```

To Tear Down
```bash
$ docker-compose down --volumes
```

To rebuild the containers:
```bash
$docker-compose up --force-recreate --build
```

To delete the db_data volume
```bash
$ docker-compose down -v
```

After building the images you can go to http://example.loc (if you set up a hostname) or go to 127.0.0.1:80 and start work. Put WordPress in to app/ and the install process will start and create a database for you.

## :cd: Installing WP
![DB config](https://raw.githubusercontent.com/welch08/wp_docker/master/db_settings.jpg "DB config")

## :books: PhpMyAdmin
Go to http://127.0.0.1:8080 (http://localhost:8080)
**login: ** root
**passowrd: **password

------------
Recommended to update wp-config.php (/app/wp-config.php)
```php
/** The name of the database for WordPress */
define('DB_NAME', $_SERVER['DB_NAME'] ?? $_ENV['DB_NAME'] ?? null);

/** MySQL database username */
define('DB_USER', $_SERVER['DB_USER'] ?? $_ENV['DB_USER'] ?? null);

/** MySQL database password */
define('DB_PASSWORD', $_SERVER['DB_PASSWORD'] ?? $_ENV['DB_PASSWORD'] ?? null);

/** MySQL hostname */
define('DB_HOST', $_SERVER['DB_HOST'] ?? $_ENV['DB_HOST'] ?? null);

// ... later ...

define('WP_DEBUG', (bool) ($ENV['WP_DEBUG'] ?? false));
define('WP_DEBUG_LOG', (bool) ($ENV['WP_DEBUG'] ?? false));
```
The environment variables we set in docker-compose.yml are used here.

------------
# Successful Development! :muscle:
