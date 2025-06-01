# Discord Token Utilities

A collection of two Tampermonkey userscripts to help with Discord token management:

1. **Discord Token Display Panel (Modern UI)**  
   Displays your current Discord token in a slide-out panel on any Discord page, with options to copy and refresh.

2. **Discord Token Quick Login UI**  
   Adds a login panel to Discord’s login page where you can quickly input a token and log in with an animated spinner showing progress.

---

## Features

### Discord Token Display Panel (Modern UI)
- Fixed slide-out panel on the right side of the screen
- Shows your Discord token in a read-only textarea
- Copy token to clipboard with one click
- Refresh button to manually update token display
- Auto-refreshes every 2 seconds
- Toggle panel visibility with a hamburger menu button

### Discord Token Quick Login UI
- Simple token input panel at the top center of the Discord login page
- Login button sets token in localStorage repeatedly for reliability
- Animated spinner shows login progress
- Automatically reloads the page after 2.5 seconds to log in

---

## Installation

1. Install [Tampermonkey](https://www.tampermonkey.net/) (or a compatible userscript manager) in your browser.
2. Create two new userscripts using the provided script code files.
3. Ensure the scripts are enabled.
4. Visit [https://discord.com](https://discord.com) and enjoy enhanced token management.

---

## Usage

- **Token Display Panel:**  
  Navigate anywhere on Discord after enabling the script. Click the hamburger icon on the right to toggle the panel. Copy or refresh your token as needed.

- **Quick Login UI:**  
  Go to [https://discord.com/login](https://discord.com/login). Enter your token and click *Login*. Watch the spinner animation while logging in.

---

## Security & Disclaimer

- **WARNING:** Using Discord tokens directly can compromise your account security if exposed.  
- Only use tokens you own and keep them private.  
- These scripts do not collect or transmit your token outside your browser.  
- Use at your own risk.

---

## Contributing

Feel free to submit issues or pull requests to improve these utilities.

---

## License

MIT License © YourName

---

## Scripts Included

- `discord-token-display-panel.user.js`  
- `discord-token-quick-login.user.js`

---

Thanks for checking out this project!  
If you want me to help generate a full repo structure or upload to GitHub, just ask.
