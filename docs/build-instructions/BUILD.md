# Building Ralph Wiggum Loop (Atom Fork)

This document provides build instructions for the Ralph Wiggum Loop fork of Atom.

## Prerequisites

### All Platforms
- **Node.js**: Version 18.0.0 or higher
- **Git**: For version control

### Windows
- **Visual Studio 2022** (or 2019) with C++ workload
  - Install via [Visual Studio Downloads](https://visualstudio.microsoft.com/downloads/)
  - Required workloads: "Desktop development with C++"
- **Python 3.x**: For building native modules
  - Add Python to your PATH
- **Windows SDK**: For building on Windows

### macOS
- **Xcode Command Line Tools**:
  ```bash
  xcode-select --install
  ```
- **Homebrew** (recommended for installing dependencies)

### Linux
- **Build essentials** (Ubuntu/Debian):
  ```bash
  sudo apt-get install build-essential git libx11-dev libxext-dev libxss1 libgtk-3-0 libnotify4 libnss3 libasound2 libcurl4 libgbm1 libgcrypt20 libxkbfile1 xdg-utils
  ```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/atom.git
   cd atom
   ```

2. Install script dependencies:
   ```bash
   cd script
   npm install
   cd ..
   ```

3. Install npm dependencies:
   ```bash
   npm install
   ```

## Building

### Windows
```bash
script\build
```

### macOS / Linux
```bash
./script/build
```

The build script will:
1. Download the correct Electron version
2. Compile native modules (tree-sitter, nsfw, etc.)
3. Transpile CoffeeScript and other sources
4. Generate the application bundle

## Running Tests

Run the test suite:
```bash
npm test
```

Or run tests directly:
```bash
./script/test
```

## Development

To run Atom in development mode:
```bash
atom .
```

## Troubleshooting

### Native Module Build Failures
If native modules fail to build:
1. Ensure Visual Studio (Windows) or Xcode (macOS) is installed correctly
2. Try cleaning and rebuilding:
   ```bash
   script/clean
   npm rebuild
   ```

### Electron Version Issues
If you encounter Electron-related errors:
```bash
script/redownload-electron-bins.js
```

### Node.js Version
Make sure you're using Node.js 18+. Check with:
```bash
node --version
```

## Known Issues

- Some native modules may require specific Visual Studio versions on Windows
- Building on Linux requires 64-bit Ubuntu/Debian
- The auto-updater is disabled in this fork

## Additional Resources

- [Original Atom Flight Manual](https://flight-manual.atom.io)
- [Electron Documentation](https://www.electronjs.org/docs)
