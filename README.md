[//]: # (# grafana-prometheus-all-in-one)

[//]: # (# grafana-prometheus-all-in-one)

This repository contains such tools as:
Grafana, Prometheus, node-exporter, alertmanager, cadvisor-exporter, snmp-exporter, InfluxDB.

Clone the repository first:
```
git clone https://github.com/youonmyown/grafana-prometheus-all-in-one.git
```
Edit and uncomment the necessary blocks from the file `/prometheus/prometheus.yml`

Change the ports for the services in the `docker-compose.yml` file to the ones you need.

You can change the login and password for logging into grafana in the file `/grafana/config.monitoring`

After you have edited the files, return to the previous directory and run docker-compose:
```
cd ..
docker compose up -d
```
## TrueNAS Core monitoring
For monitoring the TruNAS server, an InfluxDB (with Graphite protocol)  service is prepared in the docker-compose file.
Enter into the console to get a list of running containers:
```
docker ps
```
You will receive something similar, we need the container ID:
![image](https://github.com/youonmyown/grafana-prometheus-all-in-one/assets/138362837/8e805bce-94ba-41bf-a12e-34047195f6b8)


After that enter:
```
docker exec -it <container id> bash
```
After we entered the container we need to use InfluxDB:
```
influx
Connected to http://localhost:8086 version 1.8.10
InfluxDB shell version: 1.8.10
> show series
```
Based on the obtained data, you can build your own dashboard. I didn’t find ready-made options and used the dashboard https://grafana.com/grafana/dashboards/12921-truenas/ as a template.

