# Setting Up n8n on Windows

This guide will walk you through setting up the n8n workflow automation tool on Windows.

## Prerequisites

- Windows 10 or later
- Administrative access
- Git installed ([install Git](https://git-scm.com/download/win) if needed)

## Step 1: Install Node Version Manager for Windows (nvm-windows)

1. Download the latest nvm-windows installer from the [releases page](https://github.com/coreybutler/nvm-windows/releases)
2. Run the installer (nvm-setup.exe) and follow the installation wizard
3. After installation, close and reopen any command prompt windows

Verify the installation by opening a new Command Prompt or PowerShell window and running:

```powershell
nvm version
```

## Step 2: Install Node.js

The correct Node.js version is specified in the `.nvmrc` file (v22.15.0). Since nvm-windows doesn't automatically read `.nvmrc` files, you'll need to install it manually:

```powershell
# Install and use the required Node.js version (v22.15.0)
nvm install 22.15.0
nvm use 22.15.0
```

Verify the installation:

```powershell
node --version
npm --version
```

## Step 3: Install Dependencies

```powershell
npm install
```

## Step 4: Start n8n

```powershell
npm start
```

n8n will now be running at [http://localhost:5678](http://localhost:5678).

## Optional: Create a Windows Shortcut

For easier access, you can create a shortcut to start n8n:

1. Right-click on your desktop and select "New > Shortcut"
2. For the location, enter: `powershell -ExecutionPolicy Bypass -Command "cd 'C:\path\to\n8n-starter' ; npm start"`
3. Replace `C:\path\to\n8n-starter` with the actual path to your repository
4. Name the shortcut "Start n8n" and click Finish

## Troubleshooting

### Error: Node.js version not found

If you get an error that the specified Node.js version is not installed:

```powershell
# List all available Node.js versions
nvm list available

# Install the closest available version
nvm install 22.15.0
```

### Error: n8n fails to start

Check if the required ports (default: 5678) are available:

```powershell
netstat -ano | findstr :5678
```

If the port is in use, you can configure n8n to use a different port by setting the `N8N_PORT` environment variable in your `.env` file.

### Error: Long path issues

Windows has path length limitations. If you encounter issues:

1. Enable long path support in Windows:
   ```powershell
   # Run as administrator
   Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1
   ```

2. Configure Git to handle long paths:
   ```powershell
   git config --global core.longpaths true
   ```

## Additional Resources

- [nvm-windows GitHub Repository](https://github.com/coreybutler/nvm-windows)
- [n8n Documentation](https://docs.n8n.io/)
- [Windows Terminal](https://aka.ms/terminal) - A better command-line experience for Windows