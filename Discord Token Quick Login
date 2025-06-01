// ==UserScript==
// @name         Discord Token Quick Login UI (Top Center) with Feedback
// @namespace    http://tampermonkey.net/
// @version      1.3
// @description  Adds a login panel with token input and login animation on Discord login page.
// @author       YourName
// @match        https://discord.com/login
// @grant        none
// ==/UserScript==

(function () {
    'use strict';

    function createSpinner() {
        const spinner = document.createElement('div');
        spinner.style.border = '3px solid #f3f3f3';
        spinner.style.borderTop = '3px solid #7289DA';
        spinner.style.borderRadius = '50%';
        spinner.style.width = '18px';
        spinner.style.height = '18px';
        spinner.style.animation = 'spin 1s linear infinite';
        spinner.style.marginLeft = '10px';

        // Add keyframes for spin animation
        const style = document.createElement('style');
        style.textContent = `
          @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
          }
        `;
        document.head.appendChild(style);

        return spinner;
    }

    function createLoginPanel() {
        // Container
        const panel = document.createElement('div');
        panel.id = 'token-login-panel';
        panel.style.position = 'fixed';
        panel.style.top = '60px'; // Not very top, slight offset
        panel.style.left = '50%';
        panel.style.transform = 'translateX(-50%)';
        panel.style.background = '#2c2f33';
        panel.style.padding = '15px';
        panel.style.borderRadius = '8px';
        panel.style.boxShadow = '0 2px 10px rgba(0, 0, 0, 0.3)';
        panel.style.zIndex = 9999;
        panel.style.display = 'flex';
        panel.style.gap = '10px';
        panel.style.alignItems = 'center';

        // Input
        const input = document.createElement('input');
        input.type = 'text';
        input.placeholder = 'Enter Discord token';
        input.style.flex = '1';
        input.style.padding = '8px';
        input.style.border = 'none';
        input.style.borderRadius = '4px';
        input.style.outline = 'none';
        input.style.fontSize = '14px';
        input.style.width = '250px';

        // Button
        const button = document.createElement('button');
        button.innerText = 'Login';
        button.style.padding = '8px 12px';
        button.style.background = '#7289DA';
        button.style.color = 'white';
        button.style.border = 'none';
        button.style.borderRadius = '4px';
        button.style.cursor = 'pointer';

        let spinner;

        button.addEventListener('click', () => {
            const token = input.value.trim();
            if (!token) return alert('Please enter a token.');

            // Disable input and button
            input.disabled = true;
            button.disabled = true;
            button.style.cursor = 'default';

            // Show spinner
            spinner = createSpinner();
            panel.appendChild(spinner);

            // Start setting token repeatedly to localStorage
            const interval = setInterval(() => {
                const iframe = document.createElement('iframe');
                iframe.style.display = 'none';
                document.body.appendChild(iframe);
                iframe.contentWindow.localStorage.token = `"${token}"`;
                document.body.removeChild(iframe);
            }, 50);

            // After 2.5 seconds reload page
            setTimeout(() => {
                clearInterval(interval);
                location.reload();
            }, 2500);
        });

        // Assemble
        panel.appendChild(input);
        panel.appendChild(button);
        document.body.appendChild(panel);
    }

    // Detect URL changes to hide/show panel
    const observer = new MutationObserver(() => {
        if (location.pathname === '/login') {
            if (!document.getElementById('token-login-panel')) createLoginPanel();
        } else {
            const panel = document.getElementById('token-login-panel');
            if (panel) panel.remove();
        }
    });

    observer.observe(document.body, { childList: true, subtree: true });

    // Create panel if already on login page
    if (location.pathname === '/login') {
        createLoginPanel();
    }
})();
