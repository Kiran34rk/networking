# 🌐 What is TCP Traceroute?

`tcptraceroute` is a network diagnostic tool that traces the path to a destination using TCP packets instead of the traditional ICMP or UDP packets used by standard `traceroute`.

---

## 🧠 Why Use TCP Instead of ICMP/UDP?

- Traditional `traceroute` uses UDP (or ICMP Echo on Windows).
- But many firewalls block ICMP/UDP traffic — leading to missing hops (`* * *`).
- `tcptraceroute` sends TCP SYN packets (like a normal connection request) to a specific port (like 443 for HTTPS).
- These packets are more likely to pass through firewalls and NAT devices, revealing the actual route used by real-world applications.

---

## 💻 Basic Syntax

```bash
tcptraceroute <destination> <port>
```

### Example:

```bash
tcptraceroute google.com 443
```

This traces the route to `google.com` using TCP SYN packets on port 443 (HTTPS).

---

## 📊 Sample Output

```bash
tcptraceroute to google.com (142.250.182.206), 30 hops max, 60 byte packets
 1  192.168.1.1      1.134 ms  1.098 ms  1.112 ms
 2  10.0.0.1         10.230 ms  10.240 ms  10.221 ms
 3  172.16.100.1     20.487 ms  20.442 ms  20.490 ms
 4  142.250.182.206  30.870 ms  30.710 ms  30.650 ms
```

---

## 🔧 Advantages

| Feature                 | Benefit                                 |
|-------------------------|-----------------------------------------|
| Uses TCP SYN packets     | Mimics real traffic like HTTP/HTTPS     |
| Works better through firewalls | Avoids ICMP/UDP blocking           |
| Traces specific port access | Shows the actual path used by real applications |

---

## 📌 When to Use TCP Traceroute

- Traditional `traceroute` shows `* * *` or inconsistent results.
- You want to trace path to a specific service/port (e.g., web, SSH).
- You're troubleshooting firewall-related issues.
- You want to simulate actual application traffic routing.

---

## 📥 Installation (if not available)

### On Ubuntu/Debian:

```bash
sudo apt install tcptraceroute
```

### On RHEL/CentOS:

```bash
sudo yum install tcptraceroute
```

---

## 🚫 Limitations

- Needs `root` or `sudo` to run (raw sockets).
- Some hosts may not respond to TCP SYNs, especially on closed ports.
- Like traditional traceroute, it depends on intermediate routers replying.

---

## ✅ Summary

| Standard Traceroute     | TCP Traceroute                      |
|------------------------|-----------------------------------|
| Uses UDP or ICMP       | Uses TCP SYN                      |
| Blocked by many firewalls | Likely to pass through firewalls |
| Shows basic connectivity | Shows app-level path (e.g., port 443) |
