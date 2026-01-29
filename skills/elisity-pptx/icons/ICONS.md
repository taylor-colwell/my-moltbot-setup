# Elisity Icon Library

48 SVG icons for network security diagrams and presentations.

## Usage

**IMPORTANT**: SVG icons must be rasterized to PNG before embedding in PowerPoint:

```javascript
const sharp = require('sharp');

await sharp('icons/virtual-edge-node.svg')
  .resize(200, 200)
  .png()
  .toFile('workspace/virtual-edge-node.png');
```

## Icon Categories

### Network Infrastructure
| File | Description |
|------|-------------|
| `router.svg` | Network router |
| `switch.svg` | Network switch |
| `firewall.svg` | Firewall device |
| `switch-firewall.svg` | Combined switch/firewall |
| `wireless-ap.svg` | Wireless access point |
| `wireless-router.svg` | Wireless router |
| `wireless-lan-controller.svg` | Wireless LAN controller |
| `server.svg` | Server |
| `data-center.svg` | Data center facility |
| `internet.svg` | Internet/WAN connection |

### Cloud Providers
| File | Description |
|------|-------------|
| `AWS.svg` | Amazon Web Services |
| `Azure.svg` | Microsoft Azure |
| `GCP.svg` | Google Cloud Platform |
| `cloud.svg` | Generic cloud |

### Elisity Products
| File | Description |
|------|-------------|
| `cloud-control-center.svg` | Elisity Cloud Control Center |
| `virtual-edge.svg` | Elisity Virtual Edge |
| `virtual-edge-node.svg` | Elisity Virtual Edge Node |
| `virtual-edge-vm.svg` | Virtual Edge VM deployment |

### End User Devices
| File | Description |
|------|-------------|
| `laptop.svg` | Laptop computer |
| `desktop-computer.svg` | Desktop computer |
| `printer.svg` | Network printer |
| `ip-phone.svg` | IP/VoIP phone |
| `smart-TV.svg` | Smart TV |
| `camera.svg` | Security camera |
| `generic-device.svg` | Generic network device |
| `device-group.svg` | Group of devices |
| `virtual-machine.svg` | Virtual machine |

### Users & Identity
| File | Description |
|------|-------------|
| `user.svg` | Single user |
| `users.svg` | Multiple users |
| `IDP.svg` | Identity Provider |
| `NAC.svg` | Network Access Control |
| `ad-agent.svg` | Active Directory agent |

### Security & Policy
| File | Description |
|------|-------------|
| `policy.svg` | Security policy |
| `policy2.svg` | Security policy (alternate) |
| `policies.svg` | Multiple policies |
| `security-profile.svg` | Security profile |

### Locations
| File | Description |
|------|-------------|
| `campus.svg` | Campus/headquarters |
| `branch.svg` | Branch office |
| `hospital.svg` | Hospital/healthcare facility |
| `factory.svg` | Factory/manufacturing |
| `data-center.svg` | Data center |

### Industrial/OT Devices
| File | Description |
|------|-------------|
| `plc.svg` | Programmable Logic Controller |
| `hvac.svg` | HVAC system |
| `robot.svg` | Industrial robot |
| `eng-workstation.svg` | Engineering workstation |

### Medical/IoMT Devices
| File | Description |
|------|-------------|
| `ct-scanner.svg` | CT Scanner |
| `EHR-server.svg` | Electronic Health Records server |

### Other
| File | Description |
|------|-------------|
| `application.svg` | Application/software |
| `data.svg` | Data/database |

## Color Customization

Icons use Elisity brand colors. When rasterizing, you can apply color transformations if needed using Sharp's tint or composite features.

## Best Practices

1. **Size icons appropriately** - Typically 100-200px for slide diagrams
2. **Maintain aspect ratio** - Don't stretch icons
3. **Use consistent sizing** - Keep related icons the same size
4. **Add labels** - Icons should have text labels for clarity
5. **Use whitespace** - Don't crowd icons together
