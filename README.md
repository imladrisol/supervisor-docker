Docker - Supervisor config for (PHP) workers
============================================

Starting point configuration for running (PHP) workers inside Docker containers 
with **Supervisor** and **Supervisorctl** to manage them. 

### What's inside ?

* PHP-CLI based Docker image with Supervisor installed: located in `docker/php/Dockerfile`.
* Supervisor global configuration: located in `docker/php/conf/supervisord.conf`.
* Supervisor programs configuration: located in `docker/php/conf/supervisord-programs.conf`.

### How to use

#### Start container(s)
    
```bash
$ docker-compose build --pull
$ docker-compose up --build
```

#### List worker(s)
    
```bash
$ docker-compose exec php_worker supervisorctl status
```

#### Stop all worker(s)
    
```bash
$ docker-compose exec php_worker supervisorctl stop all
```

#### Start all worker(s)
    
```bash
$ docker-compose exec php_worker supervisorctl start all
```

#### Restart all worker(s)
    
```bash
$ docker-compose exec php_worker supervisorctl restart all
```

#### Stop container(s)

```bash
$ docker-compose stop
```

#### Cleanup  container(s)

```bash
$ docker-compose down --volumes --remove-orphans
```
### Work with supervisor
 After changes in conf we should re-read the config directory and figure out whether or not any changes has happened made to any config files
```bash
$ supervisorctl reread
$ supervisorctl update
```
Check if processes are running
```bash
$ supervisorctl
```

>app_worker_a                     RUNNING   pid 32, uptime 0:00:02
> 
>app_worker_b                     RUNNING   pid 33, uptime 0:00:02

Check if process run
```bash
$ ps ax | grep 32
```
> 32 ?        S      0:00 /usr/local/bin/php /home/project/app/worker_a.php
