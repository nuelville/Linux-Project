# Linux System Information and Network Connectivity Testing

## 📌 Project Overview

This project demonstrates fundamental Linux system administration and network troubleshooting skills using a Kali Linux environment. It focuses on identifying system information, checking available memory and disk space, and testing network connectivity using the `ping` command.

The project is divided into two main parts:

1. **System Information** — Identifying the current username, hostname, working directory, RAM capacity, available disk space, and Linux version.
2. **Basic Network Connectivity Test** — Testing network reachability, measuring round-trip time, checking packet loss, and resolving a domain name to its IP address.

The project provides practical experience with Linux terminal commands and basic network diagnostics, which are essential skills for system administrators, IT support professionals, and cybersecurity beginners.

## 🎯 Project Objectives

The main objectives of this project are to:

- Identify the currently logged-in Linux user.
- Determine the hostname of the Linux machine.
- Identify the current working directory.
- Inspect available system memory and disk space.
- Retrieve the reported Linux system version.
- Test connectivity to a remote network destination.
- Measure network round-trip time.
- Identify packet loss during network communication.
- Resolve a domain name to its corresponding IP address.
- Understand the purpose of the `ping` command and its options.

## 🛠️ Tools and Technologies

| Tool or Technology | Purpose |
|---|---|
| Kali Linux | Linux operating system used for the project |
| Linux Terminal | Interface for executing commands |
| `whoami` | Displays the current username |
| `hostname` | Displays the system hostname |
| `pwd` | Displays the current working directory |
| `free` | Displays memory usage information |
| `df` | Displays filesystem disk-space information |
| `uname` | Displays system and kernel information |
| `ping` | Tests network connectivity and measures response times |
| `-c` option | Specifies the number of ICMP echo requests to send |

## 📋 Prerequisites

To reproduce this project, you need:

- A computer or virtual machine running Kali Linux or a compatible Linux distribution.
- Access to a terminal.
- A working network connection for external connectivity tests.
- Permission to access the network destinations being tested.

The commands used in this project are standard Linux utilities and generally do not require administrator privileges.

## 🖥️ Part 1: System Information

The first part of the project involves examining the Linux environment to identify basic system information and available resources.

### Step 1: Identify the Current User, Hostname, and Working Directory

The first step is to determine which user is logged in, identify the computer's hostname, and confirm the current working directory.

#### Commands

```bash
whoami
hostname
pwd
```

#### Explanation

- **`whoami`** displays the username of the currently logged-in user.
- **`hostname`** displays the name assigned to the computer or virtual machine.
- **`pwd`** stands for *Print Working Directory* and displays the full path of the current directory.

#### Results

According to the project documentation:

| Information | Result |
|---|---|
| Username | `kali` |
| Hostname | `kali` |
| Working directory | Home directory of user `kali` |

#### Interpretation

The output identifies `kali` as the active user and the hostname of the machine. The terminal is located in the user's home directory.

These commands are useful when managing multiple Linux systems, navigating directories, troubleshooting permissions, and verifying which account is being used.

### Step 2: Check RAM, Disk Space, and Linux Version

The next step is to inspect the machine's memory, filesystem storage, and operating system information.

#### Commands

```bash
free -h
df -h
uname -a
```

#### Explanation

**1. `free -h`**

Displays memory usage, including total, used, free, shared, and available memory. The `-h` option presents values in a human-readable format.

**2. `df -h`**

Displays filesystem disk-space usage. It reports the filesystem size, used space, available space, percentage of usage, and mount point.

The `-h` option makes the output easier to read by using units such as KiB, MiB, and GiB.

**3. `uname -a`**

Displays system information, including the kernel name, hostname, kernel release, version details, and machine architecture when available.

#### Results

The attached project documentation records the following values:

| System Information | Recorded Result |
|---|---|
| Total RAM | `1 GiB` |
| Available disk space on the main partition | `230 MiB` |
| Reported Linux version | `Linux kali 16.9.14` |

*Note: The version string is reproduced as recorded in the project documentation. The precise kernel release and distribution version should be verified from the original terminal output if needed.*

#### Interpretation

The system has a reported total RAM capacity of 1 GiB and approximately 230 MiB of available disk space on the main partition.

These values help establish the resource limitations of the environment. Limited disk space may affect software installation, system updates, log storage, and the ability to save files. Limited RAM may also affect performance when running resource-intensive applications.

The `free -h` and `df -h` commands are useful for monitoring resource utilization and identifying potential capacity issues.

## 🌐 Part 2: Basic Network Connectivity Test

The second part of the project focuses on checking network communication with remote destinations. The `ping` utility is used to send ICMP echo requests and measure the responses.

### Step 1: Test Basic Network Connectivity

The first connectivity test uses the `ping` command to check whether a remote destination responds to ICMP echo requests.

#### Example Command

```bash
ping -c 4 8.8.8.8
```

This is an illustrative command for reproducing a four-packet connectivity test. The original project records a round-trip time and packet-loss result but does not explicitly identify the destination in the extracted results for this step.

#### Explanation

- **`ping`** sends ICMP echo requests to a destination and waits for responses.
- **`-c`** specifies the number of echo requests to send.
- **`4`** specifies that four requests should be sent before the command terminates.
- **`8.8.8.8`** is an example destination IP address for a connectivity test.

#### Recorded Results

| Metric | Result |
|---|---|
| Round-trip time | `1010 ms` |
| Packet loss | `0%` |

#### Interpretation

The recorded round-trip time is 1010 milliseconds, equivalent to approximately 1.01 seconds.

A round-trip time measures how long it takes for a request to reach the destination and for its response to return. A value of 1010 ms indicates a relatively slow response for many ordinary network connections.

The recorded packet loss of 0% means that no packet loss was observed during that test.

However, a successful ping does not necessarily prove that every network service is functioning correctly. Some destinations or networks block ICMP traffic, and ping results can be affected by network congestion, routing, firewall rules, or destination-side rate limiting.

### Step 2: Test Connectivity to Google Using Its Domain Name

The next test uses a domain name instead of a numeric IP address. This helps demonstrate both domain-name resolution and network connectivity.

#### Command

```bash
ping -c 4 google.com
```

#### Explanation

This command sends four ICMP echo requests to `google.com`.

When a domain name is supplied, the system first attempts to resolve the name through its configured DNS resolver. The resulting IP address is then used as the destination for the connectivity test.

The options have the following meanings:

- **`ping`** initiates the network connectivity test.
- **`-c`** specifies the number of echo requests to send.
- **`4`** sets the request count to four.
- **`google.com`** is the destination domain name.

#### Recorded Results

| Metric | Result |
|---|---|
| Domain name | `google.com` |
| Resolved IP address | `74.125.136.100` |
| Packet count | `4` |

The IP address above is the address recorded in the project documentation. DNS responses may vary depending on location, resolver, and time.

#### Interpretation

The domain name `google.com` was resolved to `74.125.136.100` during the documented test.

This demonstrates the role of DNS in translating human-readable domain names into IP addresses that computers can use for network communication.

The `-c 4` option limits the command to four echo requests rather than allowing it to continue indefinitely. This makes the test convenient for basic troubleshooting and for collecting a finite set of network measurements.

The project notes that the round-trip time was longer when pinging `google.com` directly. The documented results do not provide the exact timing for this second test, so a numerical comparison cannot be established from the available information alone.

A longer response time may result from network routing, congestion, DNS-related delays before the first response, or other network conditions. The packet-count option itself does not inherently make individual packets travel more slowly.

## 📊 Project Results Summary

The following table summarizes the main results documented in the project.

| Category | Test or Measurement | Result |
|---|---|---|
| System | Current username | `kali` |
| System | Hostname | `kali` |
| System | Working directory | User `kali` home directory |
| System | Total RAM | `1 GiB` |
| System | Available disk space | `230 MiB` |
| System | Reported Linux version | `Linux kali 16.9.14` |
| Network | Recorded round-trip time | `1010 ms` |
| Network | Recorded packet loss | `0%` |
| Network | Domain tested | `google.com` |
| Network | Resolved IP address | `74.125.136.100` |
| Network | Echo request count for Google test | `4` |

## 🔍 Key Findings

The project demonstrates several important Linux and networking concepts.

### 1. Basic Linux System Identification

The `whoami`, `hostname`, and `pwd` commands provide quick information about the active user, machine name, and current directory.

### 2. Resource Monitoring

The memory and disk-space checks provide an overview of available system resources. The recorded 230 MiB of available disk space suggests that storage should be monitored carefully before installing additional software or downloading large files.

### 3. Network Reachability

The ping test recorded 0% packet loss, indicating that all packets in that particular test were reported as successfully returned.

### 4. Understanding Latency

The documented round-trip time of 1010 ms indicates a comparatively high response time. Repeating the test and comparing several measurements can help determine whether the delay is consistent or temporary.

### 5. DNS Resolution

The Google connectivity test demonstrates how a domain name is resolved to an IP address before communication takes place.

### 6. Controlled Testing

Using `ping -c 4` allows a fixed number of echo requests to be transmitted, making the test finite and easier to document.

## 🚀 How to Reproduce the Project

Follow these steps to perform similar checks on a Linux machine.

### Step 1: Open the Terminal

Open a terminal in Kali Linux.

### Step 2: Check User and Host Information

Run:

```bash
whoami
hostname
pwd
```

Record the username, hostname, and working directory.

### Step 3: Inspect Memory and Disk Usage

Run:

```bash
free -h
df -h
```

Record the total memory and available storage reported by the system.

### Step 4: Check Linux System Information

Run:

```bash
uname -a
```

Record the output, including the kernel release and architecture.

### Step 5: Test Network Connectivity

Run a finite connectivity test against a permitted destination:

```bash
ping -c 4 8.8.8.8
```

Record the packet count, packet loss, and round-trip time.

### Step 6: Test Domain Resolution and Connectivity

Run:

```bash
ping -c 4 google.com
```

Record the resolved IP address and the packet statistics.

### Step 7: Document the Results

Compare the output with the results in this README. Your results may differ because system resources, Linux versions, DNS responses, and network conditions vary between environments.

## 🧰 Troubleshooting

### Problem: `ping` Does Not Receive Responses

Possible causes include:

- The machine has no working network connection.
- The destination is unavailable.
- A firewall blocks ICMP echo requests.
- The destination limits or ignores ping traffic.

**Suggested checks:**

```bash
ip addr
ip route
ping -c 4 8.8.8.8
```

These commands help inspect network interfaces, routing configuration, and connectivity to a numeric IP address.

### Problem: `google.com` Cannot Be Resolved

A domain-resolution failure may indicate a DNS configuration issue or a lack of network connectivity.

Try:

```bash
ping -c 4 8.8.8.8
getent hosts google.com
```

If the numeric-IP test works but the domain lookup fails, investigate the system's DNS configuration.

### Problem: Disk Space Is Almost Full

Check filesystem usage:

```bash
df -h
```

Inspect directory sizes where appropriate:

```bash
du -sh ~
```

Review unnecessary files before deleting anything. Avoid removing system files or directories unless you understand their purpose.

### Problem: Memory Usage Is High

Review current memory usage:

```bash
free -h
```

For additional information about running processes, use:

```bash
top
```

These commands help identify memory pressure and processes that may be consuming significant resources.

## 🔐 Security and Best Practices

- Execute commands only on systems you own or are authorized to administer.
- Use network diagnostics for legitimate troubleshooting and learning.
- Avoid exposing sensitive system information when sharing terminal screenshots publicly.
- Monitor disk usage before installing additional packages or running updates.
- Do not assume that successful ping responses guarantee the availability or security of every service.
- Record the date, system environment, and destination when comparing network measurements.
- Verify system version details directly from terminal output before using them for security or compatibility decisions.

## 📁 Suggested GitHub Repository Structure

A simple repository layout for this project could be:

```text
linux-system-network-project/
├── README.md
├── screenshots/
│   ├── system-information.png
│   ├── resource-usage.png
│   ├── network-connectivity.png
│   └── google-ping.png
└── LICENSE
```

**File descriptions:**

- `README.md` — Project overview, commands, recorded results, and explanations.
- `screenshots/` — Optional screenshots of the terminal outputs.
- `LICENSE` — Optional license specifying how others may use and distribute the project.

The screenshot filenames are suggestions; add them only if you have the corresponding images. A license is also optional and should be selected according to your intended sharing terms.

## 📚 Learning Outcomes

By completing this project, a learner can gain practical experience with:

- Navigating and inspecting a Linux environment.
- Identifying users and hostnames.
- Checking memory and filesystem capacity.
- Reading Linux system-version information.
- Using ICMP ping requests to investigate connectivity.
- Interpreting round-trip time and packet-loss statistics.
- Understanding the relationship between DNS resolution and network communication.
- Recording technical findings in a structured format.

## 🔮 Future Improvements

The project can be expanded with additional Linux administration and networking exercises, such as:

- Monitoring CPU and memory usage over time.
- Comparing network latency across multiple destinations.
- Repeating ping tests to observe variations in latency and packet loss.
- Inspecting network interfaces and routing tables.
- Investigating DNS resolution using dedicated DNS utilities.
- Recording test results in a CSV file for analysis.
- Automating the system-information checks with a Bash script.

These are suggested extensions and are not part of the completed tests documented in the attached project.

## 🏁 Conclusion

This project provides a practical introduction to Linux system information gathering and basic network diagnostics using Kali Linux.

The system-information checks identify the active user, hostname, working directory, memory capacity, available disk space, and reported Linux version. The network tests demonstrate how to use `ping` to measure round-trip time, observe packet loss, and test connectivity using both an IP address and a domain name.

The documented results include 1 GiB of RAM, 230 MiB of available disk space, a recorded round-trip time of 1010 ms, 0% packet loss in the reported test, and a Google DNS resolution result of `74.125.136.100`.

Overall, the project builds a foundation for further learning in Linux system administration, networking, IT support, and cybersecurity.

---

**Author:** Add your name here

**Platform:** Kali Linux

**Project Type:** Linux System Administration and Network Troubleshooting

**Status:** Completed — Basic System Information and Network Connectivity Tests
