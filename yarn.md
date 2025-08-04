# yarn

## Update yarn by corepack

1. Enable corepack (default in Node.js 16.9+)

   ```bash
   corepack enable
   ```

   If `corepack enable` fails, upgrade Node.js to v16.9+ or v14.19+ (older versions require manual Corepack installation):

   ```bash
   # Install Corepack (for Node < 16.9):
   npm install -g corepack
   ```

1. Let corepack to automatically set the Yarn version in your project

   ```bash
   # Run this in the root of your project to force sync the specified Yarn version in package.json
   yarn set version stable  # Or run `yarn install` directly (Corepack will handle it automatically)
   ```

1. Re install dependencies

   ```bash
   yarn install
   ```

1. Backup option (not recommended): If you don't want to use Corepack, you can manually install the required Yarn version

   ```bash
   # Uninstall old version of Yarn
   npm uninstall -g yarn

   # Install the specific version of Yarn
   npm install -g yarn@3.6.3
   ```

   Note: This may cause compatibility issues with other projects, so it's recommended to use Corepack first.

1. Verify the installation by checking the Yarn version:

   ```bash
   yarn --version  # Should output the version you installed, e.g., 3.6.3
   ```

   Re-run `yarn install` to ensure dependencies are installed correctly.
