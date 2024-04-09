# Overloaded Web Server Scenario

## Background
A web hosting company has a Linux server that suddenly starts to slow down, affecting all the websites it hosts. The server admin needs to quickly identify and resolve the issue to minimize downtime.

## Configuration
- **Install Necessary Tools**: Ensure tools like `htop`, `iostat`, and `cpufrequtils` are installed for monitoring and managing the CPU.
  ```bash
  sudo apt-get install htop iostat cpufrequtils
  ```

## Maintenance
- **Regular Monitoring**: Set up a cron job to regularly monitor CPU usage and temperatures using `htop` and `sensors`.
  ```bash
  * * * * * /usr/bin/htop -b -n 1 >> /var/log/cpu_usage.log
  * * * * * /usr/bin/sensors >> /var/log/cpu_temp.log
  ```

## Diagnostics
- **High Load Investigation**: Use `htop` to identify processes that are consuming excessive CPU resources.
  ```bash
  htop
  ```
- **Check I/O Wait**: Use `iostat` to check for high I/O wait times, which can indicate that the CPU is waiting on disk operations.
  ```bash
  iostat -c 1 10
  ```

## Troubleshooting
- **Identify Faulty Hardware**: If diagnostics suggest a hardware issue, use `dmesg` to look for kernel messages related to CPU errors.
  ```bash
  dmesg | grep -i cpu
  ```
- **CPU Frequency Scaling**: If the CPU is overheating, reduce the frequency using `cpufreq-set`.
  ```bash
  sudo cpufreq-set -u 1.8GHz
  ```

## Resolution
The server admin discovers a runaway process that's consuming all available CPU cycles. They kill the process and implement better resource limits to prevent a recurrence. They also schedule regular maintenance checks to monitor system health.

## Dependencies
- `htop` for process monitoring.
- `iostat` from `sysstat` package for I/O statistics.
- `cpufrequtils` for CPU frequency management.
- `lm_sensors` for temperature monitoring.
- `cron` for scheduling regular tasks.
