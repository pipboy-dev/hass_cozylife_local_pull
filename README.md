# CozyLife Local Pull - Home Assistant Integration Forked from zqbake

[![GitHub Release](https://img.shields.io/github/v/release/zqbake/hass_cozylife_local_pull)](https://github.com/pipboy-dev/hass_cozylife_local_pull/releases)
[![License](https://img.shields.io/github/license/zqbake/hass_cozylife_local_pull)](LICENSE)
[![hacs][hacs-shield]][hacs-url]

[hacs-shield]: https://img.shields.io/badge/HACS-Custom-orange.svg
[hacs-url]: https://github.com/hacs/integration

Home Assistant integration for controlling CozyLife smart devices over local network.

## Features

✨ **Automatic Device Discovery**
- Automatic UDP broadcast discovery on startup
- Periodic scanning every 5 minutes (configurable)
- **Cross-subnet device discovery** via TCP scanning
- Automatic offline detection and reconnection
- No Home Assistant restart required for new devices

✨ **Modern Architecture**
- Full async/await implementation
- Non-blocking operations
- Device Registry integration
- UI configuration support (no YAML editing needed)
- Support for multiple color modes (brightness, color temperature, RGB)

✨ **Supported Device Types**

| Device Type | Features |
|-------------|----------|
| **Light** | On/Off, Brightness, Color Temperature, RGB Color |
| **Switch** | On/Off, Fast Response |

## Installation

### Via HACS (Recommended)

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=zqbake&repository=hass_cozylife_local_pull&category=integration)

Or manually:
1. Click **HACS** > **Integrations**
2. Click **⋮** > **Custom repositories**
3. Add this repository URL: `https://github.com/pipboy-dev/hass_cozylife_local_pull`
4. Category: **Integration**
5. Click **Add**
6. Search for "CozyLife Local" and click **Install**
7. Restart Home Assistant

### Manual Installation

1. Clone this repository to your `custom_components` directory:
```bash
git clone https://github.com/pipboy-dev/hass_cozylife_local_pull.git custom_components/hass_cozylife_local_pull
```

2. Restart Home Assistant

## Configuration

### Via UI (Recommended)

1. **Settings** → **Devices & Services**
2. Click **Create Integration** → Search **"CozyLife Local"**
3. Configure:
   - **Language**: Select your language
   - **Device IP Addresses** (Optional): Manually add specific device IPs (comma or space-separated)
   - **Subnet Ranges** (Optional): Add subnets for cross-network discovery (e.g., 192.168.2.0/24)
   - **Scan Interval**: Default 300 seconds (5 minutes)

### Via YAML (Legacy Support)

Add to `configuration.yaml`:

```yaml
hass_cozylife_local_pull:
  lang: "en"
  ip:
    - "192.168.1.100"
    - "192.168.1.101"
  subnets:
    - "192.168.2.0/24"
    - "192.168.3.0/24"
  scan_interval: 300
```

**Configuration Parameters:**
- `lang`: Language code (en, zh, es, pt, ja, ru, nl, ko, fr, de)
- `ip`: List of device IP addresses (optional, leave empty for UDP auto-discovery)
- `subnets`: List of subnet ranges to scan for cross-network devices in CIDR format (optional)
- `scan_interval`: How often to rescan for new devices in seconds (default: 300, minimum: 60)

Then restart Home Assistant.

## Troubleshooting

### Devices not discovered?

1. Ensure devices are on the same network as Home Assistant
2. Check if router firewall blocks UDP port 6095
3. Manually add device IP addresses in configuration

### Connection issues?

- Verify device IP address is correct
- Check device supports TCP port 5555
- Ping device to verify network connectivity
- Restart the device

### Slow response?

- Check network quality and WiFi signal strength
- Reduce scan interval if needed (minimum 60 seconds)
- Try wired connection instead of WiFi

## Support

- 📝 Submit an [Issue](https://github.com/pipboy-dev/hass_cozylife_local_pull/issues) on GitHub
- 💬 Discuss on [Home Assistant Community](https://community.home-assistant.io/)
- 📧 Email: info@cozylife.app

## Changelog

### v0.3.1 (2026)
- ✨ Removed unnecessary external http request

### v0.3.0 (2024)
- ✨ Complete async architecture upgrade
- ✨ Periodic automatic device discovery (every 5 minutes)
- ✨ **Cross-subnet device discovery** via TCP scanning
- ✨ Device Registry integration
- ✨ UI configuration flow support (no YAML editing required)
- ✨ Automatic offline detection and reconnection
- 🐛 **Fixed color display issues** (dpid 2 mode checking, value validation)
- 🐛 **Fixed multiple color mode support** (brightness, color temp, RGB)
- 🐛 **Improved color space conversion** (proper RGB intermediate conversion)
- 📚 Comprehensive documentation
- ⚡ **3-5x faster device control response**
- 📉 **20%+ lower memory usage** (async instead of threading)

### v0.2.0
- Initial release with basic functionality

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Disclaimer

This integration is not officially affiliated with CozyLife. Use at your own risk.
