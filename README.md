# 🎮 UnRen v0.9.1 - Python 3 Version

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)

**UnRen for Mac and Linux** - Tool for extracting RPA archives and decompiling Ren'Py RPYC files.

<img width="848" height="818" alt="UnRen v0.9.1" src="https://github.com/user-attachments/assets/23bfe634-9b57-4c88-9b9e-3ddf2493b1e0" />


## What's New in v0.9.1

**New Feature - URM Support**

- **URM Copy**: Added option to copy Universal Ren'Py Mod (URM) to game folder
- **Menu Option 77**: New menu option to easily copy URM.rpa to game directory

**Cross-Platform Improvements**

- **Linux Compatibility**: Added automatic OS detection for cross-platform support
- **Open Command**: Now uses `xdg-open` on Linux and `open` on macOS

## What's New in v0.9.0

**Major Upgrade - Python 3 Compatibility**

This version represents a significant upgrade from Python 2 to Python 3:

- **Python 3 Upgrade**: Script now requires Python 3.9 or higher
- **unrpyc v2.x**: Updated to latest version (Python 3) from GitHub master branch
  - Supports Ren'Py 8.x down to 6.18.0
  - Requires Python 3.9+
- **rpatool**: Updated for Python 3 compatibility
- **Ren'Py SDK Configuration**: Added option to configure Ren'Py SDK path for decompiler
- **Interactive Input**: Decompiler asks for SDK path if not configured
- **Improved Warnings**: Clear messages about decompiler requirements
- **Verbose Output**: RPA extraction with detailed output

## System Requirements

- **Python 3.9 or higher** (required by unrpyc v2.x)
- macOS or Linux
- Bash shell

## Tools Used

- **rpatool**: https://codeberg.org/shiz/rpatool
  - Tool for extracting and creating Ren'Py archives (.rpa/.rpi)
- **unrpyc v2.x**: https://github.com/CensoredUsername/unrpyc
  - Ren'Py script decompiler (.rpyc → .rpy)
  - Python 3 version from master branch

## Installation

1. Make sure you have Python 3.9 or higher installed:
   ```bash
   python3 --version
   ```

2. Make the script executable:
   ```bash
   chmod +x "UnRen.command"
   ```

## Configuration

### Ren'Py SDK Configuration (Optional but Recommended for Decompiler)

The decompiler requires the Ren'Py SDK to work properly. You can configure it in three ways:

#### Method 1: File Configuration

Edit the Configuration section in `UnRen.command` (line 72):

```bash
# Optional: Ren'Py SDK path for decompiler
# If not set, decompiler will ask for path interactively
renpy_sdk_path="/path/to/renpy-sdk"
```

#### Method 2: Interactive Input

If you don't configure the path in the file, when you select the decompiler you'll be asked to enter it:

```
Ren'Py SDK path not configured in the Configuration section.
Please enter the path to your Ren'Py SDK (or press Enter to skip):
```

Enter the full path to your Ren'Py SDK (e.g., `/path/to/renpy-sdk`).

#### Method 3: System PATH

You can add the Ren'Py SDK to your system PATH:

```bash
export PATH="/path/to/renpy-sdk:$PATH"
```

### Other Configuration Parameters

```bash
quicksavekey="K_F5"    # Quick save key
quickloadkey="K_F9"    # Quick load key
```

## Usage

### Starting the Script

```bash
./UnRen.command
```

Or drag the `UnRen.command` file into the terminal.

### Game Selection

The script will ask you to drag the game folder into the terminal or enter the path manually.

### Main Menu

After selecting the game, you'll see the main menu with the following options:

1. **Extract RPA packages** - Extract game RPA archives
2. **Decompile rpyc files** - Decompile RPYC files to RPY
3. **Decompile rpyc files (overwrite)** - Decompile overwriting existing RPY files
4. **Enable Console** - Enable developer console
5. **Enable Developer Menu** - Enable developer menu
6. **Enable Quick Save/Load** - Enable quick save/load with configured keys
7. **Skip Unread Text** - Enable skipping unread text
8. **Rollback Anywhere** - Enable rollback anywhere
9. **Open Game Folder** - Open game folder
77. **Copy URM to game folder** - Copy Universal Ren'Py Mod to game
10. **Quit** - Exit the script

## Features

### RPA Extraction

Extracts Ren'Py archives (.rpa) in the game folder with verbose output:
- Shows current directory
- Shows each file being extracted
- Confirms extraction completion

### RPYC Decompilation

Decompiles compiled Ren'Py files (.rpyc) into readable scripts (.rpy):
- Requires configured Ren'Py SDK
- Supports Ren'Py 8.x down to 6.18.0
- Asks for SDK path if not configured
- Option to overwrite existing files

### Developer Console

Enables Ren'Py developer console for debugging and testing.

### Developer Menu

Enables developer menu with advanced features.

### Quick Save/Load

Enables quick save (F5) and quick load (F9) with configured keys.

## Important Notes

### Decompiler

- The decompiler requires the Ren'Py SDK to work properly
- Without the SDK, you may get import errors
- unrpyc v2.x supports Ren'Py 8.x down to 6.18.0
- For older games (pre-6.18.0), you may need to use the `--no-init-offset` option
- For Ren'Py 7 or earlier games, use the legacy version (Python 2) of unrpyc

### Compatibility

- This version is only compatible with Python 3.9+
- Not compatible with Python 2
- For Ren'Py 7 or earlier games, use version v0.8.2 (Python 2)

### RPA Extraction

- RPA extraction works without Ren'Py SDK
- Extracted files are saved in the game folder
- Necessary subdirectories are created

## Troubleshooting

### Error: "Python 3 is not installed"

Install Python 3.9 or higher from https://python.org

### Error: "ModuleNotFoundError: No module named 'deobfuscate'"

This error should not occur in v0.9.0. Make sure you have all files in the `UnRen Tools` folder:
- `unrpyc.py`
- `deobfuscate.py`
- `rpatool`
- `decompiler/` folder

### Import error during decompilation

Make sure to:
1. Have the Ren'Py SDK installed
2. Configure the SDK path correctly
3. Use the correct unrpyc version for your game version

### Error: "cannot find rpatool or unrpyc"

Verify that the files exist in the `UnRen Tools` folder:
```bash
ls "UnRen Tools/"
```

## File Structure

```
UnRen/
├── UnRen.command              # Main script
├── README.md                  # This file
└── UnRen Tools/
    ├── unrpyc.py              # Decompiler (v2.x Python 3)
    ├── deobfuscate.py         # Deobfuscation module
    ├── rpatool                # RPA archive tool
    └── decompiler/            # Decompiler modules
        ├── __init__.py
        ├── util.py
        ├── codegen.py
        ├── sl2decompiler.py
        ├── screendecompiler.py
        ├── testcasedecompiler.py
        ├── astdump.py
        ├── translate.py
        └── magic.py
```

## Credits

- **Original**: goobdoob @ www.f95zone.to
- **Based on**: jimmy5 @ www.f95zone.to
- **Based on**: UnRen.bat by Sam @ www.f95zone.to
- **rpatool**: https://codeberg.org/shiz/rpatool
- **unrpyc**: https://github.com/CensoredUsername/unrpyc
- **URM (Universal Ren'Py Mod)**: https://f95zone.to/threads/universal-renpy-mod-urm-2-6-2-mod-any-renpy-game-yourself.48025/

## License

See individual LICENSE files for rpatool and unrpyc for license information.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for the complete version history.
