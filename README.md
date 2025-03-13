# UnrealMCP Plugin

## VERY WIP REPO
I'm working on adding more tools now and cleaning up the codebase, 
I plan to allow for easy tool extension outside the main plugin

## Overview
UnrealMCP is an Unreal Engine plugin designed to control Unreal Engine with AI tools. It implements a Machine Control Protocol (MCP) within Unreal Engine, allowing external AI systems to interact with and manipulate the Unreal environment programmatically.

This is very much a work in progress, and I need to clean up a lot of stuff!!!!!

## Features
- TCP server implementation for remote control of Unreal Engine
- JSON-based command protocol for AI tools integration
- Editor UI integration for easy access to MCP functionality
- Comprehensive scene manipulation capabilities
- Python companion scripts for client-side interaction

## Requirements
- Unreal Engine 5.x
- C++ development environment configured for Unreal Engine
- (Optional) Python 3.7+ for client-side scripting

## Installation
1. Clone this repository into your Unreal project's `Plugins` directory:
   ```
   git clone https://github.com/kvick-games/UnrealMCP.git Plugins/UnrealMCP
   ```
2. Regenerate your project files (right-click your .uproject file and select "Generate Visual Studio project files")
3. Open your project and enable the plugin in Edit > Plugins > Integration > UnrealMCP

## Usage
### In Unreal Editor
Once the plugin is enabled, you'll find MCP controls in the editor toolbar. The TCP server can be started/stopped from here.

### Client-Side Integration
Use the provided Python scripts in the `MCP` directory to connect to and control your Unreal Engine instance:

```python
from unreal_mcp_client import UnrealMCPClient

# Connect to the Unreal MCP server
client = UnrealMCPClient("localhost", 1337)

# Example: Create a cube in the scene
client.create_object(
    class_name="StaticMeshActor",
    asset_path="/Engine/BasicShapes/Cube.Cube",
    location=(0, 0, 100),
    rotation=(0, 0, 0),
    scale=(1, 1, 1),
    name="MCP_Cube"
)
```

## Command Reference
The plugin supports various commands for scene manipulation:
- `get_scene_info`: Retrieve information about the current scene
- `create_object`: Spawn a new object in the scene
- `delete_object`: Remove an object from the scene
- `modify_object`: Change properties of an existing object
- `execute_python`: Run Python commands in Unreal's Python environment
- And more to come...

Refer to the documentation in the `Docs` directory for a complete command reference.

## Security Considerations
- The MCP server accepts connections from any client by default
- Limit server exposure to localhost for development
- Validate all incoming commands to prevent injection attacks

### Project Structure
- `Source/UnrealMCP/`: Core plugin implementation
  - `Private/`: Internal implementation files
  - `Public/`: Public header files
- `Content/`: Plugin assets
- `MCP/`: Python client scripts and examples
- `Resources/`: Icons and other resources

## License
MIT License

Copyright (c) 2023 kvick

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Credits
- Created by: kvick
- Twitter: [@kvickart](https://x.com/kvickart)

## Contributing
Contributions are welcome, but I will need some time to wrap my head around things first, lol