# Discord Token Quick Login & Display Panel

A small userscript and local panel for quickly viewing and reusing Discord tokens for development and debugging purposes.

## Overview

This repository contains two primary artifacts:

- `Discord Token Quick Login.user.js` — a userscript that provides a quick-login helper for Discord using a token.
- `Discord Token Display Panel.user.js` — a userscript that adds a panel to display the current token.
- `index.html` — a simple local page to demo or host the display panel.

These tools are intended for development, testing, and personal account debugging only. They are not intended for misuse.

## Features

- Display the current Discord token in a convenient panel.
- Quickly log in using a saved token (convenience for developers).
- Simple, lightweight, and easily installed via a userscript manager.

## Installation

1. Install a userscript manager in your browser (for example, Tampermonkey or Greasemonkey).
2. Open the `.user.js` files from this repository in the browser or your editor and install them with the userscript manager.
3. Reload Discord in the same browser profile; the scripts add UI elements/panels for the token display and quick login.

Alternatively, open `index.html` locally in a browser to view or test the display panel.

## Usage

- Use these scripts only on accounts you own for debugging or development.
- After installing the userscripts, open Discord in the same browser and look for the added panel or quick-login UI.

Do not share tokens or use these tools to access accounts you do not own.

## Security & Legal Notice

- WARNING: Discord tokens are extremely sensitive credentials. Anyone with access to a token can control the corresponding account.
- Use these tools only on accounts you own or have explicit permission to test.
- Unauthorized access to accounts is illegal and a violation of Discord's Terms of Service.
- The author is not responsible for misuse. Use at your own risk.

## Contributing

Contributions are welcome for bug fixes, documentation improvements, and safety hardening. Please open issues or pull requests.

## License

This project is provided under the MIT License. See `LICENSE` if present or add one if you want a different license.

## Acknowledgements

This utility is meant for convenience during development. Consider safer alternatives that do not expose credentials when possible.
