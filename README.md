# Troubleshooting Steps for Setting Up Eliza

## Common Errors and Solutions

### Error 1: Node.js Version Compatibility
**Issue:** The project requires Node.js version 23+, but I had an older version installed.

**Solution:** 
- Check the installed version of Node.js:
  ```bash
  node -v
  ```
- If the version is below 23, update Node.js using nvm (Node Version Manager):
  ```bash
  nvm install 23
  nvm use 23
  ```

### Error 2: pnpm Not Installed
**Issue:** The command `pnpm install` failed because pnpm was not installed.

**Solution:** 
- Install pnpm globally:
  ```bash
  npm install -g pnpm
  ```

### Error 3: Missing .env File
**Issue:** The application crashed because the `.env` file was missing or not configured.

**Solution:** 
- Create a `.env` file from the example:
  ```bash
  cp .env.example .env
  ```
- Edit the `.env` file to include necessary API keys and configurations.

### Error 4: Dependency Installation Failures
**Issue:** Some dependencies failed to install due to missing build tools.

**Solution:** 
- Install required build tools:
  ```bash
  sudo apt-get install build-essential python3
  ```
- Retry installing dependencies:
  ```bash
  pnpm install
  ```

### Error 5: Permission Issues
**Issue:** Encountered permission errors while installing packages.

**Solution:** 
- Use `sudo` to install globally, or fix permissions for npm:
  ```bash
  sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
  ```

### Error 6: Memory Issues During Runtime
**Issue:** The application crashed due to high memory usage.

**Solution:** 
- Check memory usage:
  ```bash
  node --trace-gc index.js
  ```
- Optimize the code or increase the memory limit:
  ```bash
  node --max-old-space-size=4096 index.js
  ```

### Error 7: Incorrect Character File Format
**Issue:** The agent failed to start due to an invalid character file format.

**Solution:** 
- Ensure the character file is correctly formatted as JSON. Use a JSON validator to check for syntax errors.

### Conclusion
By following these troubleshooting steps, I was able to resolve the issues I encountered while setting up the Eliza project. Documenting these errors and solutions can help others avoid similar pitfalls and streamline their setup process.
