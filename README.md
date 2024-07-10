# lab-monitoring
![image](https://github.com/refracta/lab-monitoring/assets/58779799/d973161b-00d5-4c36-b137-a7438160c2a6)
![image](https://github.com/refracta/lab-monitoring/assets/58779799/13b2211a-8eef-4465-a136-2fdb82196d12)
![image](https://github.com/refracta/lab-monitoring/assets/58779799/28489ad0-b2d2-4a74-9036-26a8e91e1dce)
![image](https://github.com/refracta/lab-monitoring/assets/58779799/b087a764-69c7-4ca9-a159-d67d9bb73fb8)
This is a lab resource monitoring system (GPU, CPU, Docker) using Prometheus and Grafana.

# Run the Service Server
```bash
cd server
docker compose up -d
```

# Connect a New Node
```bash
git clone https://github.com/refracta/lab-monitoring
cd lab-monitoring/node
# For Synology servers, go to node-synology

# Assuming Docker and Docker Compose are installed
docker compose up -d (or docker-compose up -d)
# Now, node-exporter, dcgm-exporter, and cadvisor will run on ports 9100, 9101, and 9102 respectively
```

# Add New Node to Server
Edit server/prometheus/prometheus.yml to add the new node to the monitoring targets. (After adding, restart the service server using docker compose)
 - In the scrape_configs section, for job_name entries node-exporter (System Exporter), dcgm-exporter (GPU Exporter), and cadvisor (Docker Exporter), add the new server to the static_configs > targets section with the same ports.
 - For Synology nodes, only register with node-exporter.
