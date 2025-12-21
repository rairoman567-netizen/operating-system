
# Phase 3: Application Selection for Performance Testing

## Objective:
The goal is to select applications that represent different types of workload (CPU-intensive, RAM-intensive, I/O-intensive, Network-intensive, etc.), document their anticipated resource usage, and create a strategy for monitoring and measuring performance.

---

## 1. Select Applications for Different Workload Types:
The goal is to select applications that represent various workload characteristics. Below is an example of an **Application Selection Matrix** with justifications:

### Application Selection Matrix:

| **Workload Type**   | **Application**  | **Justification for Selection**                                                |
|---------------------|------------------|--------------------------------------------------------------------------------|
| **CPU-intensive**    | stress-ng (CPU)  | stress-ng can simulate high CPU loads, useful for stress testing CPU performance.|
| **RAM-intensive**    | stress-ng (RAM)  | stress-ng can also stress test RAM by allocating large amounts of memory.        |
| **I/O-intensive**    | fio              | fio is a flexible I/O performance benchmarking tool, ideal for testing disk I/O.|
| **Network-intensive**| iperf3           | iperf3 measures network bandwidth and latency, making it perfect for network testing.|
| **Server Application**| nginx           | nginx is a widely used web server; it will represent typical server workloads in production. |

---

## 2. Installation Documentation with Exact Commands for SSH-based Installation:
Here’s the installation guide for each selected application via SSH.

### Installation Documentation (SSH-based Commands):

1. **stress-ng (CPU & RAM Stress Test):**
   - Install stress-ng:
   - sudo apt update
   - sudo apt install stress-ng
     ```

2. **fio (Disk I/O Benchmark):**
   - Install fio:
   - sudo apt update
   - sudo apt install fio
     ```

3. **iperf3 (Network Benchmark):**
   - Install iperf3
   - sudo apt update
   - sudo apt install iperf3
    

4. **nginx (Web Server):**
   - Install nginx
   - sudo apt update
   - sudo apt install nginx
     ```

---

## 3. Expected Resource Profiles:
For each application, document the anticipated resource usage based on typical workloads. Below is an example of expected resource profiles.

### Expected Resource Profiles:

| **Application**         | **CPU Usage**   | **Memory Usage** | **Disk I/O** | **Network Usage** |
|-------------------------|-----------------|------------------|--------------|-------------------|
| **stress-ng (CPU)**      | High            | Low              | Minimal      | None              |
| **stress-ng (RAM)**      | Low             | High             | Minimal      | None              |
| **fio**                  | Moderate        | Low              | High         | Minimal           |
| **iperf3**               | Moderate        | Low              | Minimal      | High              |
| **nginx**                | Moderate        | Moderate         | Low          | Moderate          |

- **CPU Usage:** Whether the application is heavy on the CPU (e.g., stress-ng for CPU testing).
- **Memory Usage:** Expected memory consumption (e.g., stress-ng for RAM will use significant memory).
- **Disk I/O:** How much disk read/write activity the application generates (e.g., fio will be I/O-intensive).
- **Network Usage:** The expected level of network bandwidth consumption (e.g., iperf3 is network-heavy).

---

## 4. Monitoring Strategy:
For performance testing, I want to monitor various system metrics such as CPU, RAM, disk I/O, and network usage during the application’s execution.

### Monitoring Strategy:

- **CPU Usage:** Use `top`, `htop`, or `mpstat` to monitor CPU utilization.
  - Command: `top` or `htop` for interactive monitoring.
  - Example for `mpstat`: 
    ```bash
    mpstat -P ALL 1
    ```
    This shows CPU usage for all cores.

- **Memory Usage:** Use `free -h` or `vmstat` to monitor memory usage.
  - Command: `free -h` (shows memory usage in human-readable format).
  - Example: `vmstat 1` for real-time memory stats.

- **Disk I/O:** Use `iostat`, `iotop`, or `fio` itself to measure disk I/O performance.
  - Command: `iostat -x 1` (to show extended disk I/O stats).
  - Example: `iotop` for real-time disk I/O monitoring.

- **Network Usage:** Use `iftop`, `nload`, or `iperf3` to monitor network bandwidth.
  - Command: `iftop` for real-time bandwidth monitoring.
  

---

By following this structure,  I will ensure that I have a systematic approach to performance testing, proper installation documentation, and a clear strategy for monitoring and analyzing system performance.
