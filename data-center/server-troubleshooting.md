# Server Troubleshooting Scenario

## Issue Description
A Linux server is experiencing intermittent network connectivity issues and slow performance. The system administrator is tasked with diagnosing and resolving the problems.

## Troubleshooting Steps

### Step 1: Verify Network Connectivity
- **Command**: `ping -c 4 google.com`
- **Purpose**: To check if the server can reach the internet.
- **Expected Output**: 4 packets transmitted, 4 received, 0% packet loss.

### Step 2: Check Network Configuration
- **Command**: `ip addr`
- **Purpose**: To verify the server's network interface configurations.
- **Expected Output**: A list of network interfaces and their IP addresses.

### Step 3: Analyze Network Traffic
- **Command**: `tcpdump -i eth0 -c 100`
- **Purpose**: To capture the first 100 packets on the `eth0` interface to analyze traffic.
- **Expected Output**: A list of captured packet headers.

### Step 4: Identify Hardware Components
- **Command**: `lspci`
- **Purpose**: To list all PCI devices to ensure all hardware is recognized.
- **Expected Output**: A list of all connected PCI devices.

### Step 5: Check for Hardware Errors
- **Command**: `dmesg | grep -i error`
- **Purpose**: To filter kernel messages for hardware-related errors.
- **Expected Output**: Any error messages related to hardware components.

### Step 6: Monitor System Performance
- **Command**: `top`
- **Purpose**: To display real-time system summary information and a list of processes.
- **Expected Output**: A dynamic view of process activity.

### Step 7: Report Disk Space Usage
- **Command**: `df -h`
- **Purpose**: To report file system disk space usage.
- **Expected Output**: A list of mounted filesystems and their disk usage.

### Step 8: Estimate File Space Usage
- **Command**: `du -sh /var`
- **Purpose**: To estimate file space usage of the `/var` directory.
- **Expected Output**: Total size of the `/var` directory.

### Step 9: Collect System Activity Information
- **Command**: `sar -u 1 5`
- **Purpose**: To collect and report system activity information.
- **Expected Output**: CPU usage statistics for five intervals.

### Step 10: Remote Management
- **Command**: `ssh user@server-ip`
- **Purpose**: To securely connect to the server for remote management.
- **Expected Output**: A prompt for the user's password to initiate the SSH session.

## Resolution
After following the troubleshooting steps, the system administrator identified a faulty network card causing connectivity issues and a process consuming excessive resources, leading to slow performance. Replacing the network card and terminating the resource-intensive process resolved the issues.
