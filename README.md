Monitoring project containing strong monitoring tools like Prometheus, Grafana, Node Exporter & cAdvisor

A Docker-based monitoring solution for system/container metrics visualization with alerting capabilities.

🚀 -- Prerequisites
- Docker Engine 20.20+
- Docker Compose 2.0+
- Git
- WSL

🚀 -- Installation
git clone https://github.com/Robert-Berbece/Monitoring-stack.git
cd Monitoring-stack
docker compose -f monitoring-stack.yml up -d

🌐 Access Services
Service	        URL	                    Credentials
---------------------------------------------------
Grafana	        http://localhost:3000	  admin/admin
---------------------------------------------------
Prometheus	    http://localhost:9090	  -
---------------------------------------------------
Node Exporter	  http://localhost:9100	  -
---------------------------------------------------
cAdvisor	      http://localhost:8080	  -

🛠 Configuration
1. Prometheus Targets
Verify all targets are healthy:
http://localhost:9090/targets
<img width="1862" height="655" alt="image" src="https://github.com/user-attachments/assets/7a3172c9-038f-4a4a-bf49-3bf28e42fd27" />

