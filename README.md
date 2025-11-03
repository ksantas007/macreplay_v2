# MacReplay v2 - IPTV Portal Proxy for Unraid

[![Docker](https://img.shields.io/badge/docker-enabled-blue?logo=docker)](https://docker.com)
[![Unraid](https://img.shields.io/badge/unraid-compatible-orange?logo=unraid)](https://unraid.net)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

MacReplay v2 is an improved IPTV portal proxy designed to run as a Docker container on Unraid. It provides advanced channel management, EPG support, and portal administration features with enhanced playlist editing capabilities.

## 🚀 Features

- **Portal Management**: Add and configure multiple IPTV portals with MAC address rotation
- **Advanced Channel Editor**: Enhanced filtering, duplicate management, and smart autocomplete
- **Multiple MAC Support**: Rotate between MAC addresses across a single portal for multiple simultaneous connections
- **Smart Fallback System**: Automatic failover to backup channels when primary streams fail
- **Intelligent Duplicate Detection**: Only considers enabled channels as duplicates for cleaner management
- **One-Click Duplicate Cleanup**: Remove duplicate enabled channels while preserving the first occurrence
- **Multi-Level Filtering**: Portal, Genre, and Duplicate filters work together for precise channel selection
- **EPG Support**: Electronic Program Guide integration
- **Dashboard**: Statistics and monitoring interface with real-time status
- **Cross-Platform**: Works seamlessly with Plex, M3U-based software, and other media platforms

## 📦 Unraid Installation

### Quick Start

1. **Download the repository files:**
   ```bash
   cd /mnt/user/appdata/
   git clone https://github.com/T4s3rF4c3/macreplay_v2.git macreplay
   cd macreplay
   ```

2. **Start the container:**
   ```bash
   docker-compose -f docker-compose-unraid.yml up -d --build
   ```

3. **Access the web interface:**
   ```
   http://YOUR-UNRAID-IP:8001
   ```

### Alternative: Manual Setup

```bash
# Create directories
mkdir -p /mnt/user/appdata/macreplay/{data,logs}
chown -R 99:100 /mnt/user/appdata/macreplay

# Build and run
cd /mnt/user/appdata/macreplay
docker build -t macreplay:unraid -f Dockerfile-unraid .
docker run -d \
  --name macreplay \
  --restart unless-stopped \
  -p 8001:8001 \
  -v /mnt/user/appdata/macreplay/data:/app/data \
  -v /mnt/user/appdata/macreplay/logs:/app/logs \
  -e PUID=99 \
  -e PGID=100 \
  -e TZ=Europe/Berlin \
  macreplay:unraid
```

## 🛠️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | `99` | User ID (nobody on Unraid) |
| `PGID` | `100` | Group ID (users on Unraid) |
| `TZ` | `Europe/Berlin` | Timezone for logs and EPG |
| `PYTHONUNBUFFERED` | `1` | Python output buffering |

### Volume Mounts

| Host Path | Container Path | Description |
|-----------|----------------|-------------|
| `/mnt/user/appdata/macreplay/data` | `/app/data` | Application data and configuration |
| `/mnt/user/appdata/macreplay/logs` | `/app/logs` | Application logs |

### Ports

| Port | Protocol | Description |
|------|----------|-------------|
| `8001` | HTTP | Web interface |

## 🌐 Usage

### 1. Add IPTV Portal
- Navigate to **Portals** section
- Click **Add Portal**
- Enter portal URL and MAC addresses (comma-separated)
- Configure streams per MAC and EPG offset
- Save and test the portal

### 2. Configure Channels
- Go to **Channel Editor**
- Use filters to find specific channels:
  - **Portal Filter**: Filter by specific portal
  - **Genre Filter**: Filter by channel genre
  - **Duplicate Filter**: Show only duplicates or unique channels
- Enable/disable channels as needed
- Set custom channel numbers, names, and genres
- Configure fallback channels for reliability
- Use **Deactivate Duplicates** to clean up duplicate enabled channels

### 3. Advanced Features
- **Smart Autocomplete**: Type in fallback fields to get channel suggestions
- **Bulk Operations**: Select all channels or use filters for bulk changes
- **Real-time Preview**: Play channels directly in the editor
- **Export/Import**: Save and restore channel configurations

### 4. Integration
- **M3U Playlist**: `http://YOUR-IP:8001/playlist.m3u8`
- **EPG URL**: `http://YOUR-IP:8001/epg.xml`
- **Plex Integration**: Use the M3U URL in Plex Live TV settings

## 📁 Directory Structure

```
/mnt/user/appdata/macreplay/
├── data/
│   └── MacReplay.json     # Configuration file
├── logs/
│   └── macreplay.log      # Application logs
├── templates/             # Web interface templates
├── static/               # CSS and static assets
├── app-docker.py         # Main application
├── stb.py               # STB proxy functionality
└── requirements.txt     # Python dependencies
```

## 🔧 Maintenance

### View Logs
```bash
docker logs macreplay -f
```

### Update Container
```bash
cd /mnt/user/appdata/macreplay
docker-compose -f docker-compose-unraid.yml down
git pull
docker-compose -f docker-compose-unraid.yml up -d --build
```

### Backup Configuration
```bash
cp /mnt/user/appdata/macreplay/data/MacReplay.json /mnt/user/backups/
```

### Reset Configuration
```bash
docker stop macreplay
rm /mnt/user/appdata/macreplay/data/MacReplay.json
docker start macreplay
```

## 🐛 Troubleshooting

### Container Won't Start
```bash
# Check logs
docker logs macreplay

# Verify permissions
ls -la /mnt/user/appdata/macreplay/
chown -R 99:100 /mnt/user/appdata/macreplay/
```

### Web Interface Not Accessible
- Ensure port 8001 is not used by other services
- Check Unraid firewall settings
- Verify container is running: `docker ps | grep macreplay`

### Channel Loading Issues
- Check portal configuration in the web interface
- Verify MAC addresses are valid
- Check EPG offset settings
- Review application logs for errors

### Performance Issues
- Monitor system resources on Unraid dashboard
- Check log file sizes in `/mnt/user/appdata/macreplay/logs/`
- Consider reducing the number of active channels

## 🔄 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Dashboard |
| `/portals` | GET | Portal management interface |
| `/editor` | GET | Channel editor interface |
| `/settings` | GET | Application settings |
| `/playlist.m3u8` | GET | M3U playlist for media players |
| `/epg.xml` | GET | EPG data in XMLTV format |
| `/editor_data` | GET | JSON data for channel editor |

## 📋 Requirements

- **Unraid 6.8+** with Docker support
- **2GB RAM** minimum (4GB recommended)
- **1GB disk space** for application and logs
- **Network access** to IPTV portals

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Issues**: Create an issue on GitHub for bug reports
- **Documentation**: Check the wiki for detailed guides
- **Community**: Join discussions in the issues section

## 🙏 Acknowledgments

Based on the original [MacReplay](https://github.com/Evilvir-us/MacReplay) project with significant enhancements for Unraid deployment and improved user experience.