# 🛡️ Republic AI Network — Validator Dashboard

A real-time validator monitoring dashboard for the Republic AI Network, built with vanilla HTML/CSS/JavaScript and powered by live RPC data.

🔗 **Live:** [https://rai-dashboard.duckdns.org](https://rai-dashboard.duckdns.org)

---

## ✨ Features

### Validator Set
- Live validator list with names (moniker), colored avatars and shortened addresses
- Voting Power, Uptime, Last 10 Blocks and Miss count columns
- Clickable column headers for ascending/descending sorting
- **MISS MONITOR** button — instantly filter by most or least missed blocks

### Live Block Feed
- Last 20 blocks updating in real-time every 6 seconds
- Proposer name, transaction count and miss warning per block

### Leaderboard
- 🏆 **Best Uptime** — top validators by signing performance
- ⚠️ **Most Missed** — 7-day cumulative miss counter with automatic weekly reset

### Network Statistics
- Miss Distribution chart (last 20 blocks)
- Block Time History chart (ms)
- Network Health ring chart

### Staking & Economics
- Total bonded power and average voting power
- Top validator share and Nakamoto Coefficient
- Top 10 power distribution bar chart

### Block Explorer
- Last 15 blocks with height, hash, proposer, TX count and miss info

---

## 🚀 Stack

- **Frontend:** Vanilla HTML, CSS, JavaScript
- **Charts:** Chart.js
- **Data:** Tendermint RPC + Cosmos REST API
- **Server:** Nginx reverse proxy on Ubuntu VPS

---

## 📡 API Endpoints Used

| Endpoint | Purpose |
|----------|---------|
| `/rpc/status` | Chain ID, sync status |
| `/rpc/validators` | Validator set and voting power |
| `/rpc/block` | Block data and proposer |
| `/rpc/commit` | Commit signatures for miss detection |
| `/api/cosmos/staking/v1beta1/validators` | Validator monikers |

---

## ⚙️ Self-Hosting

```nginx
server {
    listen 80;
    root /var/www/rai-dashboard;
    index index.html;

    location /rpc/ {
        proxy_pass http://localhost:26657/;
        add_header Access-Control-Allow-Origin * always;
    }

    location /api/ {
        proxy_pass http://localhost:1317/;
        add_header Access-Control-Allow-Origin * always;
    }
}
```

```bash
# Deploy
sudo curl -o /var/www/rai-dashboard/index.html \
  https://raw.githubusercontent.com/cemsid/rai-network-hub/main/index.html
```

---

Built with ❤️ for the Republic AI Network community.
