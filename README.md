# Simple Network Simulator

A lightweight, interactive Python-based network simulator with a GUI built using Tkinter. This application allows users to design, visualize, and test network topologies in real-time.

## Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [How It Works](#how-it-works)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

## Features

✅ **Interactive Network Design**
- Add network devices (PCs, Routers, Switches)
- Create connections between devices
- Visual network topology display

✅ **Device Management**
- Create multiple device types with automatic naming
- Configure IP addresses for each device
- Delete devices from the network
- View device properties and information

✅ **Network Connectivity Testing**
- Ping test between any two devices
- Automatic pathfinding using shortest path algorithm
- Visual feedback on connectivity status
- Path routing information

✅ **User-Friendly Interface**
- Intuitive sidebar with tools
- Real-time event logging
- Right-click context menus
- Color-coded device types
- Interactive canvas for network design

✅ **Network Graph Analysis**
- Uses NetworkX for graph operations
- Shortest path calculation
- Connectivity verification
- Support for complex topologies

## Technology Stack

- **Language**: Python 3.x
- **GUI Framework**: Tkinter
- **Graph Library**: NetworkX
- **Visualization**: Canvas-based rendering
- **Mathematics**: Python math library for distance calculations

## Installation

### Prerequisites

- Python 3.7 or higher
- pip (Python package manager)

### Step 1: Clone the Repository

```bash
git clone https://github.com/YoussefShaher/Simple-Network-Simulator.git
cd Simple-Network-Simulator
```

### Step 2: Install Dependencies

```bash
pip install networkx
```

Note: Tkinter comes pre-installed with most Python distributions. If you need to install it separately:

**On Ubuntu/Debian:**
```bash
sudo apt-get install python3-tk
```

**On macOS:**
```bash
brew install python-tk
```

**On Windows:**
Tkinter is included with Python installer by default.

### Step 3: Run the Application

```bash
python project.py
```

or

```bash
python "import tkinter.py"
```

## Usage

### Main Interface

The application consists of three main areas:

1. **Sidebar (Left Panel)** - Tools and controls
2. **Canvas (Main Area)** - Network visualization
3. **Event Log** - Operation history

### Adding Devices

1. Select a device type from the Tools section:
   - **Add PC** - Personal Computer (Sky Blue)
   - **Add Router** - Network Router (Salmon/Red)
   - **Add Switch** - Network Switch (Light Green)

2. Click on the canvas where you want to place the device
3. Device will appear with an auto-generated name (e.g., "PC1", "Router1")
4. Event log will show confirmation

### Creating Connections

1. Select **"Link Devices"** mode
2. Click on the first device (it will be highlighted in the log)
3. Click on the second device to create a connection
4. A line will appear connecting both devices
5. Event log shows the connection details

### Device Properties

1. Right-click on any device
2. Select **"Properties"** from the context menu
3. Edit the device information:
   - Device Name
   - IP Address
   - Device Type (read-only)
4. Click **"Save"** to apply changes

### Deleting Devices

1. Right-click on a device
2. Select **"Delete"** from the context menu
3. Device will be removed along with all its connections

### Ping Test

#### Method 1: Using Ping Test Button

1. Click the **"Ping Test"** button in the sidebar
2. Enter source node name (e.g., "PC1")
3. Enter destination node name (e.g., "PC2")
4. Click **"Ping"** to test connectivity
5. Result will show the path or "Unreachable" error

#### Method 2: Right-Click Ping

1. Right-click on a device
2. Select **"Ping from this"**
3. Enter the destination device name
4. Click **"Ping"**
5. View the results

### Event Log

The event log displays all operations:
- Device creation
- Connections established
- Device deletions
- IP address updates
- Ping test results
- Path information

## Project Structure

```
Simple-Network-Simulator/
├── project.py                 # Main application (v1)
├── import tkinter.py         # Main application (v2)
└── README.md                 # This file
```

## How It Works

### Network Graph

The simulator uses NetworkX's `Graph` class to represent the network:
- **Nodes** represent network devices (PC, Router, Switch)
- **Edges** represent connections between devices
- Each node stores:
  - Device type
  - IP address
  - Position on canvas

### Pathfinding

The application uses NetworkX's `shortest_path()` function to find the route between two devices:
```python
path = nx.shortest_path(graph, source=source_node, target=destination_node)
```

If no path exists, it raises `NetworkXNoPath` exception.

### Visual Rendering

Devices are drawn as circles on a Tkinter Canvas:
- Circle radius: 20 pixels
- Colors determined by device type
- Labels show device name and IP address (if configured)
- Connections drawn as gray lines

### Distance Detection

Clicked positions are compared against device locations using Euclidean distance:
```python
distance = math.hypot(device_x - click_x, device_y - click_y)
if distance <= NODE_RADIUS:
    # Device was clicked
```

## Examples

### Example 1: Simple Star Topology

1. Add 1 Router in the center
2. Add 3 PCs around it
3. Link each PC to the Router
4. Ping between any two PCs - path will go through the Router

### Example 2: Mesh Topology

1. Add 4 PCs
2. Connect every PC to every other PC
3. Ping tests will show direct paths
4. Multiple routes available for redundancy

### Example 3: Complex Network

1. Add 2 Routers connected together
2. Add 3 PCs connected to Router1
3. Add 3 PCs connected to Router2
4. Ping from PC on Router1 to PC on Router2
5. Path will route through both Routers

## Device Types & Colors

| Device Type | Color | Purpose |
|------------|-------|---------|
| PC | Sky Blue | End user computers |
| Router | Salmon | Network routing |
| Switch | Light Green | Network switching |

## Keyboard & Mouse Controls

- **Left Click** - Create device or add link
- **Right Click** - Open context menu for device operations
- **Text Entry** - Configure device properties

## Troubleshooting

### Issue: "No module named 'networkx'"
**Solution**: Install NetworkX
```bash
pip install networkx
```

### Issue: "No module named 'tkinter'"
**Solution**: Install Tkinter for your OS (see Installation section)

### Issue: Ping always fails
**Check**: 
- Device names are correct (case-sensitive)
- Devices are actually connected in the network
- Both devices exist in the network

### Issue: Application doesn't start
**Solution**:
- Ensure Python 3.7+ is installed
- Check all dependencies are installed
- Try running from command line to see error messages

## Performance Notes

- The simulator can handle networks with hundreds of devices
- Ping operations are instant (uses algorithm, not real networking)
- Real-time rendering on canvas
- Event log shows last operations

## Future Enhancements

Potential features for future versions:
- 🔄 Save/Load network topology
- 📊 Network statistics and analytics
- 🎨 Custom themes and color schemes
- 🔧 Advanced device configuration
- 📡 Bandwidth and latency simulation
- 📝 Export network diagrams
- 🎬 Animation of packet flow
- 🌐 Subnetting and VLAN support

## Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is open source and available under the MIT License.

## Author

**Youssef Shaher**
- GitHub: [@YoussefShaher](https://github.com/YoussefShaher)

## Support

For issues, questions, or suggestions, please:
- Open an issue on GitHub
- Contact the development team
- Check existing issues for solutions

## Acknowledgments

- NetworkX library for graph algorithms
- Python Tkinter for GUI framework
- Community feedback and contributions

---

**Version**: 1.0  
**Last Updated**: May 2026  
**Repository**: [Simple-Network-Simulator](https://github.com/YoussefShaher/Simple-Network-Simulator)
