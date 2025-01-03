# 🚀 Seanime Docker Setup Guide

Welcome to the **Seanime** setup guide! This guide will help you set up your own Seanime instance using Docker in just a few steps. 🎉 

With this guide, you can easily pull the pre-built Docker image and configure the required files on your host machine.

---

## 📋 Prerequisites

Ensure you have the following installed on your system:

- 🐳 [Docker](https://docs.docker.com/get-docker/)  
- 🛠️ [Docker Compose](https://docs.docker.com/compose/install/)  

---

## ⚡ Quick Start

### ▶️ Run the Application

1. Clone the project or create a `docker-compose.yml` file with the required configuration.
2. Start the services using the following command:

   ```bash
   docker-compose up

   # 🔑 qBittorrent Configuration

When initializing Seanime, you’ll be asked to provide **qBittorrent** details. Use the following credentials:  

- **Username**: `admin`  
- **Password**: `admin123`  
- **Port**: `8080`  

---

## 📁 Library Path Setup

Provide the **Library Path** as per your Docker Compose volume configuration. For example:  
`/home/seanime/Downloads`

---

## 🌐 Access the Application

Once the services are running, you can access Seanime via:  
👉 **http://localhost:43211**  

*(Replace `localhost` with your server’s IP if accessing remotely.)*

---

## 🎬 Stream with Jellyfin (Optional)

Want to stream downloaded videos using **Jellyfin**?  

1. Update the **download volume path** in `docker-compose.yml` to point to Jellyfin’s media location.  
2. Jellyfin will automatically pick up the files for streaming.  

---

## 🛠️ Troubleshooting

- 🔍 Ensure all required directories and volumes are properly created and accessible by the Docker container.  
- ⚠️ Check for port conflicts on `8080` and `43211`. Update the `docker-compose.yml` file to use alternative ports if needed.  

---

## 🎉 Conclusion

Congratulations! 🎊 You now have your own Seanime instance running via Docker.  

💡 Feel free to customize the setup or contribute to the project. If you encounter any issues, don’t hesitate to open a ticket in the repository—we’re here to help! 😊
