// ==UserScript==
// @name         Discord Token Display Panel (Modern UI)
// @namespace    https://yourdomain.com/
// @version      2.0
// @match        https://discord.com/*
// @grant        none
// @run-at       document-idle
// ==/UserScript==

(function () {
    'use strict';

    function getToken() {
        try {
            const iframe = document.createElement('iframe');
            iframe.style.display = 'none';
            document.body.appendChild(iframe);
            const raw = iframe.contentWindow.localStorage.getItem('token');
            document.body.removeChild(iframe);
            return raw ? raw.replace(/"/g, '') : '';
        } catch (e) {
            console.error('Error fetching token:', e);
            return '';
        }
    }

    function createPanel() {
        const panel = document.createElement('div');
        panel.id = 'discord-token-modern-panel';
        Object.assign(panel.style, {
            position: 'fixed',
            top: '50%',
            right: '-340px',  // Start hidden off-screen
            transform: 'translateY(-50%)',
            width: '320px',
            height: 'auto',
            backgroundColor: '#36393f',
            borderLeft: '2px solid #202225',
            color: '#fff',
            fontFamily: 'gg sans, sans-serif',
            fontSize: '14px',
            zIndex: '100000',
            padding: '16px',
            boxShadow: '0 0 12px rgba(0,0,0,0.6)',
            borderRadius: '8px 0 0 8px',
            transition: 'right 0.3s ease',
        });

        // Header
        const header = document.createElement('div');
        header.textContent = 'Token Viewer';
        Object.assign(header.style, {
            fontSize: '16px',
            fontWeight: '600',
            marginBottom: '12px',
            textAlign: 'center',
            color: '#7289da',
        });
        panel.appendChild(header);

        // Textarea
        const tokenBox = document.createElement('textarea');
        tokenBox.readOnly = true;
        tokenBox.value = getToken();
        Object.assign(tokenBox.style, {
            width: '100%',
            height: '80px',
            backgroundColor: '#2f3136',
            border: '1px solid #202225',
            color: '#ccc',
            fontFamily: 'monospace',
            fontSize: '12px',
            padding: '8px',
            borderRadius: '4px',
            resize: 'none',
        });
        panel.appendChild(tokenBox);

        // Buttons container
        const btnContainer = document.createElement('div');
        Object.assign(btnContainer.style, {
            display: 'flex',
            justifyContent: 'space-between',
            marginTop: '12px',
        });

        const copyBtn = document.createElement('button');
        copyBtn.textContent = 'Copy';
        Object.assign(copyBtn.style, {
            flex: '1',
            marginRight: '6px',
            backgroundColor: '#5865f2',
            border: 'none',
            color: '#fff',
            padding: '6px 10px',
            borderRadius: '4px',
            cursor: 'pointer',
        });
        copyBtn.onclick = () => {
            navigator.clipboard.writeText(tokenBox.value).then(() => {
                copyBtn.textContent = 'Copied!';
                setTimeout(() => copyBtn.textContent = 'Copy', 1500);
            });
        };

        const refreshBtn = document.createElement('button');
        refreshBtn.textContent = 'Refresh';
        Object.assign(refreshBtn.style, {
            flex: '1',
            backgroundColor: '#3ba55d',
            border: 'none',
            color: '#fff',
            padding: '6px 10px',
            borderRadius: '4px',
            cursor: 'pointer',
        });
        refreshBtn.onclick = () => tokenBox.value = getToken();

        btnContainer.appendChild(copyBtn);
        btnContainer.appendChild(refreshBtn);
        panel.appendChild(btnContainer);

        // Toggle button
        const toggleBtn = document.createElement('div');
        toggleBtn.innerHTML = '&#9776;';
        Object.assign(toggleBtn.style, {
            position: 'fixed',
            top: '50%',
            right: '0',
            transform: 'translateY(-50%)',
            backgroundColor: '#5865f2',
            color: '#fff',
            fontSize: '20px',
            padding: '8px 12px',
            borderRadius: '8px 0 0 8px',
            cursor: 'pointer',
            zIndex: '100001',
            userSelect: 'none',
        });

        let shown = false;
        toggleBtn.onclick = () => {
            shown = !shown;
            panel.style.right = shown ? '0' : '-340px';
        };

        document.body.appendChild(panel);
        document.body.appendChild(toggleBtn);

        // Auto-refresh token every 2 seconds
        setInterval(() => {
            const latest = getToken();
            if (tokenBox.value !== latest) tokenBox.value = latest;
        }, 2000);
    }

    setTimeout(createPanel, 500);
})();
