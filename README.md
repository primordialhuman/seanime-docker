
# Seanime Docker Setup Guide

Welcome to the **Seanime** setup guide. This guide will walk you through running your own instance of Seanime using Docker. You can easily pull the pre-built Docker image and set up the necessary configuration files on your host machine.

## Prerequisites

- Docker installed on your system. [Get Docker](https://docs.docker.com/get-docker/)
- Docker Compose installed. [Install Docker Compose](https://docs.docker.com/compose/install/)
  
## Quick Start




###  Run the Application

Now, you can start the services using Docker Compose:

```bash
docker-compose up
```

### qbittorrent on port 8080 when initialising seanime it will ask qbittorrent details add below details

### -----------
username : admin
password : admin123
port : 8080
### -----------


###  Access the Application

Once the services are up and running, you can access Seanime at `http://localhost:43211` (replace `localhost` with your server's IP if running remotely).

### If you want to stream downloaded videos using jellyfin just change the download volume path in docker-compose to jellyfin location and then jellyfin will pickup files.

## Troubleshooting

- Ensure that all required directories for configuration and volumes are created and accessible by the Docker container.
- If there are any port conflicts, make sure the necessary ports (`8080` and `43211`) are available or adjust the `docker-compose.yml` file to use alternative ports.

## Conclusion

You now have your own instance of Seanime up and running using Docker. Feel free to contribute to the project or customize your instance as needed. If you encounter any issues, please open a ticket in the repository, and we’ll be happy to help!
