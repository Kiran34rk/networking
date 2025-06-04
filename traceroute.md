# 🌐 What is `traceroute`?

`traceroute` is a network diagnostic command used to track the path that your data (packets) takes from your computer to a destination (like a website or server).

It shows each hop (intermediate router) and how long the data takes to reach it.

---

## 🧠 How Traceroute Works

When you send data across the internet:

- It doesn’t go directly to the destination.
- It passes through multiple routers (hops) between the source and destination.

`traceroute` uses the **TTL (Time To Live)** field in packets:

- Sends packets with TTL=1 → first router sends back a “Time Exceeded” message.
- TTL=2 → second router replies.
- This continues until the packet reaches the final destination.

Each reply gives:
- The router’s IP address or hostname
- Time taken (latency in milliseconds)

---

## 📥 Command Example

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

## 🧾 What Each Line Means

| Column          | Meaning                                      |
|-----------------|----------------------------------------------|
| 1, 2, 3...       | Hop number (position in the path)            |
| 192.168.1.1      | IP address (or hostname) of the router       |
| 1.123 ms         | Round-trip time (RTT) to that hop (usually 3 probes) |

If a hop is unreachable or blocking traffic, you’ll see:
```bash
 *  *  *
```

---

## 🎯 Why Use Traceroute?

| Use Case                 | Purpose                                 |
|--------------------------|-----------------------------------------|
| Troubleshoot slow networks | See where the delay is happening      |
| Find broken links         | See where the path fails               |
| Check route to a server   | See the network path from your location |
| Identify firewall issues  | Check where packets are being dropped  |

---

## 🔧 Common Options

| Option | Description                                               |
|--------|-----------------------------------------------------------|
| `-n`   | Show IPs only, skip DNS resolution (faster)               |
| `-I`   | Use ICMP echo instead of UDP                              |
| `-T`   | Use TCP (useful for firewall-restricted environments)     |
| `-p`   | Specify port (used with TCP traceroute)                   |

---

## 🚧 Limitations

- Some routers/firewalls drop ICMP or UDP packets, causing `* * *` lines.
- Results can vary depending on **network congestion** or **routing policies**.
