<img src="/uploads/logos/nodejs.png" align="right" width="200" />

# Node.js
##### Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine.

## Overview
- [Official Website](https://nodejs.org/en/)
## Installation
It's recommended to use NVM to manage your Node.js installations.
### Ubuntu

```sh
# Download and install

curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash

# Add to context and load NVM

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"

# Install the latest LTS version of node

nvm install --lts
nvm use --lts
```

### Windows

Download the latest version from the Releases page (use the `nvm-setup.zip` file):
https://github.com/coreybutler/nvm-windows/releases

Install NVM from the downloaded zip file.

Once installed, run the following commands in a CMD prompt:

```powershell
nvm install --lts
nvm use --lts
```

## Documentation
The complete API documentation is available at:
https://nodejs.org/dist/latest-v6.x/docs/api/
