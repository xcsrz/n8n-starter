# n8n-starter: Workflow Automation Setup

This repository provides a minimal setup for quickly getting started with [n8n](https://n8n.io/) workflow automation server. n8n is a powerful, open-source workflow automation tool that enables you to create custom workflows with minimal code.

## Features

- Pre-configured n8n environment
- Node.js version management via nvm
- Simplified dependency installation
- Quick start scripts for immediate workflow development

## Getting Started

Follow these steps to set up your own n8n instance:

### 1. Clone this repository

```bash
git clone https://github.com/xcsrz/n8n-starter
cd n8n-starter
```

### 2. Set up your local environment

Choose your operating system below for detailed setup instructions:

- [macOS Setup Guide](docs/getting-started-macos.md)
- [Windows Setup Guide](docs/getting-started-windows.md)

## Quick Reference

Once set up, you can start n8n with:

```bash
npm start
```

This will launch n8n at [http://localhost:5678](http://localhost:5678).

## Configuration

You can customize your n8n instance by creating a `.env` file in the root directory. See the [n8n documentation](https://docs.n8n.io/hosting/environment-variables/environment-variables/) for available configuration options.

## Resources

- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community Forum](https://community.n8n.io/)
- [n8n Academy](https://academy.n8n.io/)

## License

This project is released under the MIT License. See the LICENSE file for details.