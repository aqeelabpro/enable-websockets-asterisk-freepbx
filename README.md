# Enable WebSockets in FreePBX (GUI Only)

This guide shows how to enable **WebSockets** in **FreePBX** using only the **web GUI**—no need to manually edit configuration files or set up WebRTC.

---

## ✅ Step-by-Step Instructions (GUI Only)

### 1. Log in to the FreePBX Admin Panel

- Open your browser and go to your FreePBX server's IP or hostname.
- Example: `http://your-server-ip/admin`

---

### 2. Enable the Asterisk HTTP Mini Server

1. In the top menu, go to **Settings** → **Asterisk SIP Settings**.
3. Scroll down to the section called **"Asterisk Builtin Mini-HTTP Server"**.
4. Set the following options:

   - **Enabled**: ✅ Yes  
   - **Bind Address**: `0.0.0.0` (or your server IP)  
   - **Bind Port**: `8088` (default)

5. Click the **Submit** button at the bottom of the page.

---

### 3. Apply Configuration

- Click **"Apply Config"** (usually a red button at the top).
- This restarts the relevant Asterisk modules with HTTP/WebSocket support.

---

### 4. Verify WebSocket is Listening

You can verify the WebSocket is active using a browser or tool like `telnet`:

- Visit: `http://your-server-ip:8088/ws`  
  You should receive `Upgrade Required
Asterisk/18.26.1` message, which is normal.

> NOTE: 18.26.1 can be any asterisk depending upon your installed Asterisk version

Or:

```bash
wscat -s echo -c ws://127.0.0.1:8088/ws
