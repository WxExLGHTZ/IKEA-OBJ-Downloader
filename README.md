# IKEA OBJ Downloader

A Selenium script that bulk-downloads all available IKEA 3D models in OBJ format from polantis.com, sorts them into single-piece and multi-piece categories, and extracts the downloaded ZIP archives.


## Motivation

Polantis hosts IKEA furniture as downloadable 3D models, but only supports downloading them one at a time through its web interface. This script automates the entire workflow: logging in, scrolling through the full catalog via infinite scroll, batch-downloading all OBJ files, and organizing them into a clean directory structure separated by single-piece and multi-piece objects.

## Features

- Downloads all available IKEA 3D models from polantis.com as OBJ files
- Separates single-piece and multi-piece objects into dedicated directories
- Scrolls the entire catalog page automatically to load all entries
- Extracts downloaded ZIP archives and organizes the resulting OBJ files
- Validates login credentials and exits cleanly on authentication failure
- Prints a summary of downloaded object counts after completion

## Tech Stack

| Category | Technology |
|----------|-----------|
| Language | Python 3.x |
| Browser Automation | Selenium 4.5.0 |
| Browser Driver | ChromeDriver |
| HTTP | urllib3 1.26.12 |

## Getting Started

### Prerequisites

- Python 3.x
- Google Chrome
- ChromeDriver (matching the installed Chrome version)
- A registered account on [polantis.com](https://www.polantis.com)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/ikea-obj-downloader.git
   cd ikea-obj-downloader
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Download ChromeDriver and place it in the project directory:
   ```bash
   # https://googlechromelabs.github.io/chrome-for-testing/
   # Version must match your installed Chrome version
   mv chromedriver ./
   chmod +x chromedriver
   ```

## Usage

```bash
python main.py
```

The script prompts for your polantis.com username and password, then opens a Chrome browser and starts downloading. The full process may take several minutes depending on your connection and the number of available models.

Once complete, files are organized as follows:

```
ikea_einteilig/
├── ikea_einteilig_zips/    # Original ZIP archives
└── ikea_einteilig_obj/     # Extracted OBJ files

ikea_mehrteilig/
├── ikea_mehrteilig_zips/   # Original ZIP archives
└── ikea_mehrteilig_obj/    # Extracted OBJ files
```