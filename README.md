# trial-prometheus

- [Grafana](https://grafana.com/docs/grafana/latest/setup-grafana/installation/docker/): http://localhost:3000
- [Prometheus](https://prometheus.io/docs/prometheus/latest/installation/#using-docker): http://localhost:9090

## Bootstrap

确保主节点的 3000、9090 端口，被监控节点的 9100 端口均已打开。

### 主节点

启动服务

```shell
mkdir -p data/grafana
chmod 777 data/grafana
docker compose up -d
```

#### 添加数据源

```shell
sudo nano prometheus.yml
```

#### 添加数据库

`URL` 字段填写 `http://prometheus:9090` 并回车即可。

#### 导入 Dashboard

http://localhost:3000/dashboard/import

`Import via grafana.com` 字段填写 `1860` 后点击 `Load`。

### 被监控节点

```shell
docker run --name node-exporter --restart always -d -p 9100:9100 prom/node-exporter
```

## Grafana

http://localhost:3000

默认账号 admin/admin
