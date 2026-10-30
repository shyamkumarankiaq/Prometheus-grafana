# PromQL Queries and Explanations

## 1. Target Availability

Query:
up

Explanation:
Checks whether Prometheus targets are healthy.
1 = UP, 0 = DOWN.

## 2. CPU Utilisation

Query:
100 * (1 - avg by(instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])))

Explanation:
Calculates CPU utilisation percentage using idle CPU time.

## 3. Memory Utilisation

Query:
100 * (1 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes))

Explanation:
Calculates percentage of RAM currently used.

## 4. Disk Utilisation

Query:
100 * (1 - (node_filesystem_avail_bytes{mountpoint="/etc/hostname"} / node_filesystem_size_bytes{mountpoint="/etc/hostname"}))

Explanation:
Calculates filesystem usage percentage for the monitored mountpoint.
Note: This is a container-mounted filesystem, not necessarily the Ubuntu host root filesystem.

## 5. Network Traffic

Query:
rate(node_network_receive_bytes_total[5m])

Explanation:
Calculates incoming network traffic in bytes per second over five minutes.





