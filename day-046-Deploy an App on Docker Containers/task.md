
# Day 46: Deploy an App on Docker Containers

## 🛠️ Task

On App Server 3 in Stratos Datacenter create a docker compose file `/opt/itadmin/docker-compose.yml` (should be named exactly).
The compose should deploy two services (web and DB), and each service should deploy a container as per details below:

### Web service:

- Container name: `php_host`
- Image: `php` with any apache tag (e.g., `php:8.2-apache`)
- Map container port 80 to host port 8082
- Map `/var/www/html` volume (container) to `/var/www/html` (host)

### DB service:

- Container name: `mysql_host`
- Image: `mariadb` (preferably latest)
- Map container port 3306 to host port 3306
- Map `/var/lib/mysql` volume (container) to `/var/lib/mysql` (host)
- Set `MYSQL_DATABASE=database_host` and use any custom user (not root) with a complex password

---
