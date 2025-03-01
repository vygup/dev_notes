## Установка

### Настройка `docker-compose`
Создаем директории:
```bash
mkdir -p /opt/monitoring_stack/{prometheus,grafana}

cd /opt/monitoring_stack

nano docker-compose.yml
```

В открывшийся файл `docker-compose.yml` записываем данные ниже::
```yml
version: '3.9'

services:

  prometheus:
    image: prom/prometheus:latest
    volumes:
      - ./prometheus:/etc/prometheus/
    container_name: prometheus
    hostname: prometheus
    command:
      - --config.file=/etc/prometheus/prometheus.yml
    ports:
      - 9090:9090
    restart: unless-stopped
    environment:
      TZ: "Europe/Moscow"
    networks:
      - default

  node-exporter:
    image: prom/node-exporter
    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro
    container_name: exporter
    hostname: exporter
    command:
      - --path.procfs=/host/proc
      - --path.sysfs=/host/sys
      - --collector.filesystem.ignored-mount-points
      - ^/(sys|proc|dev|host|etc|rootfs/var/lib/docker/containers|rootfs/var/lib/docker/overlay2|rootfs/run/docker/netns|rootfs/var/lib/docker/aufs)($$|/)
    ports:
      - 9100:9100
    restart: unless-stopped
    environment:
      TZ: "Europe/Moscow"
    networks:
      - default

  grafana:
    image: grafana/grafana
    user: root
    depends_on:
      - prometheus
    ports:
      - 3000:3000
    volumes:
      - ./grafana:/var/lib/grafana
      - ./grafana/provisioning/:/etc/grafana/provisioning/
    container_name: grafana
    hostname: grafana
    restart: unless-stopped
    environment:
      TZ: "Europe/Moscow"
    networks:
      - default

networks:
  default:
    ipam:
      driver: default
      config:
        - subnet: 172.98.0.0/12

```

### Настройка `prometheus`

В файл `prometheus.yml`:
```bash
sudo nano prometheus/prometheus.yml
```

```yml
scrape_configs:
  - job_name: node
    scrape_interval: 5s
    static_configs:
    - targets: ['node-exporter:9100']
```

### Проверка работы сервисов
Запускаем `docker-compose`:
```bash
sudo docker-compose up -d
```

### Настройка `Grafana`

1) Открываем `Grafana` и нажимаем `add data source`
2) Прописываем хост промитеуса и порт:
	`http://prometheus:9090`
