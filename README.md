# Media Center Stack with Docker Compose

![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![Plex](https://img.shields.io/badge/Plex-000000?style=for-the-badge&logo=plex&logoColor=white)

A complete self-hosted media ecosystem featuring secure torrenting, automated media management, and streaming capabilities.

## 🌟 Features

| Service       | Description                                  | Key Feature                          |
|---------------|----------------------------------------------|--------------------------------------|
| Transmission  | Torrent client with OpenVPN integration      | Secure PIA VPN connection            |
| Radarr        | Movie collection manager                     | Automated movie downloads            |
| Sonarr        | TV show organizer                            | TV series management                 |
| Lidarr        | Music collection manager                     | Music library automation             |
| Prowlarr      | Unified indexer manager                      | Torrent indexer aggregator           |
| Plex          | Media streaming server                       | Hardware transcoding support         |
| Samba         | Network file sharing                         | Easy local network access            |

## 🚀 Getting Started

### Prerequisites
- Docker Engine >= 20.10.14
- Docker Compose >= 2.4.1
- PIA VPN account (or modify for different VPN provider)
- Basic Linux terminal knowledge

### Installation

1. **Clone Repository**
   ```bash
   git clone https://github.com/yourusername/media-center-stack.git
   cd media-center-stack

2. **Configure Enviorement**
    ```bash
    cp .env.example .env
    nano .env  # Edit with your credentials
    ```

3. **Start Services**
    ```bash
    docker-compose up -d
    ```

### 🔧 Configuration

**Essential Settings (.env)**  

    ```bash
    # VPN Configuration (PIA)
    OPENVPN_PROVIDER=PIA
    OPENVPN_CONFIG=france
    OPENVPN_USERNAME=your_pia_username
    OPENVPN_PASSWORD=your_pia_password

    # System Settings
    TZ=America/Mexico_City
    PUID=1000
    PGID=1000
    LOCAL_NETWORK=192.168.0.0/16

    # Plex Claim (Optional)
    # PLEX_CLAIM=claim-xxxxxxxxxxxxxxxx
    ```

**Volume Structure**  

   
        /media/
        ├── usb1/                 # Main storage
        │   ├── downloads/        # Transmission downloads
        │   ├── movies/           # Radarr-managed movies
        │   ├── tv/               # Sonarr-managed TV shows
        │   └── music/            # Lidarr-managed music
        │
        └── configs/
            ├── transmission/     # VPN and client config
            ├── radarr/           # Movie database
            ├── sonarr/           # TV show database
            ├── lidarr/           # Music database
            ├── prowlarr/         # Indexer config
            └── plex/             # Media library metadata
  