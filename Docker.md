Here's a comprehensive list of Docker commands for Laravel in Markdown format:

```markdown
# Docker Commands for Laravel

## Basic Docker Commands

```bash
# Check Docker version
docker --version

# List running containers
docker ps

# List all containers (running and stopped)
docker ps -a

# List all Docker images
docker images

# Remove a container
docker rm <container_name_or_id>

# Remove an image
docker rmi <image_name_or_id>

# Stop a running container
docker stop <container_name_or_id>

# Start a stopped container
docker start <container_name_or_id>

# Restart a container
docker restart <container_name_or_id>

# View container logs
docker logs <container_name_or_id>

# View real-time container logs
docker logs -f <container_name_or_id>

# Execute a command in a running container
docker exec -it <container_name_or_id> <command>
```

## Docker Compose Commands for Laravel

```bash
# Build and start all containers (in detached mode)
docker-compose up -d

# Stop all containers
docker-compose down

# Stop and remove all containers, networks, and volumes
docker-compose down -v

# Rebuild containers
docker-compose up -d --build

# View logs for all services
docker-compose logs

# View logs for a specific service
docker-compose logs <service_name>

# List all running services
docker-compose ps

# Execute a command in a specific service container
docker-compose exec <service_name> <command>
```

## Laravel-Specific Docker Commands

```bash
# Install Laravel dependencies (composer)
docker-compose exec app composer install

# Update Laravel dependencies
docker-compose exec app composer update

# Run Laravel migrations
docker-compose exec app php artisan migrate

# Run Laravel migrations with seed
docker-compose exec app php artisan migrate --seed

# Rollback migrations
docker-compose exec app php artisan migrate:rollback

# Generate Laravel key
docker-compose exec app php artisan key:generate

# Clear Laravel cache
docker-compose exec app php artisan cache:clear

# Clear Laravel views
docker-compose exec app php artisan view:clear

# Clear Laravel routes
docker-compose exec app php artisan route:clear

# Clear Laravel config
docker-compose exec app php artisan config:clear

# Run Laravel tests
docker-compose exec app php artisan test

# Run npm install (if using Node.js)
docker-compose exec npm install

# Run npm dev (for frontend assets)
docker-compose exec npm run dev

# Run npm production build
docker-compose exec npm run prod

# Enter the app container shell
docker-compose exec app bash

# Enter the database container shell
docker-compose exec db bash

# Access MySQL database
docker-compose exec db mysql -u root -p
```

## Docker Volume Commands

```bash
# List all volumes
docker volume ls

# Inspect a volume
docker volume inspect <volume_name>

# Remove a volume
docker volume rm <volume_name>

# Remove unused volumes
docker volume prune
```

## Docker Network Commands

```bash
# List all networks
docker network ls

# Inspect a network
docker network inspect <network_name>

# Remove a network
docker network rm <network_name>

# Remove unused networks
docker network prune
```

## Tips

1. For a typical Laravel project with Docker, you'll usually need these services:
   - `app` (PHP-FPM with Laravel)
   - `web` (Nginx/Apache)
   - `db` (MySQL/PostgreSQL)
   - `redis` (optional)
   - `mailhog` (optional for email testing)

2. Always run composer and artisan commands in the `app` container.

3. For production, remember to:
   - Set proper environment variables
   - Optimize the configuration
   - Use proper SSL certificates
   - Consider separate containers for queue workers, scheduler, etc.
```

This Markdown file includes all the essential Docker commands you'll need when working with Laravel in a Docker environment. You can save this as `docker-laravel-commands.md` for future reference.