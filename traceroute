# 📌 traceroute Command - Network Troubleshooting

## 🌐 What is `traceroute`?

`traceroute` is a network diagnostic tool used to trace the path that packets take from your computer to a destination (e.g., a website or server).  
It displays each intermediate device (called a "hop") the packet passes through, and how long each step takes.

---

## 🧠 How It Works

- Sends packets with increasing TTL (Time To Live) values.
- Each router reduces TTL by 1.
- When TTL becomes 0, the router replies with a "Time Exceeded" message.
- This helps identify each router between source and destination.

---

## 💻 Usage

### On Linux/macOS:
```bash
traceroute google.com
```

### On Windows:
```cmd
tracert google.com
```

---

## 📄 Sample Output

```bash
traceroute to google.com (142.250.182.46), 30 hops max
 1  192.168.1.1      1.123 ms  1.018 ms  1.012 ms
 2  10.0.0.1         10.541 ms  10.657 ms  10.711 ms
 3  172.16.54.1      20.314 ms  20.098 ms  20.274 ms
 4  142.250.182.46   30.412 ms  30.211 ms  30.301 ms
```

---

## 📊 Output Explanation

| Field      | Description                                      |
|------------|--------------------------------------------------|
| Hop Number | Position in the path                             |
| IP Address | IP address or hostname of the router             |
| RTT        | Round-trip time for 3 packets (in milliseconds)  |

> If a hop does not respond, you’ll see: `*  *  *`

---

## 🎯 Common Use Cases

- Troubleshoot slow or failed connections
- Identify where delays or drops are happening
- Trace actual network path to a server
- Debug firewall or routing issues

---

## 🔧 Common Options

```bash
traceroute -n google.com        # Don't resolve DNS (faster)
traceroute -I google.com        # Use ICMP packets
traceroute -T -p 443 google.com # Use TCP SYN to port 443 (e.g. HTTPS)
```

---

## ⚠️ Notes

- Some routers/firewalls block ICMP or UDP packets.
- This may result in timeouts (`* * *`) for some hops.
- For service-level testing, use **TCP traceroute** (useful for ports like 443, 22, etc).

---

## 🧪 Related Tools

- `ping` – Check if a host is reachable
- `mtr` – Combines `traceroute` and `ping` (real-time tracing)
- `tcptraceroute` – Traceroute using TCP packets (bypasses some firewalls)
