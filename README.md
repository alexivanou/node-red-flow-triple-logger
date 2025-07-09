# Triple Logger for Node-RED

> ✨ Complete logging solution for Node-RED with file, MongoDB, HTTP logging, dynamic dashboard control and log monitoring.

## 🧩 Included Flows

### 1️⃣ `triple-logger-flow.json`

Main logic flow responsible for:
- Logging messages to:
  - 📁 JSON file (`/tmp/triple-log.json`)
  - 🍃 MongoDB collection (`messages`)
  - 🌐 HTTP endpoint (`https://api.example.com/logs`)
- Filtering based on log level (`debug`, `info`, `warn`, `error`)
- Optional expression filters (`msg.level === 'error'`, etc.)
- Selection of logged fields (`payload,topic`)
- Auto-timestamping (`_logged_at`)
- Auto-cleanup of old logs (e.g., older than 7 days)

### 2️⃣ `logger-dashboard-flow.json`

Dashboard UI flow that enables:
- Dynamic configuration of logging parameters:
  - File path, MongoDB connection, HTTP endpoint
  - Log level, filter expression, selected fields
  - Retention policy in days
- Real-time monitoring:
  - 🔢 Log count
  - 🕒 Last log timestamp
  - 📈 Activity chart

Configured through groups:
- ⚙️ `Logger Settings`
- 📊 `Logger Monitor`

Accessible via Node-RED Dashboard tab **Logger Control**.

---

## 📦 Installation

1. Open **Node-RED**.
2. Import both files via `Menu → Import → Clipboard`:
   - First, import `triple-logger-flow.json`
   - Then, import `logger-dashboard-flow.json`
3. Open Dashboard tab `Logger Control` to configure the logger.
4. Deploy the flows.

> Make sure you have installed required nodes:
> - `node-red-dashboard`
> - `node-red-node-mongodb`
> - `node-red-node-ui-table` *(optional)*

---

## 🛠 Configuration Tips

- Expression example:  
  `msg.payload.temperature > 70 && msg.level !== 'debug'`
- Fields to log:  
  `payload,topic`
- MongoDB must be running and accessible.
- HTTP endpoint should support `POST` with JSON payload.

---
