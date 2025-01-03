Seanime Docker Setup Guide 🚀
=====================================
Welcome to the Seanime setup guide! 🤝 This guide will walk you through running your own instance of Seanime using Docker. 🐳
Prerequisites 📝
------------------------
Docker installed on your system 🐳. 
Docker Compose installed 📈. 
Quick Start ⏱️
----------------------
Run the Application 🚀
Start the services using Docker Compose:
Bash
docker-compose up
Configure qBittorrent 📊
When initializing Seanime, you'll be asked for qBittorrent details. Use the following:
Username: admin
Password: admin123
Port: 8080
Set Library Path 📁
Provide the library path based on the Docker Compose volume path, e.g., /home/seanime/Downloads
Access the Application 📊
Access Seanime at http://localhost:43211 (replace localhost with your server's IP if running remotely).
Stream Downloaded Videos using Jellyfin 📺
To stream downloaded videos using Jellyfin, change the download volume path in docker-compose.yml to the Jellyfin location. Jellyfin will then pick up the files.
Troubleshooting 🤔
-------------------------
Ensure all required directories for configuration and volumes are created and accessible by the Docker container.
If there are port conflicts, make sure the necessary ports (8080 and 43211) are available or adjust the docker-compose.yml file to use alternative ports.
Conclusion 🎉
------------------
You now have your own instance of Seanime up and running using Docker! 🚀 Feel free to contribute to the project or customize your instance as needed. If you encounter any issues, please open a ticket in the repository, and we'll be happy to help! 🤝
