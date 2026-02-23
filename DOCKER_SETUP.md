# Docker Setup Documentation

This project is now ready for containerized deployment using Docker and Docker Compose.

## Prerequisites
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Environment Variables
A `.env` file has been created in the root directory. You can modify this file to change the database credentials, Django secret key, and other settings.

## Running the Application

To build and start the application, run:

```bash
docker-compose up --build
```

This command will:
1. Build the Django application image.
2. Start the PostgreSQL database container.
3. Start the Django application container.
4. Automatically run database migrations.
5. Collect static files.
6. Start the Gunicorn server on port `8000`.

The application will be accessible at `http://localhost:8000`.

## Stopping the Application

To stop the containers, run:

```bash
docker-compose down
```

To stop and remove volumes (this will delete the database data!):

```bash
docker-compose down -v
```

## Creating a Superuser

While the containers are running, you can create a Django superuser by running:

```bash
docker-compose exec web python manage.py createsuperuser
```

## Useful Commands

- **Check logs**: `docker-compose logs -f`
- **Run migrations manually**: `docker-compose exec web python manage.py migrate`
- **Shell**: `docker-compose exec web python manage.py shell`
