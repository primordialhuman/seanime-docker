Seanime Docker Setup Guide
Welcome to the Seanime setup guide. This guide will walk you through running your own instance of Seanime using Docker. You can easily pull the pre-built Docker image and set up the necessary configuration files on your host machine.

Prerequisites
Docker installed on your system. Get Docker
Docker Compose installed. Install Docker Compose
Quick Start
Step 1: Pull the Docker Image
To pull the latest version of the Seanime Docker image, run the following command:

bash
Copy code
docker pull primordialhuman/seanime:2.1.1
Step 2: Create the config.toml File
Create a config.toml file in a directory on your host system. This file contains configuration settings for Seanime.

bash
Copy code
mkdir -p ./seanime/config
nano ./seanime/config/config.toml
Copy and paste the following content into the config.toml file:

toml
Copy code
# The current version of Seanime (Do not change)
version = ''

[cache]
# The directory where cached data is stored
dir = '$SEANIME_DATA_DIR/cache'
# The directory where transcode video segments are stored
transcodedir = '$SEANIME_DATA_DIR/cache/transcode'

[database]
# The name of the database
name = 'seanime'

[logs]
# The directory where logs are stored
dir = '$SEANIME_DATA_DIR/logs'

[manga]
# The directory where manga chapters are downloaded
downloaddir = '$SEANIME_DATA_DIR/manga'

[offline]
# The directory where offline assets are downloaded
assetdir = '$SEANIME_DATA_DIR/offline/assets'
# The directory where the offline database is stored
dir = '$SEANIME_DATA_DIR/offline'

[server]
# The host to bind the server to
host = '0.0.0.0'
# Whether the server should run in offline mode
offline = false
# The port to bind the server to
port = 43211
# Whether SEANIME_WORKING_DIR should be the binary path (true) or the system's working directory (false)
usebinarypath = true

[web]
# The directory where custom web assets like background images are stored
assetdir = '$SEANIME_DATA_DIR/assets'
Step 3: Create the qBittorrent.conf File
Next, create a qBittorrent.conf file to configure qBittorrent with default settings, including setting the default password. This file should also be located on your host system.

bash
Copy code
nano ./seanime/config/qbittorrent/qBittorrent.conf
Paste the following content into qBittorrent.conf:

ini
Copy code
[Application]
FileLogger\Age=1
FileLogger\AgeType=1
FileLogger\Backup=true
FileLogger\DeleteOld=true
FileLogger\Enabled=true
FileLogger\MaxSizeBytes=66560
FileLogger\Path=/home/seanime/.local/share/qBittorrent/logs

[BitTorrent]
Session\ExcludedFileNames=
Session\Port=62896
Session\QueueingSystemEnabled=false

[Core]
AutoDeleteAddedTorrentFile=Never

[LegalNotice]
Accepted=true

[Meta]
MigrationVersion=6

[Network]
Cookies=@Invalid()

[Preferences]
General\Locale=en
MailNotification\req_auth=true
WebUI\AuthSubnetWhitelist=@Invalid()
WebUI\LocalHostAuth=false
WebUI\Password_PBKDF2="@ByteArray(w57KPpiYHCad/RHP9BK0IQ==:tKKmsb9nbF6kK/ILvDvVQ+mr34s8vgPBUTAuxoyLCylDrJTQc4GqUo81nHhsZM9F3SNC75TTE0qbfebQvzOgoQ==)"

[RSS]
AutoDownloader\DownloadRepacks=true
AutoDownloader\SmartEpisodeFilter=s(\\d+)e(\\d+), (\\d+)x(\\d+), "(\\d{4}[.\\-]\\d{1,2}[.\\-]\\d{1,2})", "(\\d{1,2}[.\\-]\\d{1,2}[.\\-]\\d{4})"
Step 4: Docker Compose Configuration
Below is the docker-compose.yml file, which will configure and start Seanime along with qBittorrent. Create this file in the project root directory.

bash
Copy code
nano docker-compose.yml
Add the following content:

yaml
Copy code
version: '3'
services:
  seanime:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
      - "43211:43211"
    volumes:
      - ./seanime/config:/home/seanime/.config/Seanime
      - ./seanime/config/qbittorrent:/home/seanime/.config/qBittorrent
Step 5: Run the Application
Now, you can start the services using Docker Compose:

bash
Copy code
docker-compose up
This command will build and start Seanime and qBittorrent, exposing the application on ports 8080 and 43211.

Step 6: Access the Application
Once the services are up and running, you can access Seanime at http://localhost:8080 (replace localhost with your server's IP if running remotely).

Troubleshooting
Ensure that all required directories for configuration and volumes are created and accessible by the Docker container.
If there are any port conflicts, make sure the necessary ports (8080 and 43211) are available or adjust the docker-compose.yml file to use alternative ports.
Conclusion
You now have your own instance of Seanime up and running using Docker. Feel free to contribute to the project or customize your instance as needed. If you encounter any issues, please open a ticket in the repository, and we’ll be happy to help!

