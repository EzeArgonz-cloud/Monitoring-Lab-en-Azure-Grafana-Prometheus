A monitoring solution based on Prometheus and Grafana was implemented, deployed on virtual machines, with the goal of centralizing metrics and providing operational visibility to teams through accessible and customizable dashboards.

Architecture
Data Flow:
Node Exporter → Prometheus → Grafana

Node Exporter: exposes operating system metrics (CPU, memory, disk, network)
Prometheus: collects metrics through scraping
Grafana: visualizes the information in dashboards

Implementation

Infrastructure
Creation of a Linux VM in Azure
Configuration of network rules (NSG) to allow access to:
SSH (22)
Grafana (3000)
Prometheus (9090)
Node Exporter (9100)
Grafana
Installation and configuration as a service
Web access for administration and visualization
Prometheus
Manual installation
Configuration of the prometheus.yml file
Exposure of metrics on port 9090
Node Exporter
Installation and execution on the VM
Exposure of system metrics at /metrics
Integration
Prometheus was configured to collect metrics from Node Exporter:

job_name: "node"
static_configs:
targets: ["localhost:9100"]

Then, Prometheus was integrated as a Data Source in Grafana for visualization.

Dashboard

A single dashboard was created with multiple panels to visualize:

CPU usage (%)
Memory usage (%)
Available memory (GB)
Disk usage (%)
Network traffic (inbound/outbound)
System load

This allows having a clear and real-time view of the server status.

Challenges during implementation

During the lab, different challenges typical of a real environment arose:

Initial configuration of repositories and packages
Adjustments in Prometheus configuration
Validation of connectivity between services
Linux process management
Organization of dashboards in Grafana
