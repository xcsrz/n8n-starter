# Setting Up n8n on macOS

This guide will walk you through setting up the n8n workflow automation tool on macOS.

## Prerequisites

- macOS 10.15 (Catalina) or later
- Terminal access
- Git installed ([install Git](https://git-scm.com/download/mac) if needed)

## Step 1: Install Node Version Manager (nvm)

nvm helps manage multiple Node.js versions on your system.

```bash
# Install nvm using curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```

After installation, close and reopen your terminal, or run:

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

Verify the installation:

```bash
nvm --version
```

## Step 2: Install Node.js

The correct Node.js version is specified in the `.nvmrc` file (v22.15.0).

```bash
# Install and use the Node.js version specified in .nvmrc (v22.15.0)
nvm install
nvm use
```

Verify the installation:

```bash
node --version
npm --version
```

## Step 3: Install Dependencies

```bash
npm install
```

## Step 4: Start n8n

```bash
npm start
```

n8n will now be running at [http://localhost:5678](http://localhost:5678).

## Optional: Install direnv for Automatic Environment Setup

[direnv](https://direnv.net/) automatically loads the correct Node.js version when you enter the project directory.

```bash
# Install direnv using Homebrew
brew install direnv

# Add to your shell configuration (~/.zshrc or ~/.bash_profile)
echo 'eval "$(direnv hook zsh)"' >> ~/.zshrc  # For zsh users
# OR
echo 'eval "$(direnv hook bash)"' >> ~/.bash_profile  # For bash users
```

After installation, restart your terminal or source your shell configuration file.

## Troubleshooting

### Error: EACCES: permission denied

If you encounter permission errors when installing global npm packages:

```bash
npm config set prefix ~/.npm-global
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc  # or ~/.bash_profile
source ~/.zshrc  # or ~/.bash_profile
```

### Error: n8n fails to start

Check if the required ports (default: 5678) are available:

```bash
lsof -i :5678
```

If the port is in use, you can configure n8n to use a different port by setting the `N8N_PORT` environment variable in your `.env` file.

## Additional Resources

- [nvm GitHub Repository](https://github.com/nvm-sh/nvm)
- [n8n Documentation](https://docs.n8n.io/)
- [direnv Documentation](https://direnv.net/)