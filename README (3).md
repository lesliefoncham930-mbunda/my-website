# CoolWatch – IoT Data Center Cooling Monitoring

A live web dashboard for our ESP32 cooling system. It connects to the public EMQX MQTT broker over secure WebSockets and shows temperature, humidity and fan status in real time.

The whole site is one file, `index.html`. No build step or install is needed.

## MQTT settings (already filled in)

| Setting | Value |
|---|---|
| Broker WebSocket URL | `wss://broker.emqx.io:8084/mqtt` |
| Subscribe | `hossam7192/datacenter/#` |
| Temperature | `hossam7192/datacenter/temperature` → `25.50` |
| Humidity | `hossam7192/datacenter/humidity` → `45.20` |
| Fan status | `hossam7192/datacenter/fan/status` → `ON` / `OFF` |

Open the site → **Dashboard** → **Live MQTT** → **Connect**.

## Run locally

Double-click `index.html` (Chrome or Edge), or run `python -m http.server 8000` in this folder and open http://localhost:8000.

## Host on GitHub Pages

1. Create a new public repository on GitHub, e.g. `coolwatch-dashboard`.
2. Upload `index.html` and `README.md` (Add file → Upload files → Commit changes).
3. Settings → Pages → Build and deployment → Source: *Deploy from a branch*, Branch: `main`, folder `/ (root)` → Save.
4. After about a minute: `https://<your-username>.github.io/coolwatch-dashboard/`

## Host on Vercel

1. Sign in at vercel.com with your GitHub account.
2. Add New… → Project → Import the `coolwatch-dashboard` repository.
3. Framework Preset: **Other**. Leave Build Command and Output Directory empty → Deploy.
4. Your site is live at `https://coolwatch-dashboard.vercel.app` (or similar). Every push to `main` redeploys automatically.

## Notes

- The hosted site uses HTTPS, so the broker URL must start with `wss://`.
- Some school or company networks block port 8084. If Connect fails, try another network or a phone hotspot.
- The public broker is readable by anyone. Do not send passwords or private data on these topics.
- Libraries load from CDNs: Chart.js 4.4.1 (cdnjs) and MQTT.js 5.10.1 (unpkg).
