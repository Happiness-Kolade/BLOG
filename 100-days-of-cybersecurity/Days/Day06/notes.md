# Basic Linux networking commands...

## You’ll definitely need this for SOC roles, basic troubleshooting, and also positions that require a basic understanding of networking. These commands—`ifconfig`, `ping`, and `netstat`—are foundational for understanding network interfaces, connectivity, and active connections or ports on a Linux machine. 

I’ll break down each command and explain with:

* What it does,
* How to use it,
* How to test it,
* What to watch out for (common pitfalls or important details).

---

## 1. `ifconfig` — Network Interface Configuration

### What it does:

* Shows detailed info about your network interfaces (IP addresses, MAC addresses, subnet mask, etc.)
* You can also use it to enable/disable interfaces or assign IP addresses (though `ip` command is more modern).

### How to use:

```bash
ifconfig
```

This shows all active network interfaces.

To see a specific interface (e.g., `eth0`):

```bash
ifconfig eth0
```

### How to test:

* Run `ifconfig` on your Linux machine (could be a VM, cloud instance, or physical).
* Look for your active interfaces like `eth0`, `wlan0`, or `lo` (loopback).
* Check IP addresses assigned, e.g., `inet addr:192.168.1.10`.
* Verify MAC addresses (`HWaddr`).

### What to watch out for:

* `ifconfig` might not be installed by default on some modern Linux distros (like Ubuntu). Use `ip a` as a modern alternative.
* `ifconfig` only shows active interfaces by default. To see all, even inactive, add the `-a` flag:

  ```bash
  ifconfig -a
  ```
* Loopback interface `lo` is always there, with IP `127.0.0.1`.
* In SOC, knowing your machine’s IP and MAC helps in network forensics and validating network configurations.

---

## 2. `ping` — Test Network Connectivity

### What it does:

* Sends ICMP echo requests to test if a host (IP or domain) is reachable.
* Measures response time and packet loss.

### How to use:

```bash
ping <target>
```

Example:

```bash
ping 8.8.8.8
ping google.com
```

### How to test:

* Ping your default gateway (router IP) to check local network connectivity.
* Ping an external IP (e.g., 8.8.8.8) to test internet connectivity.
* Ping a domain name to also test DNS resolution.
* Press `Ctrl + C` to stop.

### What to watch out for:

* If ping fails, check if:

  * The target is down or unreachable.
  * Firewall or network ACL blocks ICMP.
* Some servers block ICMP, so no reply doesn’t always mean offline.
* Watch packet loss percentage and response times (latency).
* In SOC, ping helps quickly identify if a device or host is reachable and isolates network issues.

---

## 3. `netstat` — Network Connections, Listening Ports, and Routing

### What it does:

* Shows current network connections, listening ports, routing tables, and interface statistics.
* Useful to identify suspicious connections or open ports.

### How to use:

```bash
netstat -tuln
```

Flags explained:

* `-t` — TCP connections
* `-u` — UDP connections
* `-l` — Listening sockets (servers)
* `-n` — Show IPs and ports numerically (no DNS resolution)

Example:

```bash
netstat -tuln
```

Shows listening ports and their IPs.

To see all connections (established and listening):

```bash
netstat -ant
```

`-a` for all sockets, `-n` numeric, `-t` TCP.

### How to test:

* Run `netstat -tuln` on your machine and note listening ports.
* Identify which service runs on each port (e.g., 22 = SSH, 80 = HTTP).
* Run `netstat -ant` to check established connections.
* Try opening a web browser or SSH connection and see the effect on `netstat` output.

### What to watch out for:

* `netstat` is deprecated in some systems; use `ss` command as modern alternative (`ss -tuln`).
* In SOC, spotting unexpected open ports or external connections can reveal compromised hosts.
* Look for connections from suspicious IP addresses or on unusual ports.
* If many connections are in `SYN_RECV` or `TIME_WAIT`, it may indicate a network issue or attack (like SYN flood).

---

## Quick Hands-on Lab Scenario (Simulating SOC monitoring):

1. **Check interfaces:**

   * Run `ifconfig` (or `ip a`) to identify your IP addresses.
   * Confirm you are on the correct subnet.

2. **Test connectivity:**

   * Ping your gateway (e.g., `ping 192.168.1.1`).
   * Ping an external IP (e.g., `ping 8.8.8.8`).
   * Ping a domain (e.g., `ping www.google.com`).
   * Watch for packet loss or timeouts.

3. **Check open ports and connections:**

   * Run `netstat -tuln` to see which ports your machine is listening on.
   * Run `netstat -ant` to observe all current TCP connections.
   * Identify any unusual ports or IPs.

4. **Bonus SOC mindset:**

   * Imagine you see a connection to an unknown external IP on an unusual port.
   * Investigate what process owns that connection (`sudo netstat -plant`).
   * Consider blocking or reporting suspicious traffic.

---

### Summary for SOC preparation:

| Command  | Purpose                               | Key Flags                       | SOC Use Case                                        |
| -------- | ------------------------------------- | ------------------------------- | --------------------------------------------------- |
| ifconfig | View/configure network interfaces     | `ifconfig -a` (show all)        | Verify machine IP, MAC, interface status            |
| ping     | Test connectivity to hosts or domains | `ping <IP/domain>`              | Quick reachability checks and latency monitoring    |
| netstat  | View network connections, open ports  | `netstat -tuln`, `netstat -ant` | Detect suspicious connections, open ports, services |

