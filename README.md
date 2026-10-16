# Linux Fundamentals Project: System Information & Network Diagnostics

## Executive Summary
This project demonstrates foundational Linux command-line administration, system introspection, and network connectivity testing within a virtualized Kali Linux environment managed via Oracle VM VirtualBox.

## Environment & Tools
* **Host Hypervisor:** Oracle VM VirtualBox[cite: 1]
* **Guest Operating System:** Kali Linux (x86_64)[cite: 1]
* **Kernel Version:** `7.1.5+kali-amd64`[cite: 1]

---

## Part 1: System Information & Resource Analysis

The initial phase focuses on querying basic user, system, and kernel parameters, alongside monitoring available system hardware resources.

### 1. User and Host Identification
The following commands were executed to verify user privileges, hostname, and working directory:
* `whoami`: Identifies the current active user (`kali`)[cite: 1].
* `hostname`: Displays the network name of the machine (`kali`)[cite: 1].
* `pwd`: Outputs the absolute path of the current working directory (`/home/kali`)[cite: 1].

![System Info Commands](assets/Part%201%20screenshot.png)

### 2. Kernel & Resource Allocation
* **Kernel Architecture (`uname -a`):** Verified that the system runs Linux kernel `7.1.5+kali-amd64` compiled with SMP preempt support[cite: 1].

![Kernel Architecture](assets/uname%20-a%20screenshot.png)

* **Memory & Storage (`free -h` & `df -h`):** 
  * **Total RAM:** 1.9 GB[cite: 1]
  * **Available Root Partition Disk Space:** 52 GB (`/dev/sda1` mounted on `/`)[cite: 1]

![Memory and Disk Space](assets/free%20-h%20df%20-h.png)

---

## Part 2: Basic Network Connectivity & Diagnostics

Network health and remote reachability were evaluated using the `ping` utility to test ICMP echo request and response handling.

### 1. Direct IP Reachability Test (`ping -c 2 8.8.8.8`)
* **Objective:** Test basic network connectivity to a public IP address (Google DNS) with a capped packet count.
* **Findings:** 
  * Successfully transmitted 2 packets with **0% packet loss**[cite: 1].
  * Recorded an average round-trip time (RTT) of **19.890 ms**[cite: 1].

![Ping IP Test](assets/ping%208.8.8.8.png)

### 2. Domain Resolution & Latency Comparison (`ping -c 4 google.com`)
* **Objective:** Evaluate DNS resolution and measure response times to a domain name over 4 iterations (`-c 4`).
* **Findings:**
  * Resolved `google.com` to target IP address `192.178.54.14`[cite: 1].
  * Average RTT measured at **126.287 ms**[cite: 1].
  * **Analysis:** The variance in latency compared to the direct IP ping stems from differing network routes, geographic server hops, and DNS infrastructure paths[cite: 1].

![Ping Domain Test](assets/ping%20google.com%20screenshot.png)
