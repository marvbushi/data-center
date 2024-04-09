# Server CPU Management Guide

## CPU Configuration
- **Check CPU Information**: Use `lscpu` to display CPU architecture information.
- **CPU Governor**: Adjust the CPU frequency scaling with `cpupower frequency-set`.
```
lscpu
cpupower frequency-set -g performance
```
## CPU Maintenance
- **Monitor CPU Usage**: Use `top` or `htop` to monitor real-time CPU usage.
- **Update CPU Microcode**: Ensure the CPU microcode is up to date for security and performance.
```
top
sudo apt install intel-microcode # For Intel CPUs
```

## CPU Diagnostics
- **Check CPU Performance**: Use `mpstat` to report CPU statistics.
- **Stress Test CPU**: Use `stress` or `stress-ng` to stress test the CPU and check its stability.
```
mpstat -P ALL
sudo apt install stress
stress --cpu 8 --timeout 60s
```
## CPU Troubleshooting
- **Identify High CPU Load**: Use `ps` to identify processes with high CPU usage.
- **Check for Hardware Errors**: Use `dmesg` to check the kernel ring buffer for hardware error messages.
```
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head
dmesg | egrep -i 'error|warn|fail'
```
