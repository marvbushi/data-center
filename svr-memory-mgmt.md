
# Server Memory (RAM) Management Guide

## RAM Configuration
- **Check RAM Information**: Use `sudo dmidecode --type 17` to get detailed information about the RAM modules.
- **Set Swappiness**: The swappiness parameter controls the tendency of the kernel to move processes out of physical memory and onto the swap disk. Use `sudo sysctl vm.swappiness=10` to set it to a lower value if you want to decrease swap usage.

```bash
sudo dmidecode --type 17
sudo sysctl vm.swappiness=10
```

## RAM Maintenance
- **Check RAM Usage**: Use `free -h` to display the total, used, and free memory with human-readable output.
- **Clear Cache**: To clear cached memory, you can echo 3 to `/proc/sys/vm/drop_caches`.

```bash
free -h
sudo sh -c 'echo 3 >/proc/sys/vm/drop_caches'
```

## RAM Diagnostics
- **Memory Test**: Use `memtester` to test the RAM for errors. For example, `sudo memtester 1024 5` will test 1024MB of RAM five times.
- **Check for Errors**: The `dmesg` command can be used to check for hardware-related messages, including memory errors.

```bash
sudo memtester 1024 5
dmesg | grep -i error
```

## RAM Troubleshooting
- **Identify Memory Leaks**: Use `top` or `htop` to identify processes that are using a high amount of memory.
- **Check Kernel Messages**: Use `dmesg` to check for any kernel messages related to memory issues.

```bash
top
dmesg | grep -i memory
```

**Explanation of Outputs:**
- `dmidecode` output will list each memory slot and its installed memory, including size, speed, type, and other specifications.
- `sysctl vm.swappiness` will not produce an output unless there is an error; it sets the kernel parameter for future use.
- `free -h` will show memory usage statistics. The `-h` flag makes it human-readable, showing sizes in KB, MB, or GB.
- `echo 3 >/proc/sys/vm/drop_caches` will clear the cache, but it won't produce an output.
- `memtester` will output the progress of the memory test, indicating if it encounters any failures.
- `dmesg | grep -i error` will filter kernel messages for the word "error," showing relevant hardware error messages.
