# IDM Downloader (Claude Code Skill)

A Claude Code skill for downloading large files using IDM (Internet Download Manager) on Windows.

## Overview

This is a [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code) that integrates IDM into Claude Code's workflow. It allows Claude to download files on behalf of the user using IDM's acceleration and resume capabilities.

## Features

- **Large File Support**: Optimized for downloading large files (hundreds of MB to several GB)
- **COM Interface**: Uses IDM's COM automation for reliable downloads
- **Command Line Fallback**: Falls back to IDMan.exe command line if COM fails
- **Auto Detection**: Automatically locates IDM installation via registry or common paths
- **Resume Support**: Leverages IDM's pause/resume functionality

## Requirements

- Windows OS
- [Internet Download Manager](https://www.internetdownloadmanager.com/) installed
- Python 3.x
- pywin32 (`pip install pywin32`)

## Installation

1. Install pywin32:
   ```bash
   pip install pywin32
   ```

2. Copy `SKILL.md` and `scripts/` to your Claude Code skills directory:
   ```
   C:\Users\<your_username>\.claude\skills\idm-downloader\
   ```

## Usage

Once installed as a Claude Code skill, simply ask Claude to download files using IDM:

```
"使用IDM下载 https://example.com/large-file.zip"
"Download this file with IDM"
```

Or use the script directly:

```bash
python scripts/download_idm.py <url> [output_directory] [filename]
```

### Examples

```bash
python scripts/download_idm.py https://example.com/file.zip
python scripts/download_idm.py https://example.com/file.zip "C:\Downloads"
python scripts/download_idm.py https://example.com/file.zip "C:\Downloads" custom.zip
```

## How It Works

1. Claude Code receives a download request
2. The skill invokes `download_idm.py` with the URL and output path
3. The script first attempts to use IDM's COM interface for download
4. If COM fails, it falls back to IDMan.exe command line interface
5. IDM handles the actual download with acceleration and resume support

## License

MIT
