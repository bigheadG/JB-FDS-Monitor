# JB FDS Monitor

A single-page browser monitor for MQTT fall events. The page shows connection status, keeps a fall alert active until it is cleared, can play an optional audible alert, and switches between English and Traditional Chinese.

It accepts both explicit `event: "fall_detected"` messages and the ESP32 event format using `result: "Falling"`.

## Configure

Open `index.html` and edit the constants near the top of the final `<script>` block:

```js
const BROKER_WEBSOCKET_URL = "wss://YOUR_BROKER_HOST:PORT/mqtt";
const MQTT_TOPIC = "JB/FDS/#";
const MQTT_USERNAME = "";
const MQTT_PASSWORD = "";
```

The broker must expose secure MQTT over WebSocket (`wss://`) because GitHub Pages is served over HTTPS. TCP port 1883 cannot be used directly by a browser.

## Publish with GitHub Pages

1. Create a public repository named `JB-FDS-Monitor` under the `bigheadG` account.
2. Upload `index.html` to the repository root and commit it. `README.md` is optional.
3. Open **Settings → Pages** in the repository.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select the `main` branch and `/ (root)`, then click **Save**.
6. After deployment completes, open <https://bigheadG.github.io/JB-FDS-Monitor/>.

No credentials are included. If the broker requires authentication, fill in the username and password constants before publishing. Be aware that credentials in a public web page are visible to visitors; a restricted broker account and topic permissions are recommended.
