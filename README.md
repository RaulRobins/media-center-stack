# Media Center Stack with Docker Compose

![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![Plex](https://img.shields.io/badge/Plex-000000?style=for-the-badge&logo=plex&logoColor=white)
[![Jellyfin](https://img.shields.io/badge/Jellyfin-00A4DC?style=for-the-badge&logo=jellyfin&logoColor=white)](https://jellyfin.org)
![Navidrome](https://img.shields.io/badge/Navidrome-0084B4?style=for-the-badge&logo=navidrome&logoColor=white)
![PIA VPN](https://img.shields.io/badge/PIA_VPN-4BC62D?style=for-the-badge&logo=privateinternetaccess&logoColor=white)
![Portainer](https://img.shields.io/badge/Portainer-13BEF9?style=for-the-badge&logo=portainer&logoColor=white)
![Flame](https://img.shields.io/badge/Flame-FF6B6B?style=for-the-badge&logo=firebase&logoColor=white)

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

**🌐 Accessing Services**

| Service      | Port     | Access URL               | Credentials | Status |
|--------------|----------|--------------------------|-------------|--------|
| Transmission | `9091`   | `http://<IP>:9091`       | None | ![Transmission](https://img.shields.io/badge/status-active-success) |
| Radarr       | `7878`   | `http://<IP>:7878`       | Set on launch | ![Radarr](https://img.shields.io/badge/status-active-success) |
| Sonarr       | `8989`   | `http://<IP>:8989`       | Set on launch | ![Sonarr](https://img.shields.io/badge/status-active-success) |
| Lidarr       | `8686`   | `http://<IP>:8686`       | Set on launch | ![Lidarr](https://img.shields.io/badge/status-active-success) |
| Prowlarr     | `9696`   | `http://<IP>:9696`       | Set on launch | ![Prowlarr](https://img.shields.io/badge/status-active-success) |
| Plex         | `32400`  | `http://<IP>:32400/web`  | Plex account | ![Plex](https://img.shields.io/badge/status-active-success) |
| Samba        | `139/445`| `smb://<IP>/Media`       | System user | ![Samba](https://img.shields.io/badge/status-active-success) |

## 🔒 Security Best Practices

### VPN Configuration
- **Credential Security**
  - Always store VPN credentials in `.env` file:
    ```ini
    # .env
    OPENVPN_USERNAME=your_username
    OPENVPN_PASSWORD=your_password
    ```
  - Never commit credentials in `docker-compose.yml`

- **Performance Enhancement**
  - Consider using WireGuard for better performance:
    ```yaml
    # In transmission service config
    environment:
      - OPENVPN_PROVIDER=PIA
      - OPENVPN_CONFIG=wireguard
    ```

### Plex Security
- **Account Protection**
  - Enable Two-Factor Authentication (2FA) in Plex account settings
  - Use claim token only during initial setup:
    ```yaml
    # Remove after first run
    environment:
      - PLEX_CLAIM=claim-xxxxxxxxxx
    ```

  