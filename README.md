# MCP Server for FTP Access

This Model Context Protocol (MCP) server provides tools for interacting with FTP servers. It allows Claude.app to list directories, download and upload files, create directories, and delete files/directories on FTP servers.

## Features

- **List Directory Contents**: View files and folders on the FTP server
- **Download Files**: Retrieve file content from the FTP server
- **Upload Files**: Create new files or update existing ones
- **Create Directories**: Make new folders on the FTP server
- **Delete Files/Directories**: Remove files or directories

## Installation

### Prerequisites

- Node.js 16 or higher
- Claude for Desktop (or other MCP-compatible client)

### NPM Installation

```bash
npm install -g mcp-server-ftp
```

## Configuration

To use this server with Claude for Desktop, add it to your configuration file:

### MacOS/Linux
Edit `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "ftp-server": {
      "command": "npx",
      "args": ["-y", "mcp-server-ftp"],
      "env": {
        "FTP_HOST": "ftp.example.com",
        "FTP_PORT": "21",
        "FTP_USER": "your-username",
        "FTP_PASSWORD": "your-password",
        "FTP_SECURE": "false"
      }
    }
  }
}
```

### Windows
Edit `%APPDATA%\Claude\claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "ftp-server": {
      "command": "npx",
      "args": ["-y", "mcp-server-ftp"],
      "env": {
        "FTP_HOST": "ftp.example.com",
        "FTP_PORT": "21",
        "FTP_USER": "your-username",
        "FTP_PASSWORD": "your-password",
        "FTP_SECURE": "false"
      }
    }
  }
}
```

## Configuration Options

| Environment Variable | Description | Default |
|---------------------|-------------|---------|
| `FTP_HOST` | FTP server hostname or IP address | localhost |
| `FTP_PORT` | FTP server port | 21 |
| `FTP_USER` | FTP username | anonymous |
| `FTP_PASSWORD` | FTP password | (empty string) |
| `FTP_SECURE` | Use secure FTP (FTPS) | false |

## Usage

After configuring and restarting Claude for Desktop, you can use natural language to perform FTP operations:

- "List the files in the /public directory on my FTP server"
- "Download the file /data/report.txt from the FTP server"
- "Upload this text as a file called notes.txt to the FTP server"
- "Create a new directory called 'backups' on the FTP server"
- "Delete the file obsolete.txt from the FTP server"
- "Remove the empty directory /old-project from the FTP server"

## Available Tools

| Tool Name | Description |
|-----------|-------------|
| `list-directory` | List contents of an FTP directory |
| `download-file` | Download a file from the FTP server |
| `upload-file` | Upload a file to the FTP server |
| `create-directory` | Create a new directory on the FTP server |
| `delete-file` | Delete a file from the FTP server |
| `delete-directory` | Delete a directory from the FTP server |

## Building from Source

If you want to build the project from source:

```bash
# Clone the repository
git clone https://github.com/alxspiker/mcp-server-ftp.git
cd mcp-server-ftp

# Install dependencies
npm install

# Build the project
npm run build

# Run the server (for testing)
npm start
```

## Security Considerations

- FTP credentials are stored in the Claude configuration file. Ensure this file has appropriate permissions.
- Consider using FTPS (secure FTP) by setting `FTP_SECURE=true` if your server supports it.
- The server creates temporary files for uploads and downloads in your system's temp directory.

## License

MIT