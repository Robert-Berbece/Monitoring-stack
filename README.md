Monitoring project containing strong monitoring tools like Prometheus, Grafana, Node Exporter & cAdvisor

A Docker-based monitoring solution for system/container metrics visualization with alerting capabilities.

🚀 -- Prerequisites
- Docker Engine (20.20+)
- Docker Compose (2.0+)
- Git
- WSL (Ubuntu 22.04.2)

🚀 -- Installation
git clone https://github.com/Robert-Berbece/Monitoring-stack.git
cd Monitoring-stack
docker compose -f monitoring-stack.yml up -d

🌐 Access Services
Service	    |    URL	         |           Credentials
---------------------------------------------------
Grafana	     |   http://localhost:3000	|  admin/admin
---------------------------------------------------
Prometheus	 |   http://localhost:9090	 |  -
---------------------------------------------------
Node Exporter	 |  http://localhost:9100	 |  -
---------------------------------------------------
cAdvisor	 |    http://localhost:8080	 |  -
---------------------------------------------------


🛠 Configuration
1. Prometheus Targets
Verify all targets are healthy:
http://localhost:9090/targets
<img width="1862" height="655" alt="image" src="https://github.com/user-attachments/assets/7a3172c9-038f-4a4a-bf49-3bf28e42fd27" />


2. Grafana Setup
- Add Data Source: Configuration → Data Sources → Prometheus with URL: http://prometheus:9090

Import Dashboards:
-Click "+" → Import → Enter these IDs: Node Metrics: 1860 & Container Metrics: 14282
Node Exporter dashboard
<img width="1597" height="941" alt="image" src="https://github.com/user-attachments/assets/23ebc1b5-cd0f-461e-a791-76dc1e56f427" />

cAdvisor dashboard
<img width="1665" height="932" alt="image" src="https://github.com/user-attachments/assets/bfd75d99-0d1d-4650-93ee-55b060015f0e" />


🔔 Alert Configuration
Sample CPU Alert:
1. Go to Alerting → Alert rules → New alert rule
2. Set query: node_cpu_seconds_total
3. Set Alert condition, when query is above 8000
4. Add a folder or create one
5. Set evaluation behavior as "CPU Alerts" at 5min
<img width="1242" height="820" alt="image" src="https://github.com/user-attachments/assets/a00a1961-4a1a-4ee4-a80c-8d56dde6928b" />


🧪 Testing Alerts
* In your WSL terminal run the following commands to make a stress test:
sudo apt install stress
stress -c 2 -t 10m 
( this will use 2 cores of CPU for 10 minutes )


* In Grafana go to Home -> Alerting -> Alert Rules (you should see a button in red saying "1 firing")
This way you know the stress test and Grafnaa alerting works
<img width="1598" height="940" alt="image" src="https://github.com/user-attachments/assets/a589b109-5f0d-461b-a72c-9b2e3af735cb" />


* After test is finished, make sure to kill the stress proccess, using this command:
pkill stress

🛑 Stop Services
When done working with the monitoring tools, make sure to stop all services, using this command:
docker compose -f monitoring-stack.yml down
